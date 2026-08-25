# Data Map

Each category is documented as: **What → Why → Where → Who → How long → User control**.

---

## 1. Account information

- **What:** Email address, full name, role (admin/user), country, language, reminder preferences, login days/streak data.
- **Why:** To create and manage your account, personalize the app, and send reminders.
- **Where:** Base44-managed database (cloud).
- **Who:** Base44 (processor); you.
- **How long:** Account lifetime + 30 days after account deletion.
- **User control:** Edit profile in Settings; delete account to remove.

## 2. Notes

- **What:** Note title, HTML content, notebook, tags, color, pinned state, sort order, AI summary, key terms, source type, source file URL, soft-delete timestamp, sharing lists.
- **Why:** Core note-taking feature; powers AI features and study tools.
- **Where:** Base44-managed database (cloud).
- **Who:** Base44 (processor); you; collaborators you share with (shared notes only).
- **How long:** Until you delete (trash: 30 days before permanent purge).
- **User control:** Create/edit/delete notes; restore from trash; share/unshare.

## 3. Tasks

- **What:** Title, description, status, priority, due date, category.
- **Why:** Task management and deadline reminders.
- **Where:** Base44-managed database (cloud).
- **Who:** Base44 (processor); you.
- **How long:** Until you delete.
- **User control:** Create/edit/delete; configure reminders.

## 4. Calendar events

- **What:** Title, description, location, start/end times, day-of-week (recurring) or specific date, type, color.
- **Why:** Schedule and timetable management.
- **Where:** Base44-managed database (cloud).
- **Who:** Base44 (processor); you.
- **How long:** Until you delete.
- **User control:** Create/edit/delete; import from an iCal URL.

## 5. Exams

- **What:** Title, exam date, subject, priority, notes, linked note IDs, linked flashcard IDs, linked quiz note IDs.
- **Why:** Exam preparation and AI study planning.
- **Where:** Base44-managed database (cloud).
- **Who:** Base44 (processor); you.
- **How long:** Until you delete.
- **User control:** Create/edit/delete; link notes/flashcards.

## 6. Mind maps

- **What:** Title, nodes (id, text, position, color, parent).
- **Why:** Visual study mapping.
- **Where:** Base44-managed database (cloud).
- **Who:** Base44 (processor); you.
- **How long:** Until you delete.
- **User control:** Create/edit/delete.

## 7. Focus sessions

- **What:** Duration, completion status, linked task, start time, session type (focus/short break/long break).
- **Why:** Focus timer and study-time insights.
- **Where:** Base44-managed database (cloud).
- **Who:** Base44 (processor); you.
- **How long:** Until you delete.
- **User control:** Created automatically when you complete a focus session; deletable.

## 8. Flashcards

- **What:** Note link, question, answer, card type, options, explanation, course, status, spaced-repetition fields (ease factor, interval, repetitions, next review date, review/lapse counts, last rating), soft-delete timestamp.
- **Why:** Active recall and spaced-repetition study.
- **Where:** Base44-managed database (cloud).
- **Who:** Base44 (processor); you.
- **How long:** Until you delete (trash: 30 days).
- **User control:** Create/edit/delete; review controls scheduling.

## 9. Quiz attempts

- **What:** Subject, description, note link, difficulty, total questions, correct count, full answers (question, selected, correct, correctness), soft-delete timestamp.
- **Why:** Self-assessment and adaptive difficulty.
- **Where:** Base44-managed database (cloud).
- **Who:** Base44 (processor); you.
- **How long:** Until you delete (trash: 30 days).
- **User control:** Generate/take quizzes; delete attempts.

## 10. Revision sheets

- **What:** Title, HTML content, notebook, scope.
- **Why:** AI-generated exam revision sheets.
- **Where:** Base44-managed database (cloud).
- **Who:** Base44 (processor); you.
- **How long:** Until you delete.
- **User control:** Generate/edit/delete; export to PDF.

## 11. Study-time logs

- **What:** Note link, note title, duration (seconds), start time, subject.
- **Why:** Study-time insights and streaks.
- **Where:** Base44-managed database (cloud).
- **Who:** Base44 (processor); you.
- **How long:** Until you delete.
- **User control:** Deletable; drives insights.

## 12. Custom AI agents

- **What:** Name, description, role text, persona, tone, custom instructions, data-source toggles (notes/tasks/exams/web search), icon, color.
- **Why:** Lets you build personalized AI study assistants.
- **Where:** Base44-managed database (cloud).
- **Who:** Base44 (processor); you.
- **How long:** Until you delete.
- **User control:** Create/edit/delete agents.

## 13. Uploaded files (PDFs, documents, slides, images)

- **What:** File name, type, size, folder, file URL, linked note, cached extracted text, AI chat history.
- **Why:** Document storage, AI document analysis, flashcard/quiz generation.
- **Where:** Base44-managed object storage (cloud) + metadata in database.
- **Who:** Base44 (processor); you.
- **How long:** Until you delete the file.
- **User control:** Upload/delete; cached text cleared when file deleted.

## 14. AI requests (inputs)

- **What:** The prompt assembled from your study material and your instruction when you trigger an AI feature.
- **Why:** To get an AI-generated response.
- **Where:** Transient — passed to the AI provider; **not persisted by Noto**.
- **Who:** AI provider (sub-processor).
- **How long:** Transient (provider-side retention TO BE VERIFIED).
- **User control:** AI features only run when you explicitly trigger them.

## 15. AI responses (outputs)

- **What:** The text/JSON returned by an AI provider.
- **Why:** To display results or save them as study content.
- **Where:** Not stored as "AI responses" — only what you choose to save becomes notes/flashcards/etc.
- **Who:** You (as saved study content).
- **How long:** Same as the entity you save it into.
- **User control:** Choose whether to save generated content.

## 16. Contact messages

- **What:** Name, email, message, IP address, user agent.
- **Why:** To respond to support/contact requests.
- **Where:** Base44-managed database (cloud).
- **Who:** Noto admin team.
- **How long:** Up to 12 months.
- **User control:** Submit voluntarily; request deletion.

## 17. Usage analytics

- **What:** Anonymous, aggregated in-app events (event name + minimal properties; no PII).
- **Why:** Product improvement.
- **Where:** Base44 analytics (cloud).
- **Who:** Noto team (aggregated only).
- **How long:** Raw events up to 12 months; aggregates longer.
- **User control:** Opt out in Settings.

## 18. Technical logs

- **What:** Backend function execution logs (for debugging and security auditing).
- **Why:** Operational stability and incident response.
- **Where:** Base44 platform logs.
- **Who:** Base44 / Noto admins.
- **How long:** TO BE VERIFIED (platform log retention).
- **User control:** Indirect — deleted with account data where applicable.
