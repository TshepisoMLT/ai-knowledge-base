# AI Workflow: Feature Delivery

## Discovery

- Restate the user-visible outcome and identify acceptance criteria.
- Read project guidance and map the current data flow.
- Determine whether the feature is UI-only, local state, remote API, or cross-service.
- Check authorization, privacy, accessibility, offline behavior, error states, and migrations.
- Identify existing patterns to reuse and any conflicting product limitation.

## Design

- Propose the smallest coherent change across UI, state, services, server, persistence, and tests.
- Define typed inputs/outputs and explicit loading, success, empty, and error states.
- For shared data, design server-side ownership and authorization checks. Do not rely on client-side hiding.
- For API changes, update the source OpenAPI/schema and regenerate generated code using the repo's documented workflow.
- For persisted schema changes, include migration and rollback considerations.

## Implementation

- Change the source of truth, not generated outputs by hand.
- Preserve naming, routing, component, and state conventions.
- Avoid unrelated refactors and dependency upgrades.
- Keep credentials and private data out of code, tests, logs, and documentation.
- Add tests alongside behavior rather than postponing all validation.

## Verification

- Run focused unit/component/integration tests.
- Run lint, typecheck, and build scripts applicable to the package.
- Test critical edge cases and at least one failure path.
- For mobile features, check the affected platform APIs and permissions on the target platforms.
- For full-stack features, verify the UI-to-server-to-database round trip and authorization boundary.

## Close-out

Report:

- behavior implemented;
- important files changed;
- checks actually executed and results;
- limitations, migration steps, or manual setup;
- documentation that was updated.

Do not mark a feature complete if only its UI or API schema exists.
