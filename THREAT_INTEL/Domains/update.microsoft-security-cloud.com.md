---
ioc_value: "update.microsoft-security-cloud.com"
ioc_type: "Domain"
first_seen: 2026-03-30T12:10:28.921Z
tlp: "RED"
severity: "Critical"
malicious_score: 99 # auto-enriched base rating
reputation_status: "Malicious"
source_incident: "INC-2026-APT-042"
tags: ["APT42", "C2-Server", "DNS-Tunneling", "Phishing-Origin"]
---
# Threat Context: update.microsoft-security-cloud.com

## Description
Critical C2 domain used by APT42 threat actor. This domain masquerades as legitimate Microsoft security service to evade detection. Used for DNS beaconing to exfiltrate data and receive commands from malware implants via DNS tunneling. Detected in incident INC-2026-APT-042. Domain employs sophisticated phishing techniques to deceive users into connecting to malicious infrastructure. All traffic to this domain should be blocked and monitored. Associated with advanced persistent threat operations targeting government and critical infrastructure sectors.

## Automatic Enrichment Data
- **Engine Provider**: Mock AI Sandbox
- **Threat Factor**: 99/100
- **Heuristics**: Recommended immediate block list rule.
