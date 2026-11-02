# Runtime Context Management

## Principle
Preserve capability and evidence while minimizing active context: normalize early, promote selectively, reference instead of copy, and evict completed low-value detail.

## Three context tiers
1. `RAW_ARTIFACT`: full source, dependency export, package list, or where-used result stored externally or by URI/path.
2. `NORMALIZED_EVIDENCE`: canonical objects, unique edges, path occurrences, fingerprints, counts, and evidence pointers.
3. `ACTIVE_CONTEXT`: root, current critical paths/fields, high-priority findings, unresolved blockers, current wave, and concise decisions.

Do not paste raw tool output into active context.

## Promotion
Promote evidence only when it is relevant to the current objective, critical path/field, security/configuration decision, source conflict, or completion gate. Summarize tool results before promotion.

## Compaction contracts
- Dependency exports: raw-row count, canonical nodes, unique edges, structural branches, depth, critical custom nodes, table functions, unresolved high-priority nodes, and artifact pointer.
- Source: fingerprint, relevant ranges, dependency/logic summary, and pointer; no repeated full source.
- Package/where-used: candidate counts, confirmed/rejected classifications, priority subset, and pointer.
- Templates: metadata-only registry; load one selected body.

## Eviction
After an item is complete and not on an active critical path, retain a compact record:

```yaml
context_eviction:
  object_id: DDLS:I_STANDARD_VIEW
  status: INVENTORY_COMPLETE
  retained_summary: <bounded result>
  evidence_ids: [EV-084]
  fingerprint: <hash>
  reason: not_on_critical_transformation_path
```

Eviction removes detail from active context, not from evidence storage. Rehydrate only for a new material gap or changed fingerprint.

## Checkpoint summary
At the end of each discovery wave retain only:
- scope/budget status;
- new canonical objects and critical edges;
- critical findings and open gaps;
- coverage delta;
- decisions and next wave;
- evidence pointers.

Move large inventories, graphs, evidence registers, and runtime handoffs to sidecars. Main documents use summaries and links.
