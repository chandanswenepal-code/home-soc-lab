# IR-001 — Suspicious Windows Service Installation

**Date:** September 21, 2026
**Analyst:** Chandan Yadav
**Severity:** Medium (Rule Level 5)
**Verdict:** FALSE POSITIVE — Legitimate Microsoft Defender component

## Alert Details
- Rule ID: 61138 — New Windows Service Created
- MITRE Technique: T1543.003 — Windows Service
- MITRE Tactic: Persistence, Privilege Escalation
- Agent: Windows-Server-2022 (192.168.173.130)
- Event ID: 7045

## Evidence
- Service Name: Microsoft WdAiNisDrv Driver
- Service File: system32\drivers\wd\WdAiNisDrv.sys
- Service Type: kernel mode driver
- Start Type: demand start
- Account: LocalSystem

## Triage
Alert fired on Windows Event ID 7045 — new kernel mode driver installed under LocalSystem. Investigation confirms this is a legitimate Microsoft Defender AI Network Inspection Driver. File is Microsoft-signed and located in expected Windows directory.

## Verdict
FALSE POSITIVE. Rule 61138 fires on all new service installations regardless of legitimacy. Demonstrates why SOC analysts must investigate context rather than acting on raw alerts alone.

## Recommendations
- Whitelist Microsoft-signed service paths in known Windows directories
- Monitor Event ID 7045 for services from non-standard locations
- Flag services installed from temp or user profile directories
