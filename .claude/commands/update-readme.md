---
description: Analyze all chapter notebooks and sync the README.md Table of Contents
---

Refresh the textbook-style index in README.md so it matches the actual content of the repository. Follow the rules in docs/readme-index-rules.md. Steps:

1. **Discover chapters**: List every `chapterN.ipynb` in the repo root (and any other learning notebooks/scripts/folders that exist).
2. **Analyze each one**: Open the notebook and read its cells — markdown headings, imports, PySpark functions used, and comments — to determine the concepts it actually teaches. Never describe a chapter from its filename alone.
3. **Compare with README.md**:
   - Add a Table of Contents row for any chapter that is missing, in numerical order, with a working relative link.
   - Rewrite the title/summary of any row that no longer matches the notebook's content (e.g. a 🚧 Work in Progress chapter that now has real content).
   - Mark notebooks that only contain setup cells as 🚧 "Work in Progress".
   - Put non-chapter resources (Docker setups, data folders, helper scripts, notes) in the "Setup & Extras" table instead.
4. **Keep the style consistent**: descriptive topic titles (like a textbook chapter name) and one-to-two-sentence summaries naming the key PySpark functions covered, matching the existing rows.
5. **Report**: After editing, tell the user exactly which rows were added, updated, or left unchanged.

Do not commit unless the user asks.
