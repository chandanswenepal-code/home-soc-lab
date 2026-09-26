# SOC Lab Build Summary

**Analyst:** Chandan Yadav
**Build Period:** September 21-25, 2026
**Platform:** VMware Workstation Pro 26H1 — Windows 11 Host — 16GB RAM

## Steps Completed

### Step 1 — Kali Linux Base Configuration
- Updated all packages via apt full-upgrade
- Installed Docker CE from official repository
- Configured dual network adapters: NAT (eth0) + Host-Only (eth1)
- Snapshot created: Kali-Base-Clean

### Step 2 — Windows Server 2022 Target Endpoint
- Deployed Windows Server 2022 Standard Evaluation (Desktop Experience)
- Configured dual adapters: NAT + Host-Only (192.168.173.130)
- Disabled Windows Defender real-time protection for simulation
- Verified lab connectivity: 0% packet loss between VMs

### Step 3 — Wazuh SIEM Deployment
- Installed Wazuh 4.7.5 all-in-one stack
- Three containers deployed: manager, dashboard, indexer
- Dashboard accessible at https://localhost

### Step 4 — Suricata IDS + Wazuh Integration
- Installed Suricata monitoring eth1 interface
- Loaded 52,823 Emerging Threats signatures
- Integrated eve.json alerts into Wazuh SIEM

### Step 5 — Sysmon + Wazuh Agent on Windows
- Deployed Sysmon v15.22 with SwiftOnSecurity config
- Monitoring 7 event ID categories
- Wazuh Agent connected: Active agents: 1

### Step 6 — MISP Threat Intelligence Platform
- Deployed MISP 2.5.47 via Docker Compose
- Loaded 70+ threat intelligence feeds
- Accessible at http://localhost:8080

### Step 7 — Atomic Red Team Attack Simulations
- Executed 5 MITRE ATT&CK techniques
- Generated 610+ real security alerts
- All techniques detected in Wazuh dashboard

### Step 8 — pfSense Firewall
- Deployed pfSense 2.9.0 CE as network firewall
- WAN: 192.168.236.135 — LAN: 192.168.173.132
- Configured 3 custom firewall rules

### Step 9 — Custom Suricata Rules
- Written 10 custom detection rules manually
- Rules loaded: 52,833 total signatures active
- Covering: Telnet, Nmap, C2, RDP, SSH, FTP, DNS, ICMP, SMB, PowerShell
