# Instructions for AI Coding Agents

These instructions apply to work performed in this knowledge-base repository and should be used as the baseline when assisting with the linked projects.

## Before changing code

1. Read the relevant project note in `projects/` and the target repository's own `README`, `AGENTS.md`, `AI_CONTEXT.md`, or contribution guide.
2. Inspect the current branch, working tree, package manifest, entry points, and the exact files involved.
3. Trace the feature through its UI, state, service/API, persistence, and tests before editing.
4. Check whether the implementation is real, mocked, scaffolded, or only described in documentation.
5. Identify existing conventions and reuse them unless there is a strong reason not to.

## Source-of-truth hierarchy

When sources disagree, use this order and explain material conflicts:

1. Current executable code and current package/workspace manifests.
2. Current tests and CI configuration.
3. API schemas and generated artifacts, for the contract they define only.
4. Project-specific engineering docs and `AGENTS.md` files.
5. README feature claims and older prose notes.

An OpenAPI path, generated client method, dependency, or README bullet does **not** prove a feature is wired up or available in production. Verify the server route, service integration, persistence, permissions, and user flow.

## Implementation standards

- Make the smallest complete change that solves the request.
- Follow the project's existing language, naming, formatting, component, state, navigation, and styling patterns.
- Prefer explicit types and narrow interfaces; avoid introducing `any` where a useful type can be defined.
- Reuse installed dependencies. Do not add or upgrade packages without explaining why and checking platform/framework compatibility.
- Keep generated files generated. Edit their source schema/configuration and regenerate using the repository's established workflow when available.
- Preserve backward compatibility unless the requested change explicitly requires a break.
- Keep accessibility and keyboard/touch alternatives in mind.

## Verification and reporting

- Run the narrowest relevant tests or checks, then broader checks when practical.
- Do not say tests passed unless they were actually run and passed.
- If a check cannot run, state exactly which check and why.
- Summarize changed files, behavior, verification, and remaining risks.
- Update project-specific Markdown when a change alters architecture, public API behavior, data/security boundaries, or developer workflow.

## Safety

- Do not commit secrets, tokens, private keys, or production credentials.
- Prefer least-privilege defaults for auth, storage, and network access.
- Treat user data and PII carefully; do not log or expose sensitive fields unnecessarily.

## When uncertain

Ask a clarifying question, propose a short plan, or implement the safest reversible interpretation and document the assumption.