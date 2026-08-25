# AI Data Processing

This documents every Noto feature that uses AI. Noto's AI requests are routed through the Base44 Core `InvokeLLM` integration to AI model providers.

## AI providers

Noto's AI requests are routed by the Base44 platform to one of these providers depending on the model selected for the feature:

- **OpenAI** (GPT-5 family models)
- **Google** (Gemini models — also used for web-search-enabled requests)
- **Anthropic** (Claude models)

> **Training & retention — TO BE VERIFIED.** Noto enables "no model training" terms in its provider agreements where available. However, whether each provider retains inputs or uses them for training is governed by that provider's current Data Processing Agreement and terms, which change over time. **Do not treat "Noto does not use your data for AI training" as a verified claim.** Verify against each provider's current terms before relying on it.

## Per-feature breakdown

### Study Assistant (chat)

- **Trigger:** You send a message in the AI assistant, or use a custom agent you built.
- **User data sent:** Your message + recent conversation history (up to 10 turns). Depending on the mode/agent: snippets of your latest notes (up to ~8 notes, ~400 chars each), your pending tasks (title, priority, due date, category), your upcoming exams (title, subject, date, priority), today's calendar events, and recent focus-session totals.
- **Provider:** AI provider (model: "automatic" by default).
- **Why:** To ground the assistant's answer in your real study material.
- **Provider retains:** TO BE VERIFIED (per provider policy).
- **Used for training:** Noto enables no-training terms; provider-side TO BE VERIFIED.
- **Processing location:** Provider cloud (US/EU) — TO BE VERIFIED.
- **User control:** Don't trigger the feature. For custom agents, toggle which data sources (notes/tasks/exams/web search) are included.

### Study Assistant — Research mode

- **Trigger:** You use the "research" assistant mode.
- **User data sent:** Your research query + web-search context. Uses `add_context_from_internet` with the **gemini_3_flash** model (Google).
- **Provider:** Google (Gemini).
- **Why:** To find and cite credible academic sources.
- **Provider retains:** TO BE VERIFIED.
- **Used for training:** TO BE VERIFIED.
- **Processing location:** Google cloud — TO BE VERIFIED.
- **User control:** Don't use research mode.

### Document analysis (chat with a document)

- **Trigger:** You ask a question about an uploaded document.
- **User data sent:** Extracted text of the document (up to ~12,000 chars, cached on the file) + your message + conversation history. If text extraction fails, the file itself is sent via `file_urls`.
- **Provider:** AI provider (model: "automatic").
- **Why:** To answer questions grounded in the document.
- **Provider retains:** TO BE VERIFIED.
- **Used for training:** TO BE VERIFIED.
- **Processing location:** Provider cloud — TO BE VERIFIED.
- **User control:** Don't use document chat; delete the file.

### Quiz generation (from a note)

- **Trigger:** You generate a quiz from a note.
- **User data sent:** Note text (HTML stripped, up to ~12,000 chars) + existing flashcards for that note (Q/A pairs) + chosen difficulty.
- **Provider:** AI provider (model: "automatic").
- **Why:** To create multiple-choice practice questions.
- **Provider retains:** TO BE VERIFIED.
- **Used for training:** TO BE VERIFIED.
- **Processing location:** Provider cloud — TO BE VERIFIED.
- **User control:** Don't generate quizzes.

### Quiz generation (from a document)

- **Trigger:** You generate a quiz from an uploaded document.
- **User data sent:** Extracted document text (up to ~12,000 chars) + chosen difficulty.
- **Provider:** AI provider (model: "automatic").
- **Why:** To create multiple-choice practice questions from the document.
- **Provider retains:** TO BE VERIFIED.
- **Used for training:** TO BE VERIFIED.
- **Processing location:** Provider cloud — TO BE VERIFIED.
- **User control:** Don't generate quizzes; delete the file.

### Flashcard generation (from a document)

- **Trigger:** You generate flashcards from an uploaded document.
- **User data sent:** Extracted document text (up to ~14,000 chars), or the file itself if no text was extracted. Generated cards are saved as Flashcards linked to a new Note chapter.
- **Provider:** AI provider (model: "automatic").
- **Why:** To build a spaced-repetition deck from the document.
- **Provider retains:** TO BE VERIFIED.
- **Used for training:** TO BE VERIFIED.
- **Processing location:** Provider cloud — TO BE VERIFIED.
- **User control:** Don't generate flashcards; delete generated cards.

### Revision sheet generation

- **Trigger:** You generate a revision sheet from one or more notes.
- **User data sent:** The selected notes' content (up to ~20,000 chars each) + sheet title + scope. Uses the **claude_sonnet_4_6** model (Anthropic).
- **Provider:** Anthropic (Claude).
- **Why:** To produce a structured exam revision sheet.
- **Provider retains:** TO BE VERIFIED.
- **Used for training:** TO BE VERIFIED.
- **Processing location:** Anthropic cloud — TO BE VERIFIED.
- **User control:** Don't generate revision sheets; delete generated sheets.

### Explain It Back (Feynman recall check)

- **Trigger:** You submit your own explanation of a concept from a note.
- **User data sent:** The reference note text (up to ~12,000 chars) + your typed explanation + optional concept list + your language.
- **Provider:** AI provider (model: "automatic").
- **Why:** To score how completely you covered the note's concepts.
- **Provider retains:** TO BE VERIFIED.
- **Used for training:** TO BE VERIFIED.
- **Processing location:** Provider cloud — TO BE VERIFIED.
- **User control:** Don't use the feature.

### Concept extraction

- **Trigger:** You extract key concepts from a note.
- **User data sent:** The note text (HTML stripped, up to ~12,000 chars) + your language.
- **Provider:** AI provider (model: "automatic").
- **Why:** To list the concepts you should be able to explain.
- **Provider retains:** TO BE VERIFIED.
- **Used for training:** TO BE VERIFIED.
- **Processing location:** Provider cloud — TO BE VERIFIED.
- **User control:** Don't use the feature.

### Note analysis (summary, key terms, tags, flashcards)

- **Trigger:** You analyze a note to generate a TL;DR, key terms, tags, and flashcards.
- **User data sent:** The note text (up to ~12,000 chars) + your language. Uses the **claude_sonnet_4_6** model (Anthropic). Results (summary, key terms, merged tags) are saved back onto the note.
- **Provider:** Anthropic (Claude).
- **Why:** To enrich the note with study aids.
- **Provider retains:** TO BE VERIFIED.
- **Used for training:** TO BE VERIFIED.
- **Processing location:** Anthropic cloud — TO BE VERIFIED.
- **User control:** Don't analyze notes; clear AI-generated summary/terms by editing the note.

### Auto-classify notes

- **Trigger:** You run note auto-organization.
- **User data sent:** For up to 40 notes: note ID, title, current notebook, and a ~200-char content snippet. Existing notebook names are included for reuse.
- **Provider:** AI provider (model: "automatic").
- **Why:** To organize notes into notebooks and a hierarchy.
- **Provider retains:** TO BE VERIFIED.
- **Used for training:** TO BE VERIFIED.
- **Processing location:** Provider cloud — TO BE VERIFIED.
- **User control:** Don't run auto-classify; reorganize manually.

## Features that are NOT AI

The following Noto features do **not** send data to an AI provider:

- **Flashcard review (spaced repetition):** Uses the SM-2 algorithm locally on stored card data — no AI call.
- **Cloud file categorization:** Uses local keyword rules — no AI call.
- **Trash auto-purge, deadline reminders, contact-form email, calendar URL import, note sharing, account deletion:** No AI processing.

## General AI controls

- AI features only run when you explicitly trigger them.
- Noto does not persist your AI inputs (prompts) — only outputs you choose to save become normal study content.
- You can avoid all AI processing by not using AI features.
