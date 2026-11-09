# Glimpse — Project Context

**Source repository:** [TshepisoMLT/Glimpse](https://github.com/TshepisoMLT/Glimpse)  
**Branch inspected:** `main`  
**Inspected:** 2026-11-09  
**Repository status:** public, not archived

## What it is

A React Native / Expo starter app intended to demonstrate mobile capabilities and a reusable app foundation. The README advertises image and document picking, sharing, camera, audio/video, notifications, biometrics, background tasks, network monitoring, contacts, and file-system operations.

**Important implementation distinction:** the inspected `App.tsx` currently renders a welcome header, `AuthDemo`, and `ExampleComponent`. The advertised capability list and installed Expo modules should not be treated as proof that all those user flows are implemented.

## Technology

- Expo SDK `53.0.20`
- React Native with TypeScript
- NativeWind v4 / Tailwind CSS
- Zustand with `persist` and AsyncStorage
- Axios for the HTTP client
- `@shopify/flash-list` and a broad set of Expo SDK modules

The package manifest is the authority for the currently declared versions and dependencies.

## Important files

| Area | File | Purpose |
|---|---|---|
| Entry | [`App.tsx`](https://github.com/TshepisoMLT/Glimpse/blob/main/App.tsx) | Composes the demo screen |
| Auth UI | [`components/AuthDemo.tsx`](https://github.com/TshepisoMLT/Glimpse/blob/main/components/AuthDemo.tsx) | Login/register demo controls |
| Auth state | [`stores/useAuthStore.ts`](https://github.com/TshepisoMLT/Glimpse/blob/main/stores/useAuthStore.ts) | Persisted Zustand auth state and mock actions |
| API | [`services/api.ts`](https://github.com/TshepisoMLT/Glimpse/blob/main/services/api.ts) | Axios instance, interceptors, endpoint helpers |
| Context | [`AI_CONTEXT.md`](https://github.com/TshepisoMLT/Glimpse/blob/main/AI_CONTEXT.md) | AI coding conventions and examples |
| Overview | [`README.md`](https://github.com/TshepisoMLT/Glimpse/blob/main/README.md) | Stack, package inventory, setup overview |
| Commands | [`package-scripts.md`](https://github.com/TshepisoMLT/Glimpse/blob/main/package-scripts.md) | Development/build command reference |
| Manifest | [`package.json`](https://github.com/TshepisoMLT/Glimpse/blob/main/package.json) | Actual dependency and npm script list |

## Architecture and behavior found

### Authentication is currently mocked

`useAuthStore` defines `login`, `register`, `logout`, and setter/clear actions. Login and registration wait for a one-second timeout, construct a mock user, and assign the literal mock token `mock-jwt-token`. Zustand persistence stores the user, token, and authenticated flag in AsyncStorage. This is a demo state flow, not verified production authentication.

### The API endpoint is a placeholder

`services/api.ts` configures Axios with `https://api.example.com`. A request interceptor attaches the current Zustand token as a bearer token. A 401 response clears the local auth state. The code contains commented-out token-refresh ideas, not a working refresh implementation.

### UI composition is small

`App.tsx` imports `AuthDemo` and `ExampleComponent`. The README's larger list of media, camera, background, contacts, and notification capabilities may describe available dependencies or intended demonstrations; verify each feature's actual call sites before extending it.

## Development commands

The `package.json` scripts are:

```bash
npm install
npm start
npm run android
npm run ios
npm run web
```

Build and utility commands documented in `package-scripts.md` are command suggestions, not npm scripts defined by the manifest. No test script is defined in the inspected `package.json`.

## Guidance for AI contributors

- Use TypeScript and functional React components.
- Follow the existing NativeWind classes for styling; the project's AI context discourages `StyleSheet` for normal UI styling.
- Reuse the Zustand store pattern for app-wide state when appropriate.
- Reuse the Axios service only after replacing the placeholder base URL with an explicit, environment-driven configuration.
- Add real auth/API behavior behind clear service boundaries. Do not turn mock credentials into a production security design.
- Before claiming a listed Expo feature works, inspect its implementation and exercise the flow on target platforms.

## Risks and follow-up checks

- Replace the hard-coded API placeholder with validated environment configuration before real integration.
- Replace mock login/register behavior with an actual auth provider and secure token lifecycle.
- Ensure secrets are never included in the app bundle. Client-side public configuration is not a substitute for server-side authorization.
- Check platform permissions and test Android/iOS separately for native capabilities.
- Add meaningful tests and lint/typecheck scripts if the project is to become production-maintained.

## AI quick-start prompt

> Read `AI_CONTEXT.md`, `README.md`, and `package.json` first. Then inspect the exact components, Zustand store, and service involved. The visible auth flow is mocked and the Axios base URL is a placeholder; do not assume the README's broad package inventory means all features are implemented. Make the smallest TypeScript/NativeWind-consistent change and report the checks actually run.
