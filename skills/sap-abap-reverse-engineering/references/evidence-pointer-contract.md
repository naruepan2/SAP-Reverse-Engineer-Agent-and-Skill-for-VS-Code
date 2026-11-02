# Evidence Pointer Contract

## Purpose
Retain traceability without copying full source or tool output into multiple registries.

## Canonical pointer
```yaml
evidence_pointer:
  evidence_id: EV-001
  object_id: DDLS:ZC_EXAMPLE
  provider: ADT_MCP
  source_uri: <uri-or-artifact-path>
  fingerprint: <sha256-or-provider-version>
  retrieved_at: <timestamp>
  relevant_ranges:
    - start_line: 20
      end_line: 45
      purpose: root projection
  bounded_summary: <evidence-only summary>
  state: FACT
```

## Rules
- Store a full source or raw artifact once, outside active reasoning state when possible.
- Registries, findings, lineage, and documents reference `evidence_id`; they do not repeat full source.
- Preserve exact provider, object identity, URI/path, fingerprint, and relevant ranges.
- A summary cannot replace unavailable evidence; label the blocker.
- Reread only for changed fingerprint, truncation recovery, or a targeted unresolved gap.
- Never include credentials, secrets, or unnecessary business records in pointers or summaries.
