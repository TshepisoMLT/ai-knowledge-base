# Repository Catalog

**Inspection date:** 2026-11-09  
**GitHub account:** `TshepisoMLT`

## Owned repositories

### `TshepisoMLT/Glimpse`

- Default branch: `main`
- Visibility: public
- Archived: no
- Access: admin, maintain, push, pull
- Main technologies: Expo SDK 53, React Native, TypeScript, NativeWind, Zustand, Axios, AsyncStorage.
- Assessment: starter/demo application. The visible app entry point renders `AuthDemo` and `ExampleComponent`; the authentication store uses mock responses and the API client points at `https://api.example.com`.
- Context: [`projects/GLIMPSE.md`](projects/GLIMPSE.md)

### `TshepisoMLT/MeetBudy-v1`

- Default branch: `main`
- Visibility: public
- Archived: **yes**
- Access: admin, maintain, push, pull
- Main technologies: Expo SDK 51, React Native 0.74, TypeScript, Expo Router, NativeWind 2, Zustand, SWR, Supabase.
- Assessment: social networking app prototype. Several user-facing screens exist, but important flows are local/mock or incomplete; feed and story fetchers use a hard-coded private-LAN address.
- Context: [`projects/MEETBUDY-V1.md`](projects/MEETBUDY-V1.md)

### `TshepisoMLT/project-manager-final`

- Default branch: `main`
- Visibility: public
- Archived: no
- Access: admin, maintain, push, pull
- Main technologies: pnpm workspaces, Node.js 24, TypeScript 5.9, React, Vite, Wouter, Tailwind CSS 4, Express, Drizzle scaffolding, OpenAPI, generated API clients.
- Assessment: the shipped UI is a browser-local prototype backed by `localStorage`. A large OpenAPI contract and generated clients are present, but the API server currently registers only a health route and the Drizzle schema package is a placeholder.
- Context: [`projects/PROJECT-MANAGER-FINAL.md`](projects/PROJECT-MANAGER-FINAL.md)

## Other repositories visible to the connected account

### `mltcorptech/studious-palm-tree`

- Default branch: `main`
- Visibility: public
- Repository size reported: 0
- Relationship: collaborator; push and pull allowed, admin not allowed
- Assessment: no files were present on the default branch at inspection. No project-specific technical context can be responsibly inferred.
- Context: [`projects/STUDIOUS-PALM-TREE.md`](projects/STUDIOUS-PALM-TREE.md)

### `MLTCorp-tech/Introduction-to-MLTCorp`

- Default branch: `main`
- Visibility: public
- Access: pull only; no push/admin
- Contents inspected: `README.md`, an onboarding guide describing team setup, communication, project guidelines, and support channels.
- Context: [`projects/MLTCORP-INTRODUCTION.md`](projects/MLTCORP-INTRODUCTION.md)

## Interpretation rules

- **Owned** means the GitHub API reported the authenticated user as repository owner with administrative permissions.
- **Collaborator** means the repository was returned by the collaborator-affiliation query. Push access does not imply repository administration rights.
- **Organization-accessible** is used here for the repository returned by the organization-member affiliation query. Its actual permissions were read-only. The organization list endpoint returned no organizations, so do not infer broader organization administration or membership from this snapshot.
- Repository visibility and status can change. Re-check GitHub before relying on this inventory for permissions or current status.
