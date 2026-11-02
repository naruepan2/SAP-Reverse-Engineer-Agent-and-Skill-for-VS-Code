# Decision Log

This file summarizes the main design decisions developed through the V8 series.

## Read-only and evidence-first

- SAP access is strictly `SAFE_READ`.
- The Agent never edits, activates, transports, posts, schedules, imports, or synchronizes SAP content.
- Claims are classified as `FACT`, `DERIVED`, `INFERRED`, or `UNVERIFIED`.
- Missing evidence is never converted into a plausible-looking answer.

## Single-object bootstrap

- A user may provide only one SAP object.
- The Agent discovers object type, package, source identity, and technical dependencies itself when tools allow.
- Full package scanning is not the default.
- Discovery expands by evidence value and critical paths, not by raw depth alone.

## CDS dependency analysis

- SAP ADT SQL Dependency Tree, Graph, and Complexity Metrics are distinct evidence types.
- Canonical objects, unique edges, path occurrences, and structural branches are stored separately.
- `SELECT`, `UNION`, and `UNION ALL` are structural context, not repository objects.
- Table functions on critical paths are resolved to AMDP when possible.
- Static complexity is an indicator, not proof of runtime performance problems.

## Local exports

- Existing local exports are optional evidence.
- abapGit is only one possible producer and is never required or invoked.
- Live source and local exports are reconciled by canonical identity and fingerprint.

## Guided collaboration

- Discover before asking.
- Questions use choices when helpful, free text when choices would constrain the truth, and hybrid formats for technical blockers.
- Non-blocking gaps are deferred or continued with limitations.
- Human assistance is used only after safe fallbacks are exhausted.

## Templates

- Project templates are recursively discovered under `templates/`.
- Metadata is validated before selection.
- Duplicate IDs and aliases are never resolved by filesystem order.
- Only the selected template body is loaded.
- Source templates are never modified.

## Token and context optimization

- Agent and Skill are compact routers.
- Specialist references load on demand.
- Raw artifacts stay outside active context when possible.
- Evidence pointers replace repeated full source.
- Context is promoted selectively and safely evicted after completion.
