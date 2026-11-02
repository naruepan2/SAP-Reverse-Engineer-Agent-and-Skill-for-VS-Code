# CDS Static Performance Analysis

## Evidence layers
1. SQL Dependency Tree: hierarchy and data-source paths.
2. SQL Dependency Graph: connectivity and branch visualization.
3. Complexity Metrics: SAP-native statistical summary of SQL operations and expressions.
4. Used Columns and Generated SQL: selective structural/semantic evidence when available.
5. Source analysis: aliases, calculations, annotations, fallback and business semantics.
6. Runtime evidence: trace, execution plan and PlanViz, outside static reverse engineering.

## Native versus derived metrics
Label metrics as `SAP_NATIVE_METRIC` only when returned by SAP tooling. Label counts calculated from exports or registries as `AGENT_DERIVED_METRIC` and record the method.

Capture when available:
- tables, CDS views and table functions;
- inner/outer joins;
- UNION/UNION ALL;
- functions, CAST and CASE;
- aggregations and expressions;
- unique nodes/edges, maximum depth, occurrences, fan-in/fan-out;
- branch and critical-field coverage.

Use `not_available`, never guessed values.

## Finding classes
- `STATIC_COMPLEXITY`
- `STATIC_PERFORMANCE_RISK`
- `STRUCTURAL_REDUNDANCY_CANDIDATE`
- `FIELD_LINEAGE_GAP`
- `JOIN_FANOUT_RISK`
- `UNION_SEMANTIC_RISK`
- `RUNTIME_PERFORMANCE_UNVERIFIED`

## Interpretation rule
Metrics are indicators, not proof of a performance defect. A large graph may perform well; a small-looking CDS may have an expensive execution plan. Static findings may recommend runtime verification but must not claim elapsed time, bottleneck operator, memory, CPU, network cost or production impact.

## Redundant-branch rule
Classify a branch as `POTENTIALLY_REDUNDANT` only after checking used columns, join/filter contribution, grouping, calculations, authorization, semantic references, currency/unit references and UNION compatibility. Otherwise classify as `REQUIRED` or `UNRESOLVED`.

## Runtime handoff
For static risk, create a non-executed handoff specifying representative filters/volumes, generated SQL, ST05 or equivalent trace, execution plan/PlanViz and expected measurements. Static Reverse Engineer never executes traces or business queries.
