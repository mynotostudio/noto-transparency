# Security

This documents Noto's real security practices. No secrets, keys, or credentials are included here.

## Encryption

- **In transit:** All connections between your device and Noto use **TLS** (HTTPS).
- **At rest:** The Base44-managed database and object storage are **encrypted at rest**.
- **Private files:** Served only via **signed, expiring URLs**, so a link cannot be reused after it expires.

## Authentication

- Account authentication is managed by the **Base44 auth platform**.
- Supports **email + password** and **Google OAuth**.
- Password reset and **email verification (OTP)** flows are built in.
- Passwords are handled by the platform (hashed); Noto never stores or logs plaintext passwords.

## Access control

- **Row-Level Security (RLS):** every user-content entity enforces that a user can only **read, update, and delete** their own records. Admins can manage records across the app for support.
- **Admin-only functions:** scheduled/maintenance functions verify `user.role === 'admin'` and return 403 otherwise, so non-admins cannot trigger them directly.
- **Shared notes:** access is explicit (read or edit) and granted only to users you invite; you can only share notes you own.
- **Edit-access checks:** collaborative note updates verify ownership or explicit edit permission before applying changes.

## Data isolation

- Each user's structured data is isolated by `created_by_id` enforced through RLS.
- Shared content is gated by explicit `shared_read` / `shared_edit` lists.

## Secret management

- Secrets (API keys, integration tokens) are stored in the Base44 platform's secret management / environment variables — never in source code, never exposed to the client, and never included in this repository.
- OAuth connector tokens (e.g. for this transparency repository's GitHub integration) are issued by the platform and used server-side only.

## Backups

- Automated, **encrypted** backups, retained up to 30 days, managed by Base44.

## Input validation & abuse controls

- All backend function inputs are **validated and bounded** (type checks, max lengths).
- The **contact form** uses a honeypot field and **per-IP rate limiting** to block bots and spam.
- AI message length is capped to limit abuse and cost.
- The **calendar URL import** validates the URL scheme, blocks private/internal IP ranges (SSRF protection), validates each redirect hop, and enforces timeouts and size limits.

## Output sanitization

- AI-generated HTML (e.g. revision sheets) is sanitized: `<script>`/`<style>` tags and inline `style` attributes are stripped.
- User-authored and AI-generated HTML rendered in the app is sanitized with **DOMPurify** to prevent XSS.

## Monitoring

- Backend function execution logs are available to Noto admins for debugging and security auditing.
- Platform-level monitoring and incident response are handled by Base44.

## Security updates

- The Noto application is built on the Base44 platform, which handles infrastructure patching and platform-level security updates.
- Application dependencies are kept within the platform's supported, maintained package set.

## What Noto never exposes

- API keys, passwords, tokens, database credentials, private keys, production secrets, or sensitive internal infrastructure details — none of these appear in this repository or in the app.
