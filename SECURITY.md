# Security

## Read-only design

The Agent and Skill are intended for static, read-only reverse engineering. Do not extend the tool allow-list with write, activation, transport, import, synchronization, posting, scheduling, debug, trace, or business-execution operations.

## Sensitive information

Do not commit credentials, SAP connection secrets, personal data, business records, or confidential production samples. Use evidence pointers, fingerprints, bounded summaries, and redacted examples.

## Reporting

Review security-sensitive changes to `safety-and-preflight.md`, Agent safety rules, tool routing, and local-export handling before merging.
