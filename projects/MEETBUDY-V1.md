# MeetBudy-v1 — Project Context

**Source repository:** [TshepisoMLT/MeetBudy-v1](https://github.com/TshepisoMLT/MeetBudy-v1)  
**Branch inspected:** `main`  
**Inspected:** 2026-11-09  
**Repository status:** public, **archived**

## What it is

A React Native / Expo social-networking prototype. The README describes a feed, stories, profiles, dark mode, messaging, video calling, events, interest groups, and community interactions. The inspected code includes real screen/component structure for a subset of these ideas, but several interactions remain local, placeholder, or incomplete.

Because GitHub marks this repository archived, treat changes as maintenance or historical work unless the owner intentionally unarchives it.

## Technology

- Expo SDK `~51.0.28`
- React Native `0.74.5`, React `18.2.0`
- Expo Router `~3.5.23`
- TypeScript `~5.3.3`
- NativeWind `^2.0.11`
- Zustand `^4.5.5` for local UI state
- SWR `^2.2.5` for feed/story request caching and revalidation
- Supabase JS `^2.45.4` for authentication
- Axios for feed/story REST requests

## Main structure

- `app/` — Expo Router route tree: public auth screens, tabs, messages, profile, settings, and layouts.
- `components/` — post, story, comment, message, and upload UI.
- `constants/` — theme colors and shared `Post`, `Story`, and `Comment` types.
- `stores/` — Zustand stores for home/theme, chats, comments, stories, and uploads.
- `utils/home/` — Axios fetchers for posts and stories.
- `lib/supabaseClient.ts` — Supabase client setup.

## Data flow found

### Authentication

`app/(public)/login.tsx` calls `supabase.auth.signInWithPassword`. `signup.tsx` calls `supabase.auth.signUp` and stores the username as user metadata. The client reads `EXPO_PUBLIC_SUPABASE_URL` and `EXPO_PUBLIC_SUPABASE_ANON_KEY`, using AsyncStorage to persist the Supabase auth session.

The login and signup screens are evidence of Supabase auth integration. They do not, by themselves, prove that application-wide route protection, user profile lifecycle, or all backend resources are implemented.

### Feed and stories

- `app/(tabs)/index.tsx` uses SWR and `getPosts` to load posts.
- `components/StoriesContainer.tsx` uses SWR and `getStories` to load stories.
- Both fetchers call the fixed address `http://192.168.40.112:8000/api/v1/...`.
- The Axios helpers send a hard-coded `x-api-key: test-key` header. They also send `Access-Control-Allow-Origin` as a request header; CORS response policy belongs on the server, not in a client request.

### Local-only interactions

`PostComponent` increments like/share counters in component state. The bookmark control has no active `onPress` handler in the inspected source. `UploadModal` marks live-stream and poll actions as TODO. `profile.tsx` displays hard-coded example profile data. Treat these as prototype UI, not durable social interactions.

## Key files

- [README](https://github.com/TshepisoMLT/MeetBudy-v1/blob/main/README.md)
- [Contribution guide](https://github.com/TshepisoMLT/MeetBudy-v1/blob/main/CONTRIBUTING.md)
- [Package manifest](https://github.com/TshepisoMLT/MeetBudy-v1/blob/main/package.json)
- [Expo config](https://github.com/TshepisoMLT/MeetBudy-v1/blob/main/app.json)
- [Supabase client](https://github.com/TshepisoMLT/MeetBudy-v1/blob/main/lib/supabaseClient.ts)
- [Home/feed screen](https://github.com/TshepisoMLT/MeetBudy-v1/blob/main/app/(tabs)/index.tsx)
- [Post component](https://github.com/TshepisoMLT/MeetBudy-v1/blob/main/components/PostComponent.tsx)
- [Stories container](https://github.com/TshepisoMLT/MeetBudy-v1/blob/main/components/StoriesContainer.tsx)
- [Post fetcher](https://github.com/TshepisoMLT/MeetBudy-v1/blob/main/utils/home/getPosts.ts)
- [Story fetcher](https://github.com/TshepisoMLT/MeetBudy-v1/blob/main/utils/home/getStories.ts)
- [Upload modal](https://github.com/TshepisoMLT/MeetBudy-v1/blob/main/components/UploadModal.tsx)

## Development commands

```bash
npm install
npx expo start
npm run android
npm run ios
npm run web
npm test
npm run lint
```

`npm test` uses the `jest-expo` preset and the script is configured as `jest --watchAll`. Run the commands only in a suitable local environment; this documentation inspection did not execute them.

## High-priority maintenance notes

1. **Archived repository:** verify whether unarchiving is intended before planning new feature work.
2. **Remove the LAN dependency:** move the posts/stories base URL into validated configuration and use a reachable HTTPS service outside development.
3. **Replace the test header:** do not treat `test-key` as authentication. Keep server credentials on the server.
4. **Stop logging auth configuration:** `supabaseClient.ts` logs the Supabase URL and anon key. Remove this logging. The anon key is a client key, but it still should not be needlessly emitted to logs; never expose a service-role key.
5. **Improve async error handling:** login currently does not wrap the Supabase call in `try/finally`; a thrown request can leave loading state stuck.
6. **Clarify implementation status:** persist and synchronize likes/comments/bookmarks only through authenticated backend operations; current local counters do not provide this.
7. **Fix navigation/layout issues only after confirming current behavior:** the tab layout sets `tabBarStyle.height` to `-100`, which is suspicious and should be tested on devices before changing.

## Guidance for AI contributors

- Preserve Expo Router conventions and the existing TypeScript/NativeWind component style.
- Keep UI state in the existing Zustand stores when it is genuinely cross-screen; use SWR consistently for remote reads.
- Separate remote data mutations from presentational counters and modal state.
- Check Android/iOS behavior; the code includes `ToastAndroid`, so do not assume every error path is cross-platform.
- Do not add feature claims to the README until the end-to-end behavior exists and has been tested.

## AI quick-start prompt

> This repository is archived. Read `README.md`, `CONTRIBUTING.md`, and `package.json`, then trace the exact screen/store/service involved. Distinguish Supabase auth from the LAN-based feed/story API and from local UI-only counters. Do not assume real-time messaging, video calls, durable likes, bookmarks, events, or polls are implemented without verifying their full path.
