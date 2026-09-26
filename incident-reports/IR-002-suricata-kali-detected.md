# IR-002 — Suricata: Kali Linux Host Detected on Network

**Date:** September 21, 2026
**Analyst:** Chandan Yadav
**Severity:** Low (Rule Level 3)
**Verdict:** TRUE POSITIVE / AUTHORISED — Lab SOC workstation confirmed

## Alert Details
- Rule ID: 86601
- Signature: ET INFO Possible Kali Linux hostname in DHCP Request Packet
- Category: Potential Corporate Privacy Violation
- Agent: wazuh.manager
- Alert Count: 6 occurrences

## Evidence
- Source IP: 192.168.173.131 (Kali Linux)
- Source Port: UDP 68 (DHCP client)
- Destination: 192.168.173.254 UDP 67 (DHCP server)
- Interface: eth1
- Protocol: UDP

## Triage
Suricata detected DHCP broadcast packets containing a hostname string matching Kali Linux naming conventions. Source IP 192.168.173.131 is our authorised SOC analyst workstation. In a real enterprise environment this would be HIGH priority — Kali Linux is a penetration testing OS and its unauthorised presence indicates either an active red team exercise or a serious security incident.

## Verdict
TRUE POSITIVE / AUTHORISED in lab context. In production this would trigger immediate escalation pending authorisation verification.

## Real-World Response
- Verify with IT if an authorised penetration test is in progress
- Check DHCP server logs for full lease history of flagged IP
- If unauthorised — isolate endpoint immediately
- Escalate to Tier 2 and initiate incident response process
