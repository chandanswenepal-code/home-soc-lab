# IR-005 — Suricata Stream Anomaly: TCP FIN Out of Window

**Date:** September 21, 2026
**Analyst:** Chandan Yadav
**Severity:** Low (Rule Level 3)
**Verdict:** INFORMATIONAL — Single occurrence, no malicious payload

## Alert Details
- Rule ID: 86601
- Signature: SURICATA STREAM CLOSEWAIT FIN out of window
- MITRE Technique: T1071 — Application Layer Protocol
- Agent: wazuh.manager (Suricata on eth1)
- Log Source: /var/log/suricata/eve.json

## Evidence
- TCP FIN packet received outside expected sequence window
- Occurred during CLOSEWAIT state of TCP connection
- Single occurrence with no associated suspicious IPs or payloads
- No correlated alerts in same time window

## Triage
Suricata detected a TCP stream anomaly — a FIN packet received outside the expected sequence window during CLOSEWAIT state. Can occur due to network timing issues, packet reordering, or application-layer differences. In adversarial contexts attackers may craft out-of-sequence TCP packets to evade signature-based detection. Single occurrence classified as informational.

## Verdict
INFORMATIONAL. Single occurrence, no malicious indicators. Filed for baseline documentation. Monitor for repeated occurrences from same source.

## Recommendations
- Monitor repeated TCP stream anomalies from same source IP
- Correlate with application logs if frequency increases
- Investigate if anomalies increase — possible TCP evasion or C2 keep-alive
- Review Suricata stream reassembly configuration
