# Repository Layout & Conventions

## Layout

- `chapterN.ipynb` — one notebook per chapter; each is self-contained (creates its own `SparkSession` and sample employee data).
- `docker-images/` — Docker Compose setup for a local Spark cluster with Jupyter Lab (see its own README).
- `jup_Note_url.txt` — local URLs for Jupyter (`localhost:8888`) and the Spark UI (`localhost:4040`).
- `docs/` — instructions and rules for LLMs working in this repo (linked from `CLAUDE.md`).
- `.venv/` — local Python virtual environment; never index or modify it.

## Conventions

### Code style: SQL first, then PySpark

Every new concept in a notebook cell is written as the SQL query first, then the equivalent PySpark code — readers coming from SQL understand the operation instantly. Follow this format whenever writing or editing notebook code:

```python
# how to see the DISTINCT values of a dataframe
'''SELECT DISTINCT * FROM emp'''
emp_unique = emp.distinct()
emp_unique.show()
```

Pattern: a short `#` comment naming the concept, a `'''...'''` string with the SQL equivalent, then the PySpark code. If an operation has no SQL equivalent (e.g. `printSchema()`), the SQL line can be skipped.

### General

- Notebooks run against a local Spark (`master("local[*]")`) or the Docker cluster.
- The chapters follow the sequence of a beginner-to-advanced PySpark course; new chapters continue the numbering.
- Keep README descriptions beginner-friendly: name the PySpark functions taught, since readers use the index to find where a specific function is covered.
