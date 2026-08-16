# Learn PySpark — Guide for Claude

This repository is a personal PySpark learning course made of Jupyter notebooks named `chapterN.ipynb`. The root [README.md](README.md) is the course index page — a textbook-style table of contents.

All detailed instructions live in the [docs/](docs/) folder. Read the relevant doc before acting:

| Doc | When to read it |
|-----|-----------------|
| [docs/readme-index-rules.md](docs/readme-index-rules.md) | **Always follow this rule.** Whenever a chapter/learning file is added or significantly changed, or the user types `/update-readme` — analyze the file and sync the README Table of Contents. |
| [docs/note-writing-rules.md](docs/note-writing-rules.md) | **Always follow these rules.** Before writing or editing any explanatory note in a notebook — notes go *between* the code cells (code first, short note under it), figures go *above* the prose that explains them, every markdown cell ends with a `---`, plus the ASCII figure and SQL-docstring constraints. |
| [docs/repository-guide.md](docs/repository-guide.md) | Before exploring or modifying the repo — layout, conventions, and what to leave alone (e.g. `.venv/`). |

When a new instruction/rule for Claude is needed in the future, add it as a new file in [docs/](docs/) and list it in the table above — keep this file a short index, not a rulebook.
