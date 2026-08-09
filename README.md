# Learn PySpark 🚀

A hands-on collection of Jupyter notebooks for learning Apache Spark with Python (PySpark), organized as chapters like a textbook. Each chapter builds on the previous one using a common employee dataset, so you can open any notebook and follow along.

## 📖 Table of Contents

| Chapter | Notebook | What You Will Learn |
|---------|----------|---------------------|
| 1 | [Chapter 1 — Spark Introduction & DataFrame Basics](chapter1.ipynb) | Creating a `SparkSession`, building DataFrames from raw data, defining schemas (`StructType` vs DDL strings), checking partitions, `show()` / `printSchema()`, selecting columns with `col()` and `expr()`, casting types with `cast()` and `selectExpr()`, filtering with `where()`, and writing results to CSV. |
| 2 | [Chapter 2 — DataFrame Basics (Practice)](chapter2.ipynb) | A practice run of Chapter 1's concepts: schemas, column selection, expressions, type casting, filtering, and saving output — reinforcing the DataFrame fundamentals. |
| 3 | [Chapter 3 — Column Operations](chapter3.ipynb) | Adding and overwriting columns with `withColumn()`, constant columns with `lit()`, adding multiple columns at once, renaming with `withColumnRenamed()`, dropping columns with `drop()`, filtering rows, and limiting results with `limit()` and `show(n)`. |
| 4 | [Chapter 4 — Data Cleaning & Transformation](chapter4.ipynb) | Conditional logic with `when()` / `otherwise()`, string replacement with `regexp_replace()`, date parsing with `to_date()`, adding `current_date()` / `current_timestamp()`, timezone formatting with `date_format()`, handling nulls with `na.drop()` and `coalesce()`, and reshaping the final DataFrame. |
| 5 | [Chapter 5 — Combining & Aggregating Data](chapter5.ipynb) | Combining DataFrames with `union()` (alias `unionAll()`) and schema-order-safe `unionByName()`, sorting with `orderBy()` (asc/desc), aggregations with `groupBy()` + `agg()` using `sum()` / `avg()` with `alias()`, and SQL `HAVING`-style filtering on aggregated results. |
| 6 | [Chapter 6 — Distinct Data & Window Functions](chapter6.ipynb) | Removing duplicates with `distinct()`, window functions with `Window.partitionBy().orderBy()` — running `max()` over a window, finding the 2nd-highest salary per department with `row_number()`, and writing window expressions as SQL strings with `selectExpr()` and `expr()`. Bonus tip: step-by-step guide to practicing on Databricks Community Cloud (free cluster + notebook setup). |
| 7 | [Chapter 7 — Spark Architecture, Partitioning & Joins](chapter7.ipynb) | Spark architecture notes (driver, master, workers, executors, tasks, and what shuffling is), controlling partitions with `repartition(n)` / `repartition(n, col)` / `coalesce(n)` and inspecting row placement with `spark_partition_id()`, then joining `emp` with a new `dept` DataFrame: inner `join()` with qualified columns and `alias()`, plus multi-condition joins chaining `&` with `isin()` / `isNotNull()`. |
| 8 | [Chapter 8 — Reading CSV Files & Corrupt Records](chapter8.ipynb) | Reading real files with `spark.read.format("csv")`: what `header` and `inferSchema` actually cost (extra jobs), forcing a DDL schema with `.schema()` to skip them, then handling malformed data — the `mode` option (`PERMISSIVE` / `DROPMALFORMED` / `FAILFAST`), capturing raw bad lines in `_corrupt_record` and renaming it with `columnNameOfCorruptRecord`, why `FAILFAST` survives `.load()` and only blows up on an action, the `count()`-vs-`collect()` column-pruning trap, Databricks-only `badRecordsPath`, and passing several options at once with `.options(**dict)`. |

## 🛠️ Setup & Extras

| Resource | Description |
|----------|-------------|
| [docker-images/](docker-images/) | Docker Compose setup for a full Spark cluster (1 master, 2 workers, Jupyter Lab, and a history server) — see its [README](docker-images/README.md) for step-by-step instructions. |
| [csv_samples/](csv_samples/) | Sample CSV files read by the chapters — `emp.csv` (the clean employee dataset) and `emp_new.csv` (same data with deliberately broken rows: a non-numeric salary, a wrong-format date and an empty date, used for the corrupt-record lesson in Chapter 8). Mounted into the Jupyter container at `/home/jupyter/csv_samples`. |
| [jup_Note_url.txt](jup_Note_url.txt) | Quick-reference note with the local Jupyter Lab and Spark UI URLs, plus the `docker exec … jupyter server list` command for fetching the current Jupyter token after a container restart. |

## ▶️ How to Use

1. Set up a Python environment with PySpark installed (a local `.venv` works fine), or use the Docker cluster in [docker-images/](docker-images/).
2. Start Jupyter and open any chapter notebook.
3. Run the cells top to bottom — every chapter creates its own `SparkSession` and sample data, so chapters are self-contained.

---

*This index is kept in sync automatically — every new chapter notebook added to the repo gets analyzed and listed here. See [docs/readme-index-rules.md](docs/readme-index-rules.md) for the maintenance rules.*
