# 02. Python for Data Engineering

## 1. Descripción del Módulo
Este módulo cubre el uso de Python orientado al desarrollo de software robusto para ingeniería de datos. El enfoque va más allá del análisis exploratorio: se centra en scripts modulares, manejo defensivo de excepciones, manipulación eficiente de estructuras de datos, procesamiento de archivos de gran tamaño y automatización de pipelines.

---

## 2. Niveles de Competencia (L0 – L3)

| Nivel | Descripción | Indicador de Logro |
| :--- | :--- | :--- |
| **L0: Recordar** | Recordar sintaxis de Python, estructuras de datos nativas (`dict`, `set`, `tuple`, `list`) y manejo básico de archivos. | Responde correctamente a las preguntas de Active Recall. |
| **L1: Comprender** | Explicar iteradores, generadores, decoradores y programación orientada a objetos (POO) aplicada a pipelines. | Explica por qué un generador ahorra memoria frente a una lista al procesar datasets masivos. |
| **L2: Aplicar** | Desarrollar módulos Python limpios para ingesta/limpieza de datos con manejo de errores y tipado explícito (`typing`). | Construye un script funcional que ingiera datos de una API REST, parsee JSON y exporte a Parquet/CSV. |
| **L3: Dominar** | Refactorizar scripts deficientes, aplicar logging estructurado, unit testing (`pytest`) y profiling de memoria/CPU. | Resuelve casos de debugging de fugas de memoria y optimiza un proceso de ETL lento. |

---

## 3. Temario Detallado

### Tema 1: Fundamentos Avanzados de Lenguaje
- Tipado estático en Python (`typing`, Type Hints) y validación de datos con `Pydantic`.
- List, Dict y Set Comprenhensions eficientes.
- Manejo de excepciones personalizado y logging estructurado (`logging` module).

### Tema 2: Eficiencia de Memoria y Procesamiento
- Iteradores y Generadores (`yield`) para lectura por bloques (*streaming de archivos*).
- Manejo de archivos context managers (`with` statements) e IO buffers.
- Introducción a la concurrencia: `threading`, `multiprocessing` y `asyncio` para I/O-bound vs CPU-bound tasks.

### Tema 3: Programación Orientada a Objetos y Modularización
- Clases, Herencia y Composición para conectores de bases de datos y extractores API.
- Organización de código en paquetes y módulos reutilizables.
- Pruebas unitarias integradas (`pytest`) y entorno virtual (`venv` / `poetry`).

---

## 4. Preguntas de Active Recall

1. **¿Cuál es la diferencia técnica entre utilizar `[x for x in range(1000000)]` y `(x for x in range(1000000))` en términos de uso de memoria RAM?**
2. **¿Por qué se prefiere el módulo `logging` frente a simples llamadas a `print()` en un pipeline en producción?**
3. **¿Cuál es la diferencia entre una tarea *CPU-bound* y una *I/O-bound*, y qué módulo de Python se debe usar para acelerar cada una?**
4. **¿Cómo garantiza la palabra clave `yield` que un archivo CSV de 50 GB se pueda procesar en una máquina con solo 8 GB de RAM?**

---

## 5. Casos Prácticos y Ejercicios

### Caso Práctico: Ingesta Defensiva de API con Pagina y Rate Limit
**Escenario:** Debes extraer información de una API REST de transacciones con límite de 100 peticiones por minuto. Los datos deben ser transformados y agrupados en archivos `.parquet` diarios.

**Consigna:**
1. Diseña una clase `APIExtractor` con métodos para manejar reintentos automáticos (*exponential backoff*).
2. Utiliza un generador (`yield`) para entregar los registros página por página sin saturar la memoria.
3. Define un modelo con `Pydantic` para validar que los tipos de datos recibidos correspondan con el esquema esperado.

---

## 6. Caso de Debugging

### Problema: Out of Memory (OOM) al Procesar Log Files
**Síntoma:** El script de procesamiento de logs falla intermitentemente en producción con el error `MemoryError` al intentar procesar los logs acumulados del fin de semana (12 GB).

**Código Defectuoso:**
```python
def process_logs(file_path):
    with open(file_path, 'r') as f:
        lines = f.readlines() # <--- Carga todo el archivo a RAM
    
    cleaned_data = [line.strip().split(',') for line in lines if 'ERROR' in line]
    return cleaned_data
