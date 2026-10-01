# 🗄️ 03. SQL & Relational Databases

## 📌 Competencias Objetivo
- `COMP-SQL-001`: Consultas Avanzadas, Joins y Window Functions (L3)
- `COMP-SQL-002`: Optimización de Consultas e Índices (L2)
- `COMP-SQL-003`: Modelado Relacional y Transacciones ACID (L2)

## 🗂️ Estructura
- `01_sql_basics/` — DDL, DML, DQL (`SELECT`, `WHERE`, `GROUP BY`, `HAVING`).
- `02_joins_subqueries/` — Inner, Left, Right, Full Outer, Cross Joins, CTEs.
- `03_window_functions/` — `ROW_NUMBER()`, `RANK()`, `LEAD()`, `LAG()`, agregaciones sobre ventanas.
- `04_modeling_normalization/` — 1NF, 2NF, 3NF, claves primarias y foráneas.
- `05_transactions_acid/` — `BEGIN TRANSACTION`, `COMMIT`, `ROLLBACK`, aislamientos.
- `06_indexing_optimization/` — Índices B-Tree, `EXPLAIN ANALYZE`, planes de ejecución.

## 🧠 Active Recall Benchmark
<details><summary>❓ ¿Qué diferencia a RANK() de DENSE_RANK()?</summary>

`RANK()` deja saltos en la numeración si hay empates (ej. 1, 2, 2, 4), mientras que `DENSE_RANK()` asigna rangos consecutivos sin saltar números (ej. 1, 2, 2, 3).
</details>
