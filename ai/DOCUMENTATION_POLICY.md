# AI Workflow: Documentation Policy

## What belongs in this knowledge base

- A short project purpose and verified status.
- Actual stack versions from manifests.
- Important entry points and data flow.
- Development, test, typecheck, build, and deployment commands.
- Auth, persistence, networking, and privacy boundaries.
- Implemented versus partial/demo/scaffolded/planned features.
- Known risks and source links.

## Writing rules

- Date each substantial repository review.
- Link to source files and exact paths.
- Prefer concise facts over broad claims and marketing copy.
- Label assumptions and unknowns.
- Do not include secrets, private environment values, personal data, or unapproved internal information.
- Avoid copying entire source files into docs; summarize behavior and link to the code.

## When to update

Update a project note when the entry point, primary stack, architecture, API boundary, persistence, auth, key commands, deployment, or feature status changes.

When a claim becomes stale, fix it in the same change that makes it stale when practical. If the code and docs conflict, inspect current implementation and record the discrepancy rather than silently repeating old docs.

## Suggested review checklist

- [ ] Verify repository default branch and archived status.
- [ ] Recheck package and workspace manifests.
- [ ] Recheck app entry points and key routes.
- [ ] Trace the relevant UI-to-data path.
- [ ] Recheck API routes and DB schema/migrations.
- [ ] Recheck test/build commands.
- [ ] Recheck auth and data boundaries.
- [ ] Update the reviewed date and source links.
