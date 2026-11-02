# Project Templates

Add one folder per project, or use nested document-type/version folders. Every active template requires `template.yaml` and a referenced Markdown file.

```text
templates/
├── default/
│   ├── template.yaml
│   └── functional-specification-template.md
├── SMILE/
│   ├── template.yaml
│   └── functional-specification-template.md
└── RTR/functional-specification/v2/
    ├── template.yaml
    └── template.md
```

The Skill recursively scans `templates/`, validates metadata and paths, builds a compact registry, detects duplicate IDs/aliases, and loads only the selected template body. Source templates are never modified.

Required metadata: `project_id`, `template_id`, `version`, `document_type`, `status`, `display_name`, `description`, `aliases`, and `template_file`.
