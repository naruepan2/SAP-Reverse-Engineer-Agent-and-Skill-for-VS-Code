# Template Registry and Recursive Scan

## Applicability
Run only for `FUNCTIONAL_SPEC` or `BOTH`. Skip template discovery for `CHAT_SUMMARY`.

## Scan boundary
Recursively scan only below:

```text
skills/sap-abap-reverse-engineering/templates/
```

Discover every `template.yaml` at any depth. Never follow symbolic links, absolute paths, parent traversal (`..`), or references outside the templates root.

Ignore by default:
- folders beginning with `.`;
- `archive/`, `archived/`, `backup/`, `examples/`, and `drafts/`;
- metadata with `status: ARCHIVED`, `DISABLED`, or `DRAFT`;
- files not referenced by valid template metadata.

## Supported layouts
Simple project layout:

```text
templates/<PROJECT>/template.yaml
templates/<PROJECT>/functional-specification-template.md
```

Nested layout:

```text
templates/<PROJECT>/<DOCUMENT_TYPE>/<VERSION>/template.yaml
templates/<PROJECT>/<DOCUMENT_TYPE>/<VERSION>/template.md
```

## Required metadata
Each active template must provide:

```yaml
project_id: <unique project id>
template_id: <globally unique template id>
version: <string>
document_type: FUNCTIONAL_SPECIFICATION
status: ACTIVE
display_name: <user-facing name>
aliases: []
template_file: <relative filename inside the metadata folder>
description: <short usage guidance>
```

For backward compatibility, missing `document_type`, `status`, `display_name`, or `description` may be defaulted respectively to `FUNCTIONAL_SPECIFICATION`, `ACTIVE`, `template_id`, and an empty description. Record each default as a validation warning.

## Validation
For every discovered metadata file:
1. Parse YAML safely.
2. Require non-empty `project_id`, `template_id`, `version`, and `template_file`.
3. Resolve `template_file` relative to the metadata folder.
4. Reject absolute paths, `..`, symlinks escaping the root, missing files, empty files, and unsupported document types.
5. Validate Markdown fences and required headings when declared.
6. Calculate SHA-256 for the metadata and template.
7. Never modify the source metadata or template.

## Registry
Build one compact registry entry per template:

```yaml
template_registry:
  - project_id: RTR
    template_id: RTR_FS
    version: "2.1"
    document_type: FUNCTIONAL_SPECIFICATION
    status: ACTIVE
    display_name: RTR Functional Specification
    aliases: [rtr, record-to-report]
    description: Finance, accounting, and reconciliation
    metadata_path: templates/RTR/template.yaml
    template_path: templates/RTR/functional-specification-template.md
    metadata_sha256: <hash>
    template_sha256: <hash>
    validation: VALID
```

Do not load full Markdown bodies while building the registry. Load the selected template only after selection.

## Duplicate and ambiguity rules
Mark entries `AMBIGUOUS` and do not auto-select when active templates conflict on:
- `template_id`;
- the same `project_id` + `document_type` + `version`;
- normalized alias within the same document type;
- an exact normalized folder/project name that maps to multiple active templates without a version rule.

Do not silently prefer filesystem order.

## Matching order
Match the user's request in this order:
1. exact `project_id`;
2. exact `template_id`;
3. exact project folder name;
4. exact template filename;
5. exact configured alias;
6. normalized name ignoring case, spaces, hyphens, and underscores.

Fuzzy similarity alone cannot select automatically.

## Selection behavior
- One exact valid match: select without asking and report name/version.
- Multiple valid matches: show concise choices with display name, version, description, and relative path; ask once.
- No project requested: offer a detected recommendation, Default, choose from registry, let AI decide, or specify another name.
- Requested template missing or invalid: explain briefly and offer valid candidates or Default.
- Duplicate/ambiguous registry: ask the user or use Default only when the user accepts fallback.

## Output safety
Instantiate the selected template into a new output file. Never write to the source template or metadata. Record selection method, version, relative path, SHA-256, warnings, and fallback reason in Document Control.
