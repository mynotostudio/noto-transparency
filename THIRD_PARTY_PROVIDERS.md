# Third-Party Providers

This lists every actual third-party provider that processes Noto user data. Noto does not invent providers here — only those genuinely involved are documented.

## 1. Base44 (platform)

| Field | Value |
|---|---|
| Service | Application hosting: database, object storage, authentication, backups, analytics, email, and AI request routing |
| Data processed | Account info, study content, uploaded files, usage analytics, contact messages, backups |
| Purpose | To run the Noto application |
| Location | Cloud (Base44-managed) |
| Retention | Per data category — see [DATA_RETENTION.md](./DATA_RETENTION.md) |
| Security | TLS in transit; encryption at rest; row-level security; signed file URLs |
| Documentation | https://base44.com |

## 2. OpenAI (AI provider)

| Field | Value |
|---|---|
| Service | Large language model inference (GPT-5 family) |
| Data processed | AI prompts built from your study material and instructions, for features using an OpenAI model |
| Purpose | To power AI study features |
| Location | OpenAI cloud (US/EU) — TO BE VERIFIED |
| Retention | Per OpenAI's API data policy — TO BE VERIFIED |
| Security | TLS in transit |
| Documentation | https://openai.com/enterprise-privacy / https://openai.com/policies/row-privacy-policy |

## 3. Google (AI provider + web search)

| Field | Value |
|---|---|
| Service | Large language model inference (Gemini) and web-search context |
| Data processed | AI prompts for research mode and any feature using a Gemini model |
| Purpose | To power AI study features and web-grounded research |
| Location | Google cloud — TO BE VERIFIED |
| Retention | Per Google's API/data policy — TO BE VERIFIED |
| Security | TLS in transit |
| Documentation | https://cloud.google.com/terms/data-processing-addendum |

## 4. Anthropic (AI provider)

| Field | Value |
|---|---|
| Service | Large language model inference (Claude) |
| Data processed | AI prompts for revision-sheet generation and note analysis (which use `claude_sonnet_4_6`) |
| Purpose | To power AI study features |
| Location | Anthropic cloud — TO BE VERIFIED |
| Retention | Per Anthropic's API data policy — TO BE VERIFIED |
| Security | TLS in transit |
| Documentation | https://www.anthropic.com/legal/privacy |

## 5. GitHub (only for this transparency repository)

| Field | Value |
|---|---|
| Service | Public documentation hosting |
| Data processed | The documentation files in this repository (no user data) |
| Purpose | Public transparency |
| Location | GitHub |
| Retention | Until repository is deleted |
| Security | Standard GitHub account security |
| Documentation | https://docs.github.com/site-policy/privacy-policies/github-privacy-statement |

> Note: GitHub hosts this documentation repository only. It does not receive Noto user data.

## Email delivery providers

Transactional emails (reminders, account emails, contact-form delivery) are sent through the Base44 email service. The recipient's own email provider processes the message for delivery. Noto does not directly integrate additional email providers.

## What Noto does NOT use

- No advertising or ad-tracking networks.
- No third-party analytics SDKs beyond Base44's own analytics.
- No social-media trackers.
- No data brokers.
