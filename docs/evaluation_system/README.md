# Sistema de Evaluación e Indicadores de Logro

## 1. Métrica de Evaluación por Nivel
- **L0 (Exposición):** 100% de acierto en cuestionarios de Active Recall.
- **L1 (Comprensión):** Justificación válida en diagramas de arquitectura y comparación de tecnologías.
- **L2 (Aplicación):** Código funcional que pasa pruebas unitarias (`pytest`) y ejecuta sin errores.
- **L3 (Competencia):** Resolución exitosa del caso de Debugging sin degradar la memoria ni romper el esquema.

## 2. Rúbrica de Código (L2 - L3)
1. **Modularidad:** Separación de responsabilidades en funciones/clases.
2. **Manejo de Errores:** Excepciones explícitas, logging estructurado y reintentos.
3. **Calidad:** Tipado explícito (`typing`) y estilo limpio (PEP 8).
4. **Eficiencia:** Procesamiento por bloques (*streaming/iteradores*) para evitar errores de memoria (OOM).
