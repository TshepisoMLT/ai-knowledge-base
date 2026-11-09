# AI Workflow: Bug Triage

## Reproduce first

- Capture exact steps, expected result, actual result, environment, platform, and relevant logs.
- Determine whether the issue is deterministic, intermittent, device-specific, network-specific, or data-specific.
- Reproduce with the smallest input and avoid changing multiple variables at once.

## Trace the failing path

- Follow the event from UI to state, service, API, server, and persistence.
- Identify the first incorrect value or failed boundary.
- Inspect recent related changes and existing tests.
- Separate root cause from symptoms and secondary errors.

## Fix safely

- Write a regression test that fails before the fix when feasible.
- Fix the narrowest root cause without hiding the error or weakening validation.
- Preserve cancellation, retries, cleanup, loading state, and error handling.
- Avoid logging tokens, passwords, session data, or user content.

## Verify

- Run the regression test and related suite.
- Run the relevant typecheck/lint/build.
- Re-test the original reproduction and a nearby edge case.
- Report any environment-dependent verification that could not be performed.
