# Data Export

Noto lets you download a complete archive of your data.

## How to export

1. Open the app and go to **Settings → Privacy** (the Privacy Nutrition Label / data dashboard).
2. Choose **Export my data**.
3. Noto compiles your data and downloads a **ZIP archive** to your device.

## What is included

The export contains:

- Your **profile** information (account details).
- **All your entities**, as structured JSON:
  - Notes (including content, tags, AI summary, key terms, sharing info)
  - Tasks
  - Calendar events
  - Exams
  - Mind maps (nodes)
  - Focus sessions
  - Flashcards
  - Quiz attempts
  - Revision sheets
  - Study-time logs
  - Custom AI agents
  - Cloud files (metadata)
  - Contact messages you submitted
- A machine-readable copy of the **privacy data registry** (the same categories documented in this repository).

## File binaries

Where technically possible, file binaries attached to your CloudFiles are included in the ZIP archive.

## Format

- **JSON** for structured data (one file per entity type).
- Original file formats (PDF, images, etc.) for file binaries where included.
- The archive is a standard **.zip** file, openable on any operating system.

## Notes

- Export is generated on demand and reflects your data at the moment of export.
- AI inputs (prompts) are not included because Noto does not store them.
- The export is delivered to you directly; it is not emailed to third parties.
