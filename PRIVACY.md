# Privacy Overview

This document is a plain-language summary of how Noto handles personal data. For the full technical detail, follow the linked documents in this repository.

## Who Noto is

Noto is a student productivity application: notes, calendar, tasks, mind maps, focus timer, flashcards, quizzes, revision sheets, and AI-powered study tools.

## What data Noto collects

| Category | Examples |
|---|---|
| Account information | Email address, name, role, preferences (country, reminder settings) |
| Study content | Notes, tasks, calendar events, exams, mind maps, flashcards, quizzes, focus sessions, revision sheets, study-time logs, custom AI agents |
| Uploaded files | PDFs, documents, slides, images attached to notes or stored in Noto Cloud |
| AI request data | Prompts and study material sent to AI providers when you trigger an AI feature |
| Usage analytics | Anonymous, aggregated in-app events |
| Contact messages | Name, email, and message submitted via the contact form |

See [DATA_MAP.md](./DATA_MAP.md) for the full map.

## Why data is collected

- **To provide the service** you signed up for (contract).
- **To power AI study features** you explicitly trigger (consent).
- **To improve the product** using aggregated analytics (legitimate interest).
- **To respond to support messages** you send us (consent / legitimate interest).

## Where data is stored

Noto is built on the **Base44** platform, which provides the database, file storage, authentication, backups, analytics, and AI routing. Storage is cloud-based and managed by Base44. See [DATA_ARCHITECTURE.md](./DATA_ARCHITECTURE.md).

## Who processes data

- **Base44** — hosting platform (database, storage, auth, backups, analytics, email).
- **AI providers** — process AI requests you trigger. See [AI_DATA_PROCESSING.md](./AI_DATA_PROCESSING.md) and [THIRD_PARTY_PROVIDERS.md](./THIRD_PARTY_PROVIDERS.md).

## AI processing

Several Noto features use AI. When they do, the relevant study material and your prompt are sent to an AI provider to generate a response. Noto does **not** store your AI inputs beyond the request itself; AI outputs you choose to save (e.g. a generated flashcard) are stored as your study content.

Noto enables "no model training" terms in its AI provider agreements where available. **Whether each provider retains inputs or uses them for training is TO BE VERIFIED against each provider's current data-processing terms** — see [AI_DATA_PROCESSING.md](./AI_DATA_PROCESSING.md).

## How long data is kept

Most data is kept until you delete it. Soft-deleted items are purged after 30 days. Backups are kept up to 30 days. Analytics raw events up to 12 months. See [DATA_RETENTION.md](./DATA_RETENTION.md).

## Your rights

Depending on your country, you have rights to access, correct, delete, port, restrict, object to, and withdraw consent for processing of your data. See [USER_RIGHTS.md](./USER_RIGHTS.md).

## Deleting your data

You can delete individual items, or delete your entire account from Settings. See [DATA_DELETION.md](./DATA_DELETION.md).

## Exporting your data

You can download a ZIP archive of all your data from the in-app Privacy dashboard. See [DATA_EXPORT.md](./DATA_EXPORT.md).

## Security

Encryption in transit and at rest, per-user data isolation, signed file URLs, and input validation. See [SECURITY.md](./SECURITY.md).

## International transfers

Cloud hosting and AI providers may process data outside your country under appropriate safeguards. See [INTERNATIONAL_TRANSFERS.md](./INTERNATIONAL_TRANSFERS.md).
