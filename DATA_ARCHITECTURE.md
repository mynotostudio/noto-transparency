# Data Architecture

This documents Noto's actual data architecture and the flow of user data through it.

## High-level diagram

```
You (browser / mobile app)
   │
   ▼
Noto application  ──►  Base44 platform
                        ├── Database (entities, row-level security)
                        ├── Object storage (uploaded files + private files)
                        ├── Authentication (email/password, Google, OTP)
                        ├── Email service
                        ├── Analytics
                        └── AI routing (InvokeLLM) ──► AI providers (OpenAI / Google / Anthropic)
                                                          │
                                                          ▼
                                                  (transient processing)
```

## Components

### 1. Client (You)

| Field | Value |
|---|---|
| Purpose | You interact with Noto via a web browser or the published mobile app |
| Data processed | The content you create, upload, and request AI features on |
| Data stored | Local browser storage (preferences, drafts, UI state) |
| Provider | Your device / browser |
| Location | Your device |
| Retention | Until you clear it |
| Security | Standard browser security; no secrets stored client-side |
| Optional | — |
| Shared externally | No (only what you actively send to Noto) |

### 2. Noto application (Base44-hosted)

| Field | Value |
|---|---|
| Purpose | Serves the app UI and routes requests to data, AI, and integrations |
| Data processed | All user requests and responses |
| Data stored | No persistent user data in the app layer itself (stateless handlers) |
| Provider | Base44 |
| Location | Cloud (Base44-managed) |
| Retention | Transient (per request) |
| Security | TLS in transit; authenticated requests |
| Optional | — |
| Shared externally | Routed to AI providers only when you trigger an AI feature |

### 3. Database (Base44-managed)

| Field | Value |
|---|---|
| Purpose | Stores all structured user data (entities) |
| Data processed | Account info, notes, tasks, calendar events, exams, flashcards, quizzes, mind maps, focus sessions, revision sheets, study-time logs, custom agents, contact messages |
| Data stored | Structured records per the data map |
| Provider | Base44 |
| Location | Cloud (Base44-managed database) |
| Retention | Per category — see [DATA_RETENTION.md](./DATA_RETENTION.md) |
| Security | TLS in transit; encrypted at rest; **row-level security (RLS)** isolating each user's records |
| Optional | Study content is optional; account identity is required |
| Shared externally | No (except collaborators you invite to shared notes) |

### 4. Object storage (Base44-managed)

| Field | Value |
|---|---|
| Purpose | Stores uploaded files (public uploads) and private files |
| Data processed | PDFs, documents, slides, images |
| Data stored | File binaries + file metadata |
| Provider | Base44 |
| Location | Cloud (Base44-managed object storage) |
| Retention | Until you delete the file |
| Security | TLS in transit; encrypted at rest; private files served only via **signed, expiring URLs** |
| Optional | Yes |
| Shared externally | No |

### 5. Authentication (Base44 Auth)

| Field | Value |
|---|---|
| Purpose | Sign-up, login, password reset, email verification |
| Data processed | Email, password hash (managed by platform), OTP codes, session tokens |
| Data stored | Account record, session tokens |
| Provider | Base44 |
| Location | Cloud (Base44-managed) |
| Retention | Account lifetime + 30 days after deletion |
| Security | Platform-managed auth; Google OAuth supported |
| Optional | Required to use the app |
| Shared externally | No |

### 6. AI routing (Base44 Core → AI providers)

| Field | Value |
|---|---|
| Purpose | Routes your AI feature requests to an AI model provider |
| Data processed | The prompt built from your study material + your instruction |
| Data stored | Transient — Noto does not persist your AI inputs |
| Provider | AI providers (OpenAI / Google / Anthropic) via Base44 |
| Location | Provider cloud (US/EU) — TO BE VERIFIED per provider |
| Retention | Transient per request; provider-side retention TO BE VERIFIED |
| Security | TLS in transit |
| Optional | Yes — AI features are only used when you explicitly trigger them |
| Shared externally | Yes — the AI provider receives the prompt |

### 7. Analytics (Base44)

| Field | Value |
|---|---|
| Purpose | Understand aggregate product usage (anonymous events) |
| Data processed | Anonymous in-app events |
| Data stored | Raw events + aggregates |
| Provider | Base44 |
| Location | Cloud (Base44-managed) |
| Retention | Raw events up to 12 months; aggregates longer |
| Security | TLS in transit; encrypted at rest |
| Optional | Yes (you can opt out in Settings) |
| Shared externally | No |

### 8. Email (Base44 Core SendEmail)

| Field | Value |
|---|---|
| Purpose | Transactional emails (deadline reminders, account, contact-form delivery) |
| Data processed | Recipient email + message body |
| Data stored | Transient (delivery) |
| Provider | Base44 email service |
| Location | Cloud |
| Retention | Transient |
| Security | TLS in transit |
| Optional | Reminders configurable; contact form is voluntary |
| Shared externally | Only to the recipient's email provider for delivery |

### 9. Backups (Base44-managed)

| Field | Value |
|---|---|
| Purpose | Disaster recovery |
| Data processed | Database snapshots |
| Data stored | Encrypted backups |
| Provider | Base44 |
| Location | Cloud (Base44-managed backup storage) |
| Retention | Up to 30 days |
| Security | Encrypted at rest |
| Optional | Required (system) |
| Shared externally | No |
