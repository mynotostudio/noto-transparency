# Data Retention

This documents how long each category of data is retained and what happens after deletion.

## Active data

| Category | Retention |
|---|---|
| Account information | Account lifetime + 30 days after account deletion |
| Notes | Until you delete; soft-deleted items purged after 30 days |
| Tasks | Until you delete |
| Calendar events | Until you delete |
| Exams | Until you delete |
| Mind maps | Until you delete |
| Focus sessions | Until you delete |
| Flashcards | Until you delete; soft-deleted items purged after 30 days |
| Quiz attempts | Until you delete; soft-deleted items purged after 30 days |
| Revision sheets | Until you delete |
| Study-time logs | Until you delete |
| Custom AI agents | Until you delete |
| Uploaded files | Until you delete the file |
| Cached document text | Stored on the CloudFile; cleared when the file is deleted |
| Contact messages | Up to 12 months |
| Usage analytics (raw events) | Up to 12 months |
| Usage analytics (aggregates) | Longer than raw events (indefinite aggregates) |

## AI processing data

- Noto does **not** persist the prompts (AI inputs) you send to AI providers.
- AI outputs you choose to save become normal study content and follow that content's retention.
- Provider-side retention of AI inputs is **TO BE VERIFIED** per provider policy.

## Backups

- Automated, encrypted backups are retained for **up to 30 days**.
- Backups are managed by Base44.
- When you delete data, it may remain in backups until the backup expires (up to 30 days).

## Technical logs

- Backend function execution logs are retained by the Base44 platform.
- Exact retention: **TO BE VERIFIED** (platform log retention policy).

## After deletion

- **Soft-deleted items** (notes, flashcards, quiz attempts): remain restorable for 30 days, then permanently purged by the trash auto-purge job.
- **Account deletion:** all your entities are deleted from the active database immediately; the account record is removed (best-effort) by the platform auth provider. Residual copies may exist in backups until backup expiry (up to 30 days).
- **Files:** the CloudFile record and cached text are deleted; the underlying object in storage is deleted via the platform. Whether object-storage deletion is immediate or garbage-collected is **TO BE VERIFIED**.
