# AI Knowledge Base

A dedicated Markdown repository for AI coding assistants, project context, engineering workflows, and reusable templates.

## Purpose

This repository is the shared source of project understanding for AI coding agents working across MLTCorp and related products. It stores:

- Standing instructions for AI contributors (`AGENTS.md`)
- Per-project context notes under `projects/`
- Reusable AI workflow guides under `ai/`
- Templates for specs, handoffs, ADRs, and prompts under `templates/`
- A catalog of linked repositories and their roles

Keep this repository focused on durable context. Ephemeral task notes, secrets, and large generated artifacts do not belong here.

## Layout

```
.
├── AGENTS.md                 # Baseline instructions for AI coding agents
├── README.md                 # This file
├── FILE_INDEX.md             # Flat list of Markdown files
├── REPOSITORY_CATALOG.md     # Linked code repositories and roles
├── PUBLISH.md                # How this folder was published to GitHub
├── ai/                       # Reusable AI engineering workflows
│   ├── BUG_TRIAGE.md
│   ├── CODEBASE_RECONNAISSANCE.md
│   ├── DOCUMENTATION_POLICY.md
│   ├── FEATURE_WORKFLOW.md
│   ├── SECURITY_REVIEW.md
│   └── TESTING_AND_VALIDATION.md
├── projects/                 # Project-specific context notes
│   ├── GLIMPSE.md
│   ├── MEETBUDY-V1.md
│   ├── MLTCORP-INTRODUCTION.md
│   ├── PROJECT-MANAGER-FINAL.md
│   └── STUDIOUS-PALM-TREE.md
└── templates/                # Reusable document templates
    ├── ARCHITECTURE_DECISION_RECORD.md
    ├── BUG_REPORT_TEMPLATE.md
    ├── FEATURE_SPEC_TEMPLATE.md
    ├── PROJECT_CONTEXT_TEMPLATE.md
    ├── PROMPT_TEMPLATE.md
    └── SESSION_HANDOFF.md
```

## How AI agents should use this repo

1. Start with `AGENTS.md`.
2. Open the relevant note under `projects/` for the product or service being changed.
3. Follow the workflow guides under `ai/` for reconnaissance, features, bugs, testing, security, and documentation.
4. Prefer templates under `templates/` when creating new specs, ADRs, or handoffs.
5. Treat executable code and tests in the target repository as higher priority than any prose claim here when the two disagree.

## Maintenance rules

- Update project notes when architecture, commands, data boundaries, or public behavior change.
- Prefer short, concrete, verifiable statements over marketing language.
- Distinguish implemented behavior from planned, mocked, or scaffolded work.
- Do not store secrets, tokens, private keys, or production credentials.
- Keep notes focused; link out to code and issue trackers instead of duplicating large implementation detail.

## Related repositories

See `REPOSITORY_CATALOG.md` for the current map of code repositories and how they relate to the project notes in this knowledge base.
