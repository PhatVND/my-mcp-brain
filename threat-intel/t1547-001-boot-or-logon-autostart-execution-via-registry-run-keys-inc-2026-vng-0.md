---
title: "T1547.001 - Boot or Logon Autostart Execution via Registry Run Keys (INC-2026-VNG-002)"
date: 2026-03-30
captured: 2026-03-30T12:09:34.970Z
---
# T1547.001 - Boot or Logon Autostart Execution: Registry Run Keys / Startup Folder

## MITRE ATT&CK Classification
- **Tactic:** Persistence (TA0003)
- **Technique ID:** T1547.001
- **Technique Name:** Boot or Logon Autostart Execution: Registry Run Keys / Startup Folder

## Incident Reference
- **Source Incident:** INC-2026-VNG-002
- **Severity:** Medium
- **TLP:** GREEN
- **Detection Date:** 2026-03-30T14:20:00Z

## Threat Behavior (Procedure)

Kẻ tấn công thực hiện ghi đè hoặc tạo mới một giá trị Registry tại đường dẫn:

```
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
```

Giá trị Registry này trỏ đến một tệp thực thi độc hại:

```
C:\Users\AppData\Roaming\taskhostw.exe
```

### Mục đích
- Tự động khởi chạy mã độc mỗi khi người dùng đăng nhập vào hệ thống
- Thiết lập persistence mechanism để duy trì truy cập lâu dài

### Detection Artifacts
- **Event ID:** Sysmon Event ID 13 (Registry Object Added or Deleted)
- **Parent Process:** `powershell.exe`
- **Target Registry Path:** `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run`
- **Malicious Executable:** `C:\Users\AppData\Roaming\taskhostw.exe`

## Indicators of Compromise (IOCs)

| IOC Type | Value | Notes |
|----------|-------|-------|
| **Registry Key** | `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run` | Modified/Created |
| **File Path** | `C:\Users\AppData\Roaming\taskhostw.exe` | Malicious executable |
| **Parent Process** | `powershell.exe` | Command execution source |

## Detection & Response

### EDR/SIEM Detection Rules
```
- Monitor for Registry modifications to Run keys (Event ID 13)
- Alert on PowerShell spawning Registry modifications
- Track process execution from %AppData%\Roaming\
- Monitor process hierarchy: powershell.exe → reg.exe or direct Registry API calls
```

### Immediate Actions
1. ✅ Isolate affected system from network
2. ✅ Terminate `taskhostw.exe` process
3. ✅ Remove malicious Registry entry
4. ✅ Check for lateral movement indicators
5. ✅ Collect memory dump & logs for forensics

### Long-term Mitigation
- Disable PowerShell execution for non-admin users
- Implement Registry write restrictions via GPO
- Deploy EDR with real-time Registry monitoring
- Conduct threat hunting for similar patterns

## Related Techniques
- T1547 - Boot or Logon Autostart Execution (Parent)
- T1059.001 - PowerShell (Execution Method)
- T1547.009 - Startup Folder (Alternative Method)

## Tags
- Persistence
- Registry Modification
- Windows
- Autostart
- Lateral Persistence
- PowerShell

## References
- [MITRE ATT&CK - T1547.001](https://attack.mitre.org/techniques/T1547/001/)