# 01. Foundations of Data Engineering

## 1. Descripción del Módulo
Este módulo establece los cimientos teóricos y prácticos de la ingeniería de datos. Su objetivo es entender qué es un pipeline de datos, cómo se diferencia de la ciencia/análisis de datos, los componentes de la arquitectura moderna de datos (Modern Data Stack) y los principios de diseño de sistemas distribuidos y almacenamiento.

---

## 2. Niveles de Competencia (L0 – L3)

| Nivel | Descripción | Indicador de Logro |
| :--- | :--- | :--- |
| **L0: Recordar** | Definir conceptos clave de Data Engineering (ETL vs ELT, OLTP vs OLAP, CAP Theorem). | Responde correctamente al Active Recall sin consultar notas. |
| **L1: Comprender** | Explicar diferencias arquitectónicas y justificar la elección de herramientas. | Diseña un diagrama de flujo comparando un pipeline batch vs streaming. |
| **L2: Aplicar** | Configurar y ejecutar un pipeline simple de extremo a extremo en entorno local. | Crea un script que ingiera datos, valide esquema y guarde en almacenamiento columnar. |
| **L3: Dominar** | Diagnosticar fallos, optimizar el pipeline y aplicar mejores prácticas de gobernanza/seguridad. | Resuelve casos de debugging (fallos de esquema, cuellos de botella) y documenta la solución. |

---

## 3. Temario Detallado

### Tema 1: Introducción a la Ingeniería de Datos
- Roles en el ecosistema de datos: Data Engineer vs Data Scientist vs Data Analyst.
- El ciclo de vida de los datos: Ingesta, Almacenamiento, Procesamiento, Modelado y Consumo.
- ETL (Extract, Transform, Load) vs ELT (Extract, Load, Transform).

### Tema 2: Arquitectura de Almacenamiento
- OLTP (Online Transaction Processing) vs OLAP (Online Analytical Processing).
- Formatos de almacenamiento de archivos: CSV, JSON, Parquet, Avro, ORC.
- Filas vs Columnas: Por qué el almacenamiento columnar es ideal para analítica.

### Tema 3: Diseños de Sistemas y Paradigmas de Procesamiento
- Procesamiento en Lote (Batch) vs Procesamiento en Tiempo Real (Streaming).
- Teorema CAP (Consistencia, Disponibilidad, Tolerancia al Particionamiento).
- Principios de Idempotencia en pipelines de datos.

---

## 4. Preguntas de Active Recall

> **Instrucciones:** Responde a estas preguntas mentalmente o por escrito ANTES de revisar la teoría.

1. **¿Cuál es la principal diferencia funcional entre un enfoque ETL y un enfoque ELT?**
2. **¿Por qué el formato Parquet es sustancialmente más eficiente que CSV/JSON para consultas analíticas agregadas (p. ej. `SUM`, `AVG`)?**
3. **¿Qué significa que una tarea de ingesta de datos sea *idempotente* y por qué es vital en producción?**
4. **En el Teorema CAP, ¿por qué un sistema distribuido debe elegir entre Consistencia (C) o Disponibilidad (A) en presencia de una Partición de red (P)?**

---

## 5. Casos Prácticos y Ejercicios

### Caso Práctico 1: Evaluación de Ingesta Financiera
**Escenario:** Una entidad procesa 50 millones de transacciones diarias. La aplicación transaccional corre sobre PostgreSQL (OLTP). El equipo de BI necesita generar reportes diarios de balance sin impactar el rendimiento de la base de datos de producción.

**Consigna:**
1. Determina si el enfoque debe ser ETL o ELT y justifica tu respuesta.
2. Diseña la arquitectura conceptual simplificada de la solución.
3. Especifica qué formato de archivo de destino utilizarías para la capa de almacenamiento analítico.

---

## 6. Caso de Debugging

### Problema: Corrupción de Esquema en Ingesta Batch
**Síntoma:** El pipeline diario falla durante la carga de un archivo `.json` porque uno de los campos de fecha cambió de formato (`YYYY-MM-DD` a `Unix Timestamp`), ocasionando la caída de la tarea de agregación.

**Tarea de Diagnóstico:**
1. Identifica en qué punto del ciclo de vida debió capturarse esta anomalía.
2. Escribe una estrategia defensiva (mecanismo de validación de esquema o *Schema Enforcement*) para evitar que datos corruptos lleguen a la capa analítica final.

---

## 7. Mapeo de Cursos y Competencias relacionadas

| Curso Origen | Módulo del Curso | Competencia Asociada | Código de Evidencia |
| :--- | :--- | :--- | :--- |
| **Coursera IBM DE** | Course 1: Introduction to Data Engineering | DE-FOUND-01: Ciclo de vida y arquitecturas | `EVID-FOUND-001` |
| **DataTalksClub DE** | Module 1: Containerization and Infrastructure | DE-FOUND-02: Entornos e ingesta básica | `EVID-FOUND-002` |

---

## 8. Evaluación del Módulo y Repaso Espaciado

- [ ] **Quiz de Verificación (Active Recall 100%):** Completado el `[ AAAA-MM-DD ]`
- [ ] **Caso Práctico Resuelto:** Código/Doc subido a `01_foundations/practica/`
- [ ] **Próximo Repaso Espaciado (Anki / Review):**
  - Repaso 1 (a los 3 días): `[ AAAA-MM-DD ]`
  - Repaso 2 (a los 7 días): `[ AAAA-MM-DD ]`
  - Repaso 3 (a los 30 días): `[ AAAA-MM-DD ]`
