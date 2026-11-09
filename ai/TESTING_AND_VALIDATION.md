# AI Workflow: Testing and Validation

## General rules

- Inspect the current package manifest before choosing commands.
- Prefer targeted tests first, then relevant package and workspace checks.
- Do not assume a documented command is an npm/pnpm script; inspect the manifest.
- Report commands and results truthfully. If not run, label them as suggested checks.

## Repository-specific commands from the inspected manifests

### Glimpse

```bash
npm install
npm start
npm run android
npm run ios
npm run web
```

The inspected `package.json` did not define test, lint, typecheck, or build scripts. `package-scripts.md` documents helpful CLI suggestions, but those are not package scripts unless separately configured.

### MeetBudy-v1

```bash
npm install
npx expo start
npm run android
npm run ios
npm run web
npm test
npm run lint
```

The `test` script uses Jest in watch-all mode with the `jest-expo` preset. Confirm the current repository is accessible for changes; it was archived in the inspection snapshot.

### project-manager-final

From the workspace root:

```bash
pnpm install
pnpm run typecheck
pnpm run build
pnpm --filter @workspace/project-manager run dev
pnpm --filter @workspace/project-manager run typecheck
pnpm --filter @workspace/project-manager run build
```

The API server has its own scripts under `artifacts/api-server`. Its start command requires `PORT`.

## What tests should cover

- happy path and invalid input;
- empty/loading/error states;
- unauthorized and cross-user access attempts for protected operations;
- offline and timeout behavior for network operations;
- persistence across reload/restart where promised;
- platform-specific behavior for native APIs;
- migration and generated-client consistency for API/schema changes.

The commands above were read from repository manifests/docs; they were not executed as part of the documentation inspection.
