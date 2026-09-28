# Home SOC Lab — Chandan Yadav

> SOC Analyst Portfolio · Wazuh SIEM · Suricata IDS · pfSense Firewall · MISP Threat Intel

## About

A fully functional home SOC lab built from scratch to demonstrate hands-on SOC analyst capability. Replicates a real enterprise security monitoring environment with a dedicated firewall, SIEM, network IDS, endpoint telemetry, and threat intelligence integration.

**Analyst:** Chandan Yadav
**Degree:** BSc Software Engineering & Cybersecurity — University of Bedfordshire via PCPS College, Kathmandu, Nepal
**Contact:** chandan.swenepal@gmail.com
**LinkedIn:** linkedin.com/in/chandan-yadavswe
**HTB:** Top 6% globally — Cyber Apocalypse CTF 2026 (407 of 6,744 teams)


## Lab Architecture

- pfSense 2.9.0 — Firewall/Router — WAN: 192.168.236.135 · LAN: 192.168.173.132
- Kali Linux 2026.2 — SOC Workstation — 192.168.173.131
- Windows Server 2022 — Target Endpoint — 192.168.173.130
- Network: Host-Only (192.168.173.0/24) isolated lab network
  <img width="1200" height="1050" alt="soc_lab_architecture" src="https://github.com/user-attachments/assets/888e3714-7414-4ebd-96fc-c9af2d094471" />


Three-VM lab running on VMware Workstation Pro 26H1 (16 GB RAM host).
All traffic between endpoints passes through pfSense 2.9.0 CE firewall.
Suricata IDS monitors the Host-Only LAN with 52,833 signatures + 10 custom rules.
Wazuh Agent on Windows Server forwards Sysmon telemetry to Wazuh SIEM on Kali.

## Tools Stack

| Tool | Version | Purpose |
|---|---|---|
| Wazuh | 4.7.5 | SIEM — alert correlation and dashboards |
| Suricata | 8.0.6 | Network IDS — 52,833 detection signatures |
| pfSense | 2.9.0 | Firewall — custom rules and traffic control |
| MISP | 2.5.47 | Threat Intelligence — 70+ IOC feeds |
| Sysmon | v15.22 | Endpoint telemetry — 7 event ID categories |
| Atomic Red Team | Latest | Adversary simulation — MITRE ATT&CK |
| Wazuh Agent | 4.7.5 | Windows endpoint log forwarding |

## Key Achievements

- 610+ real security alerts generated, triaged and documented
- 5 MITRE ATT&CK attack simulations executed and detected
- 10 custom Suricata detection rules written manually
- 3 pfSense firewall rules configured
- 5 professional SOC incident reports produced
- 70+ threat intelligence feeds integrated via MISP
- 52,833 total Suricata signatures active

## Attack Simulations

| MITRE ID | Technique | Tactic | Status |
|---|---|---|---|
| T1059.001 | PowerShell Abuse — Mimikatz | Execution | Detected |
| T1003.001 | OS Credential Dumping | Credential Access | Detected |
| T1070.001 | Event Log Clearing | Defence Evasion | Detected |
| T1547.001 | Registry Run Key Persistence | Persistence | Detected |
| T1082 | System Information Discovery | Discovery | Detected |

## Custom Suricata Rules

10 rules written manually in /suricata-rules/custom-rules.rules

| SID | Rule | Detects |
|---|---|---|
| 1000001 | Telnet Connection Attempt | Insecure protocol usage |
| 1000002 | Nmap Port Scan | Reconnaissance activity |
| 1000003 | Metasploit C2 Port 4444 | Post-exploitation C2 |
| 1000004 | RDP Brute Force | Credential attack |
| 1000005 | SSH Brute Force | Credential attack |
| 1000006 | FTP Connection Attempt | Insecure protocol usage |
| 1000007 | DNS Tunneling | Data exfiltration |
| 1000008 | ICMP Ping Sweep | Network reconnaissance |
| 1000009 | SMB Lateral Movement | Lateral movement |
| 1000010 | PowerShell Download Cradle | Malware delivery |

## pfSense Firewall Rules

| Rule | Interface | Port | Action |
|---|---|---|---|
| Block Telnet | LAN | 23 | Block |
| Block Metasploit C2 | LAN | 4444-4445 | Block |
| Block RDP from WAN | WAN | 3389 | Block |

## Incident Reports

Five professional SOC incident reports in /incident-reports/ covering:
- IR-001: Suspicious Windows Service Installation — FALSE POSITIVE
- IR-002: Suricata Kali Linux Host Detected — TRUE POSITIVE
- IR-003: PowerShell Execution T1059.001 — TRUE POSITIVE
- IR-004: Persistence Mechanism T1543.003 — TRUE POSITIVE
- IR-005: TCP Stream Anomaly — INFORMATIONAL

---

