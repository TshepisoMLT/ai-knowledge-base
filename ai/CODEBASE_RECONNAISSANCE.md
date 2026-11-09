# AI Workflow: Codebase Reconnaissance

Use this before a medium or large feature, unfamiliar bug, refactor, or architecture recommendation.

## 1. Establish the repository boundary

- Confirm repository, branch, working tree, and target package/app.
- Read `AGENTS.md`, README, project context docs, and contribution notes.
- Check whether the repository is archived, generated, a monorepo, or a prototype.
- Identify files that must not be changed directly (generated clients, lockfiles, build output, vendored code).

## 2. Map the project

Inspect:

- package manifests, workspace config, lockfile, runtime and framework versions;
- application entry points, routes, screens, and shared components;
- state management and data-fetching libraries;
- API clients, endpoint configuration, schemas, backend routes, and server middleware;
- persistence layer and migrations;
- auth/session lifecycle, roles, and access-control enforcement;
- tests, lint, typecheck, CI, build, and deployment workflows.

Do not read every generated or third-party file. Start with the tree, then follow imports and runtime call paths.

## 3. Draw the real data path

For each relevant feature, answer:

1. What UI initiates it?
2. Which component/hook/store handles state?
3. Which service/API is called?
4. Which server handler validates and authorizes it?
5. Where is data persisted?
6. How does the UI refresh or receive updates?
7. Which tests prove the behavior?

Record missing links. An API schema alone is only a contract; an installed dependency alone is only available tooling.

## 4. Classify evidence

Use these labels consistently:

- **Implemented:** end-to-end code path exists and has been verified.
- **Partial:** some layers exist, but the whole user flow is incomplete.
- **Demo/mock:** hard-coded, simulated, sample, or local-only behavior.
- **Scaffolded:** configuration, schema, generated client, or placeholder exists without a complete runtime path.
- **Planned:** explicitly described as future work/TODO.
- **Unknown:** not enough evidence yet.

## 5. Deliver a useful map

Before changing architecture, summarize the current path, existing patterns, known constraints, relevant tests, and a minimal implementation plan. Link the exact files rather than merely naming directories.
