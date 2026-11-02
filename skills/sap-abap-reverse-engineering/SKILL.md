---
name: sap-abap-reverse-engineering
description: Read-only SAP reverse engineering with guided interaction, compact runtime context, CDS graph/lineage analysis, and recursive project-template selection.
---
# SAP ABAP Reverse Engineering

## Load policy
Load references only when triggered:
- Every interaction: `guided-interaction-core.md`, `safety-and-preflight.md`.
- Only when asking: `guided-question-patterns.md`.
- Intake/scope: `intake-output-and-scope.md`.
- One seed object: `single-object-bootstrap-scenario.md`, `adaptive-root-discovery.md`, `tool-capability-router.md`.
- Every tool-heavy phase: `runtime-context-management.md`, `evidence-pointer-contract.md`.
- Acquisition fallback: `source-acquisition-ladder.md`; supplied local files only: `local-repository-export-analysis.md`.
- CDS: `cds-dependency-analyzer.md`, `cds-discovery-and-field-lineage.md`; complexity/performance only: `cds-static-performance-analysis.md`.
- Evidence/finish: `evidence-coverage-and-completion.md`.
- `FUNCTIONAL_SPEC`/`BOTH`: `template-registry-and-recursive-scan.md`, `template-and-deliverables.md`, then the selected template only.

## State
Maintain compact registries for scope, routes, canonical nodes, unique edges, path occurrences, structural branches, evidence pointers, fingerprints, critical lineage, findings/risks, unresolved/confirmation items, coverage, interaction decisions, template selection, artifacts, and completion status. Full raw source/tool output is stored once and referenced, not duplicated.

## Workflow
1. Guided preflight and strict read-only verification.
2. Bounded assessment and one scope/profile checkpoint when needed.
3. Exact root resolution, reconnaissance, and type-specific discovery.
4. Evidence-ranked expansion with normalization, selective promotion, and eviction.
5. Evidence closure, static/runtime boundary, coverage, and stop decision.
6. Minimal human assistance only for exhausted critical blockers.
7. Selected deliverables, save/reopen validation, and final status.
