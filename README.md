# SAP Reverse Engineer Agent and Skill for VS Code

Evidence-driven, strictly read-only SAP ABAP/CDS/RAP reverse engineering for GitHub Copilot and VS Code.

**Current version:** `V8.7.2`

## Purpose

This repository contains an Agent, Skill, specialist references, and project-aware Functional Specification templates for reverse engineering existing SAP solutions through verified read-only tooling such as SAP ADT MCP, ABAP FS, ARC-1, or supplied local repository exports.

The workflow is designed to:

- start from one SAP object when that is all the user provides;
- discover object type, package, source, and dependencies autonomously;
- use SAP ADT Dependency Analyzer evidence for CDS when available;
- preserve field lineage, branch context, DCL/AMDP/RAP/service companions, and evidence provenance;
- generate a Chat Summary, Functional Specification, or both;
- ask the user as little as possible and never guess unsupported facts;
- remain strictly read-only and never modify SAP programs, repository objects, transports, or business data.

## Repository structure

```text
.
├── agents/
│   └── sap-abap-reverse-engineer.agent.md
├── skills/
│   └── sap-abap-reverse-engineering/
│       ├── SKILL.md
│       ├── references/
│       └── templates/
├── docs/
│   ├── ARCHITECTURE_V8.7.2.md
│   ├── DECISION_LOG.md
│   └── ROADMAP.md
├── release-assets/
│   └── sap-abap-deep-reverse-engineering-v8.7.2.zip
├── CHANGELOG.md
├── CONTRIBUTING.md
├── SECURITY.md
└── VERSION
```

## Installation

1. Copy `agents/sap-abap-reverse-engineer.agent.md` to the Agent location used by the VS Code/GitHub Copilot environment, commonly `.github/agents/`.
2. Copy `skills/sap-abap-reverse-engineering/` to the Skill location used by the environment.
3. Preserve internal `references/` and `templates/` paths.
4. Add project templates under `skills/sap-abap-reverse-engineering/templates/<PROJECT>/`.

## Example request

```text
Reverse engineer ZC_RTR_ROU_OUTLEASELIABREP in system S4D, client 100.
Create both a Chat Summary and Functional Specification.
Let AI recommend the analysis profile and project template.
```

## Core safety rules

- `SAFE_READ` operations only.
- No create, edit, save, activate, transport, import, synchronization, posting, scheduling, or business execution.
- No unsupported guessing.
- Static complexity is not presented as a confirmed runtime performance defect.
- Existing local exports are optional evidence only. The Agent never invokes abapGit operations.

## Project templates

Each active template contains a `template.yaml` and one referenced Markdown template. The Skill recursively scans the templates directory, validates metadata and paths, detects duplicate identifiers and aliases, builds a metadata-only registry, and loads only the selected template body.

See `skills/sap-abap-reverse-engineering/templates/README.md`.

## Version history

See `CHANGELOG.md` and `docs/DECISION_LOG.md`.
