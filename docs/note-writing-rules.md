# Rules: How Notes Are Written in the Notebooks

Two rules decide *where* explanation goes, and one decides how it looks.

## Rule 1 — Notes sit between the code cells, never in one wall

**A reader should meet the code first, then read a short note explaining the line they just ran.**
Never stack several screens of theory above a run of code cells: by the time the reader reaches the
code they have forgotten the explanation, and while reading the theory they have nothing concrete to
attach it to.

So a teaching chapter is laid out like this:

```
[code cell]   def bonus(salary): ...
[markdown]    #### ☝️ That cell was ordinary Python - Spark knows nothing about it yet
[code cell]   bonus_udf = udf(bonus)
[markdown]    #### ☝️ That line is the registration - here is why it is needed
[code cell]   emp.withColumn("bonus", bonus_udf("salary")).show()
[markdown]    #### ☝️ What just happened - your function ran 20 times
```

- Each inline note is **short** (roughly 5–15 lines) and explains **only the cell above it**, using
  a `#### ☝️ ...` heading so it reads as a footnote to that cell, not a new topic.
- Long-form material — the mechanism, the costs, the alternatives — goes **after** the hands-on part,
  as numbered `## 📝 N.` sections, for when the code already makes sense.
- When the user has written their own code cells, **their code is not edited**. The notes are written
  to match their variable names, their data and their output.

## Rule 2 — Inside a note, the picture comes first

When a section needs a diagram, **the diagram comes first and the explanation follows it.** The
reader must be able to see the figure without scrolling while reading about it.

```
## 📝 N. <section title>

<one bold sentence defining the thing>

<THE FIGURE>

<the explanation, walking through what is in the figure>
```

- **Number the figure, then reuse those numbers.** If the figure has steps `1..7`, the prose beneath
  is a `1..7` list explaining exactly those numbers, in the same order and with the same labels.
- **One figure per idea, in the section that idea belongs to.** Two sections needing a picture of the
  same subject get two *different* figures — a numbered *sequence* ("what happens, in order") and a
  structural *map* ("which box lives on which machine") — with a one-line cross-reference each way.
  Never duplicate the same figure twice.
- **Lead the explanation by pointing at the picture** — "Now the same seven numbers, in words:",
  "What the picture is saying, line by line:" — so it is clearly a walkthrough, not a fresh start.

## Rule 3 — Separate every block with a horizontal rule

**Every markdown cell ends with a `---`**, so each code-plus-note unit is visually closed off before
the next one starts. Without it, notes and the following code run together into one grey column.

Leave a **blank line before the `---`**, otherwise markdown turns the preceding line into a heading.

## Figure drawing constraints

- **Max ~70 characters per line.** Anything wider wraps in the Jupyter/VSCode markdown renderer and
  the figure is destroyed. Prefer **vertical (stacked)** layouts over side-by-side boxes.
- **Only this character set:** `┌ ┐ └ ┘ ├ ┤ ┬ ┴ ─ │ ▼ ←` (the set chapter7's diagram already renders
  correctly in this environment). Never use `▶ ◀ ↕ ↑ ↓ × ●` or emoji inside a ```text block — they
  are not single-width in the user's font, so every box edge after them misaligns. Use ASCII `--->`,
  `<---`, `x` instead.
- **Verify before showing the user:** every line ≤ 70 chars, all box-edge lines sharing an indent
  share the same length, and no character outside the safe set.

## Code cell constraints

- **The SQL equivalent only where one exists.** The course style is `# title` → `'''SQL'''` →
  PySpark, but only when the operation genuinely translates to SQL. Declaring a UDF, printing a
  schema or calling `explain()` has no SQL form — do not invent one, and never put the SQL of a
  *different* approach there (e.g. a built-in's SQL above a pandas UDF).
- **Short `#` comments inside code cells are fine**; anything longer belongs in the note underneath.
