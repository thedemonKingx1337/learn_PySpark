# Rule: Keep the README Index in Sync

The root [README.md](../README.md) is the index page of this PySpark course, like the table of contents of a textbook. It must always list every chapter with a link and a short description so anyone browsing on GitHub can jump straight to the topic they want to learn.

Whenever a new learning file is added to this repo (e.g. `chapter7.ipynb`, or any new notebook/script/folder meant for learning), or an existing chapter's content changes significantly, update the Table of Contents in README.md:

1. **Analyze the file's content** — read the notebook's cells (markdown headings, imports, functions used, comments) and identify the actual PySpark concepts it teaches. Do not guess from the filename alone.
2. **Give the chapter a descriptive title** — a short topic name like "Data Cleaning & Transformation", not just "Chapter 7".
3. **Write a one-row summary** — list the key functions/concepts covered (e.g. `groupBy()`, `join()`, window functions) in one or two sentences, matching the style of the existing rows.
4. **Add or update the row in the Table of Contents table** in README.md, keeping chapters in numerical order with a working relative link to the file.
5. **Mark unfinished chapters** — if a notebook only has setup cells or is clearly incomplete, label it 🚧 "Work in Progress" and update the row later once real content lands.
6. **Non-chapter resources** (Docker setups, data folders, helper scripts, notes) go in the "Setup & Extras" table instead, with a link and one-line description.

Do this proactively: if you notice during any task that a chapter file exists but is missing from (or stale in) the README index, fix the index as part of your work and mention it to the user.

**Custom command**: When the user types `/update-readme`, run the full sync described above — the command definition lives in [.claude/commands/update-readme.md](../.claude/commands/update-readme.md).
