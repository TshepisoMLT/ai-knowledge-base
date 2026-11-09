# Reusable AI Coding Prompt

You are working in **[repository / project]**.

## First, understand the codebase

Read `AGENTS.md`, the project README, and the relevant project context note. Inspect the current branch, package manifests, entry points, and exact files involved. Trace the behavior across UI, state, service/API, server, and persistence. Verify whether each dependency or API path is actually wired into the running application.

## Task

[Describe the requested change in concrete user-visible terms.]

## Constraints

- Follow the repository's existing conventions.
- Preserve unrelated behavior and keep the diff focused.
- Do not add dependencies or upgrade packages without justification.
- Do not expose secrets or private data.
- Distinguish implemented behavior from mock/demo/scaffolded/planned behavior.

## Acceptance criteria

- [ ]
- [ ]

## Verification

Run the relevant tests, lint, typecheck, and build commands available in the package manifests. Report exactly what ran and what could not run.

## Final response

Summarize the implementation, files changed, verification results, and remaining limitations. Update project documentation if the change alters architecture, commands, API behavior, or data/security boundaries.
