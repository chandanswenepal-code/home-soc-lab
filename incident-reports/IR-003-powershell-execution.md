# IR-003 — Malicious PowerShell Execution (T1059.001)

**Date:** September 22, 2026
**Analyst:** Chandan Yadav
**Severity:** High
**Verdict:** TRUE POSITIVE — Simulated attack detected (authorised Atomic Red Team)

## Alert Details
- MITRE Technique: T1059.001 — PowerShell
- MITRE Tactic: Execution
- Agent: Windows-Server-2022 (192.168.173.130)
- Tool: Atomic Red Team — Invoke-AtomicTest T1059.001 -TestNumbers 1
- Payload: Invoke-Mimikatz credential dumping

## Evidence
- PowerShell process spawned with Import-Module targeting Powersploit
- Invoke-Mimikatz -DumpCreds execution attempted
- Sysmon Event ID 1 captured PowerShell execution chain
- Wazuh alerts fired for suspicious PowerShell activity
- Exit code 0 — full telemetry captured in SIEM

## Triage
Atomic Red Team simulated T1059.001 by attempting to load and execute Mimikatz via PowerShell. Mimikatz is used by attackers to extract plaintext passwords, NTLM hashes, and Kerberos tickets from Windows memory. Sysmon and Wazuh correctly captured the full execution chain.

## Verdict
TRUE POSITIVE. Attack simulation detected successfully. In a real environment this triggers immediate Tier 2 escalation and memory forensics on the affected endpoint.

## Recommendations
- Enable PowerShell Script Block Logging (Event ID 4104)
- Alert on PowerShell with -EncodedCommand or -enc flags
- Deploy Windows Defender Credential Guard
- Implement WDAC to block unsigned scripts
