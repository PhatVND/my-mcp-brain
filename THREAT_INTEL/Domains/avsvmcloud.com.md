---
ioc_value: "avsvmcloud.com"
ioc_type: "Domain"
first_seen: 2026-03-30T13:03:04.100Z
tlp: "RED"
severity: "Critical"
malicious_score: 99 # auto-enriched base rating
reputation_status: "Malicious"
source_incident: "INC-2026-AVSVMCLOUD-001"
tags: ["Lazarus-Group", "APT38", "C2-Server", "North-Korea", "Cryptocurrency-Theft", "SWIFT-System", "Supply-Chain-Attack", "Financial-Sector", "State-Sponsored", "Active-C2"]
---
# Threat Context: avsvmcloud.com

## Description
CRITICAL C2 infrastructure controlled by Lazarus Group (APT38), a state-sponsored North Korean threat actor. Domain masquerades as legitimate cloud service to evade detection. Used for command and control communication via HTTPS beaconing and DNS tunneling. Associated with cryptocurrency theft, financial sector attacks, SWIFT system compromise, and supply chain operations. Malware implants beacon to this domain every 1-6 hours to receive commands and exfiltrate sensitive data. Infrastructure active as of 2026-03-28. All traffic to this domain should be blocked at network perimeter. Detection and investigation required for any systems showing DNS/HTTPS connections to this domain. Threat actor objective: steal cryptocurrency, access financial systems, exfiltrate corporate data. Deploy immediate containment and forensic response.

## Automatic Enrichment Data
- **Engine Provider**: Mock AI Sandbox
- **Threat Factor**: 99/100
- **Heuristics**: Recommended immediate block list rule.
