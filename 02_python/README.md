# 🐍 02. Python for Data Engineering

## 📌 Competencias Objetivo
- `COMP-PY-001`: Programación Orientada a Objetos y Estructuras de Datos (L3)
- `COMP-PY-002`: Manejo de Entornos, Paquetes y Modularity (L3)
- `COMP-PY-003`: Testing Unitario con `pytest` y Validación con `Pydantic` (L2)

## 🗂️ Estructura
- `01_python_basics/` — Sintaxis, tipos de datos, control de flujo.
- `02_data_structures/` — Listas, diccionarios, sets, tuplas, iteradores, generadores.
- `03_oop/` — Clases, herencia, polimorfismo, encapsulamiento.
- `04_virtual_environments/` — `venv`, `poetry`, `conda`.
- `05_data_validation_pydantic/` — Schemas, dataclasses, validación de inputs.
- `06_testing_pytest/` — Unit testing, fixtures, mocks.

## 🧠 Active Recall Benchmark
<details><summary>❓ ¿Por qué se prefiere un Generador (`yield`) sobre una Lista para procesar archivos masivos?</summary>

Un generador evalúa los elementos bajo demanda (*lazy evaluation*), manteniendo solo un elemento en memoria a la vez ($O(1)$ espacio), mientras que una lista carga todo el conjunto de datos en RAM ($O(N)$ espacio), lo cual colapsa el sistema con archivos grandes.
</details>
