# Data Deletion

This explains exactly what happens when data is deleted in Noto.

## When a user deletes a note

1. The note is **soft-deleted** (a `deleted_at` timestamp is set).
2. The note disappears from your active lists but remains restorable from **Trash** for **30 days**.
3. After 30 days, the trash auto-purge job **permanently deletes** the note record from the database.
4. The note may remain in **backups** until backup expiry (up to 30 days).
5. **Third-party/AI:** nothing additional happens — AI inputs were never persisted. Any AI output you previously saved as part of the note is deleted with the note.
6. **Shared notes:** deletion removes the note from your collaborators' view as well.

## When a user deletes a file

1. The CloudFile record (metadata) is deleted from the database.
2. The cached extracted text stored on the record is deleted.
3. The underlying file object in Base44 object storage is deleted (whether immediately or via storage garbage-collection is **TO BE VERIFIED**).
4. If a note chapter was created from the file, that note is **not** automatically deleted — you must delete it separately.
5. Residual copies may exist in backups until expiry (up to 30 days).

## When a user deletes their account

Triggered from **Settings → Delete account**. The account-deletion function:

1. Deletes **all** your data across every entity: Tasks, Notes, CalendarEvents, MindMaps, FocusSessions, Flashcards, QuizAttempts, Exams, CloudFiles, StudyTimes, RevisionSheets, CustomAgents, and ContactMessages.
2. Attempts to remove your **User account record** (handled by the platform auth provider where the platform owns it).
3. Returns success once the active-system deletion is complete.

**What is NOT immediately erased:**
- **Backups:** residual copies may persist in encrypted backups for **up to 30 days** until backup expiry.
- **AI providers:** AI inputs were transient and not stored by Noto. Any provider-side retention is governed by the provider's policy — **TO BE VERIFIED**.
- **Analytics:** anonymous, aggregated analytics events are not directly linked to your account and are retained per the analytics schedule.

## When a user requests deletion

- You can delete your account and individual items directly in the app at any time — no need to contact us.
- For assistance or to request deletion of specific data you cannot remove yourself, contact Noto support (via the in-app Contact page).
- Deletion requests are processed in accordance with the retention periods above.

## Active-system vs. backups summary

| Layer | Behavior |
|---|---|
| Active database | Deleted immediately on user action (soft-delete then 30-day purge for notes/flashcards/quizzes) |
| Object storage | Deleted with the file record (immediate vs. garbage-collected: TO BE VERIFIED) |
| Backups | Retained encrypted for up to 30 days, then expired |
| AI providers | Not stored by Noto; provider-side retention TO BE VERIFIED |
| Analytics | Anonymous/aggregated; not deleted per-user |
