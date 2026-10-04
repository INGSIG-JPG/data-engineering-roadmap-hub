# Evaluación Práctica L2: Python Defensivo y Streaming

## Requisitos de Entrega
Un módulo `.py` en `02_python/practica/` con tipado estático, logging y pruebas en `pytest`.

## Desafío
Construir un script que lea un archivo CSV masivo mediante un generador (`yield`), valide los esquemas con `Pydantic` y escriba los datos válidos en Parquet en lotes de 50,000 filas.
