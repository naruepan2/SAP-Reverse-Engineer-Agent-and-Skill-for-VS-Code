# Single-Object Bootstrap Scenario

## Trigger and principle
Apply when one SAP object is supplied with little context. The object is a discovery seed, not the final scope. Do not ask for package, type, source, dependencies, DCL, service, or implementation details before safe discovery.

## State machine

### S0 Batched intake
Resolve only non-discoverable inputs: system/destination, client when required, objective, output mode, language/path, profile or permission to recommend, and project template for document modes. Apply guided interaction rules.

### S1 Capability map
Apply `tool-capability-router.md`. Verify providers and map exact search, properties, source, dependencies, where-used, CDS analysis, companion lookup, metadata, and supplied local files. If no live provider works but an export is supplied, use `LOCAL_EXPORT_ONLY` with limitations.

### S2 Root identity
Apply `adaptive-root-discovery.md`. Resolve exact identity and aliases safely. Record canonical name/type, package, source URI, active state, system/client, provider, fingerprint, and resolution state. Ask only for materially ambiguous exact candidates.

### S3 Reconnaissance
Read root properties/source; identify direct references, exposed fields/parameters/keys, transformations, authorization and object-type indicators. Create a provisional plan, risks, and unknowns.

### S4 Type-specific discovery
Load only relevant references:
- CDS: `cds-dependency-analyzer.md`, `cds-discovery-and-field-lineage.md`, and `cds-static-performance-analysis.md` when performance is discussed.
- RAP/service/UI: resolve interface/projection, behavior, implementation, service/binding, metadata, DCL, actions, UI exposure, and authorization using source/repository evidence.
- Program/class/function: resolve includes/methods, static calls, SQL, messages, authorization, configuration, dynamic seeds, and bounded impact.

### S5 Scope/profile checkpoint
Summarize root identity, available evidence, estimated breadth/depth, proposed companions, exclusions, recommended profile/budget, and outputs. Pause only if profile or a material scope decision is unresolved; then freeze scope.

### S6 Evidence-ranked waves
A. Critical custom path and direct exposure.
B. Critical field/filter/key lineage and branch semantics.
C. Companion DCL/AMDP/RAP/service/UI/configuration artifacts.
D. Standard foundations deeply only when they transform critical behavior; otherwise inventory.
E. Objective-relevant bounded upstream impact.
F. High-priority gap/conflict closure only.

Apply `runtime-context-management.md` and `evidence-pointer-contract.md` throughout.

### S7 Coverage and stopping
Apply `evidence-coverage-and-completion.md`. Stop when critical outputs/branches have evidence paths or blockers, critical implementations/security/companions are resolved or blocked, high-priority gaps are documented, limits are recorded, and selected outputs can be produced honestly. Budget alone neither proves completion nor requires continued traversal.

### S8 Deliverables
Generate selected outputs from one frozen state. Record provenance, metrics source, coverage, conflicts, exclusions, runtime backlog, confirmation queue, and completion status.
