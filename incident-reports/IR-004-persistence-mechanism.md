# IR-004 — Persistence Mechanism: New Windows Service (T1543.003)

**Date:** September 22, 2026
**Analyst:** Chandan Yadav
**Severity:** Medium (Rule Level 5)
**Verdict:** TRUE POSITIVE — T1547 persistence technique detected

## Alert Details
- Rule ID: 61138 — New Windows Service Created
- MITRE Technique: T1547.001 — Boot/Logon Autostart Execution
- MITRE Tactic: Persistence, Privilege Escalation
- Agent: Windows-Server-2022 (192.168.173.130)
- Event ID: 7045
- Tool: Atomic Red Team — Invoke-AtomicTest T1547.001 -TestNumbers 1

## Evidence
- Windows Event ID 7045 captured by Sysmon
- New service installed on target endpoint
- Wazuh mapped to Persistence and Privilege Escalation tactic cluster
- Service set to auto-start — survives system reboots

## Triage
Atomic Red Team simulated persistence by installing a new Windows service. Persistence techniques allow attackers to maintain access across reboots and credential changes. Wazuh rule 61138 fired correctly on Event ID 7045. The simulation confirms detection pipeline is functioning end-to-end.

## Verdict
TRUE POSITIVE. Persistence mechanism successfully detected. Wazuh Agent correctly forwarding Windows endpoint events to SIEM.

## Recommendations
- Monitor all Event ID 7045 outside Windows system directories
- Alert on services with binaries in temp or user profile directories
- Implement application whitelisting to prevent unauthorised service installation
- Review LocalSystem and NETWORK SERVICE accounts for unexpected services
