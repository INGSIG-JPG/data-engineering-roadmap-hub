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

SQL
├── teoría
├── ejemplos
├── ejercicios
├── Active Recall
├── casos
├── debugging
├── evaluación
├── repaso espaciado
├── competencia
└── evidencia
```markdown
# 03. SQL & Database Systems for Data Engineering

## 1. Descripción del Módulo
Las bases de datos relacionales y no relacionales son el corazón del almacenamiento transaccional y analítico. Este módulo domina SQL desde la consulta avanzada hasta el modelado dimensional, optimización de índices, planes de ejecución (`EXPLAIN`), procedimientos de migración y diseño de esquemas (Star Schema, Snowflake Schema).

---

## 2. Niveles de Competencia (L0 – L3)

| Nivel | Descripción | Indicador de Logro |
| :--- | :--- | :--- |
| **L0: Recordar** | Comprender la sintaxis ANSI SQL, orden de ejecución de consultas (`FROM` -> `WHERE` -> `GROUP BY` -> `HAVING` -> `SELECT`). | Responde a las preguntas de Active Recall sobre orden lógico de cláusulas. |
| **L1: Comprender** | Explicar diferencias entre índices B-Tree, Hash y Vectoriales; entender estrategias de Join (Hash Join, Nested Loop, Merge Join). | Analiza un plan de ejecución (`EXPLAIN ANALYZE`) e identifica un Sequential Scan innecesario. |
| **L2: Aplicar** | Escribir consultas analíticas complejas con Window Functions, CTEs recursivas, agregaciones avanzadas y DDL de esquemas dimensionales. | Construye una consulta que calcule ingresos acumulados y promedios móviles (*moving averages*) de 7 días. |
| **L3: Dominar** | Diseñar esquemas relacionales/analíticos escalables, optimizar consultas lentas y administrar bloqueos/transacciones en entornos de producción. | Rediseña un modelo de base de datos OLTP a un modelo Copo de Nieve (Snowflake) optimizando el rendimiento de lectura. |

---

## 3. Temario Detallado

### Tema 1: SQL Avanzado y Funciones Analíticas
- Orden de ejecución lógico de consultas SQL.
- Window Functions (`ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`, `LEAD()`, `LAG()`, `SUM() OVER()`).
- CTEs (Common Table Expressions) simples y recursivas vs Subconsultas vs Tablas Temporales.

### Tema 2: Modelado de Datos
- Normalización (1NF, 2NF, 3NF) para OLTP.
- Modelado Dimensional (Kimball): Tablas de Hechos (*Fact Tables*) y Tablas de Dimensiones (*Dimension Tables*).
- Manejo de Cambios Lentos en Dimensiones (SCD Type 1, Type 2, Type 3).

### Tema 3: Optimización y Motor de Base de Datos
- Índices: Estrategias de indexación (B-Tree, Bitmap, Clustered vs Non-Clustered).
- Análisis de planes de ejecución (`EXPLAIN ANALYZE`).
- Transacciones (ACID), niveles de aislamiento y manejo de bloqueos (*Deadlocks*).

---

## 4. Preguntas de Active Recall

1. **¿En qué orden lógico procesa el motor de SQL las siguientes cláusulas: `SELECT`, `WHERE`, `FROM`, `HAVING`, `GROUP BY`?**
2. **¿Cuál es la diferencia fundamental entre `RANK()` y `DENSE_RANK()` cuando existen valores duplicados en el ordenamiento?**
3. **¿Qué problema resuelve implementar SCD Tipo 2 (Slowly Changing Dimension Type 2) en un Data Warehouse?**
4. **Si ejecutas un `EXPLAIN` y ves un `Seq Scan` en una tabla de 50 millones de filas, ¿qué solución inmediata debes evaluar?**

---

## 5. Casos Prácticos y Ejercicios

### Caso Práctico: Cálculo de Retención de Usuarios mediante Window Functions
**Escenario:** Una plataforma de e-commerce desea calcular la recurrencia de compras de sus usuarios para determinar qué porcentaje realiza una segunda compra en menos de 30 días.

**Consigna:**
Escribe una consulta SQL utilizando `LAG()` o `LEAD()` que obtenga:
1. ID de cliente.
2. Fecha de la compra actual.
3. Fecha de la compra anterior.
4. Días transcurridos entre ambas compras.

---

## 6. Caso de Debugging

### Problema: Cuello de Botella por Subconsulta Correlacionada
**Síntoma:** El reporte mensual de ventas tarda 45 minutos en ejecutarse y satura el uso de CPU del servidor de base de datos.

**Consulta Lenta:**
```sql
SELECT 
    e.employee_id,
    e.department_id,
    e.salary,
    (SELECT AVG(salary) 
     FROM employees e2 
     WHERE e2.department_id = e.department_id) AS dept_avg_salary
FROM employees e;
