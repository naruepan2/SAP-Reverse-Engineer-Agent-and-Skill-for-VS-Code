# Guided Question Patterns

## Load condition
Load only when the Agent must ask a user-facing question. These are adaptable patterns, not mandatory scripts.

## Recommended-settings shortcut
When evidence supports a bundle, show the recommendation and allow:
1. Use all recommended settings.
2. Adjust selected settings.
3. Let AI decide from discovered evidence.
4. Specify requirements in the user's own words.

Use progressive disclosure; show detailed settings only when adjustment is requested.

## Preflight choices

### Output mode
1. Chat Summary: concise findings and risks in Chat.
2. Functional Specification: Markdown using a project template.
3. Both: Chat Summary and document from one analysis state.
4. Let AI recommend.

### Objective
1. Understand the existing solution.
2. Create a Functional Specification.
3. Analyze change impact.
4. Review logic or a suspected issue.
5. Prepare test scenarios.
6. Other: specify briefly.

### Analysis profile
1. Quick: architecture and important dependencies.
2. Standard: process, main logic, and critical fields.
3. Deep: lineage, configuration, authorization, companions, and evidence coverage.
4. Extended: broad and deep analysis for large solutions.
5. Let AI assess and recommend.

### Language
1. Thai.
2. English.
3. Thai with SAP technical terms in English.
4. Conversation language.
5. Other: specify.

### Project template for FS/BOTH
First apply `template-registry-and-recursive-scan.md`.
1. Recommended valid template, with name/version/description.
2. Bundled Default.
3. Choose from the validated registry.
4. Let AI choose from document intent and evidence.
5. Specify another project or template.

Do not present invalid, archived, duplicate, or ambiguous entries as normal choices.

## Targeted critical assistance
First summarize what was reached, what is unavailable, attempts made, why it matters, and the smallest useful action. Then offer concise choices such as:
1. Continue and mark the item `UNVERIFIED` (recommended when safe).
2. Show short lookup steps.
3. Supply a known value.
4. Provide a source file.
5. Add to the follow-up list.

If no response is received for a non-blocking request, continue with the limitation and do not ask again.
