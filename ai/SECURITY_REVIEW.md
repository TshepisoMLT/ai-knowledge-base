# AI Workflow: Security and Privacy Review

Use this checklist for auth, API, persistence, uploads, integrations, logs, and deployment changes.

## Secrets and configuration

- No real credentials, tokens, passwords, private keys, service-role keys, or sensitive environment values in source or Markdown.
- Client-exposed variables (for example, names prefixed with `EXPO_PUBLIC_`) must contain only values designed to be public.
- Server secrets must remain server-side and be validated at startup.
- Do not log credentials, authorization headers, session cookies, or full sensitive payloads.

## Authentication and authorization

- Verify the real identity/session provider and token lifecycle.
- Check authorization on the server for every protected object and action.
- Enforce tenant/workspace boundaries and ownership, not just role-based UI visibility.
- Check session expiry, revocation, refresh, logout, and unauthorized responses.

## Data and APIs

- Validate inputs at trust boundaries and constrain file type/size.
- Use HTTPS for production service endpoints.
- Avoid hard-coded LAN addresses and test API keys in shipped clients.
- Do not treat CORS headers sent by a client as access control.
- Check rate limits, error leakage, idempotency, and auditability where relevant.

## Persistence

- Treat localStorage, AsyncStorage, and other client stores as client-controlled.
- Do not present browser-local persistence as shared, secure, or backed up.
- Review migrations, backups, data retention, deletion, and export semantics.

## Documentation

- Describe data boundaries and known limitations accurately.
- Use fake examples and placeholders; never paste live values.
- Keep private organization context out of public repositories unless explicitly approved.
