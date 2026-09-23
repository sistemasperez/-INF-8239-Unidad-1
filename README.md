# Entorno profesional instalado y validado. Unidad 01. Manual laboratorios guiados.

**Asignatura:** INF-8239 Ciencia de Datos II  
**Unidad:** 01 - Modelos avanzados, reducción dimensional y Green AI  

---

## U01.LAB00 · Preparación y validación del entorno profesional
**Código:** U01.LAB00  
**Guía paso a paso:** Preparación y validación del entorno profesional.  
**Objetivo:** Instalar, preparar y validar el entorno local utilizando `uv` y pruebas automatizadas para garantizar un espacio de trabajo reproducible.

**Instrucciones de Ejecución:**
Este proyecto utiliza `uv` como gestor ultrarrápido de paquetes. Para ejecutar los notebooks o las pruebas, utiliza:
```powershell
uv run jupyter notebook
uv run pytest
```

---

## U01.LAB01 · SVM con pipeline, búsqueda de parámetros y evaluación
**Código:** U01.LAB01  
**Guía paso a paso:** SVM con pipeline, búsqueda de parámetros y evaluación.  
**Resultado Esperado:** Construirás una línea base y una SVM sin fuga; compararás C y gamma mediante validación cruzada y explicarás los errores del modelo.

---

## U01.LAB02 · Búsqueda, selección y auditoría de un dataset público
**Código:** U01.LAB02  
**Guía paso a paso:** Ensambles, PCA, t-SNE y selección Green AI.  
**Resultado Esperado:** Ampliarás el mismo problema del Ejercicio 01 con ensambles, reducción dimensional, mediciones repetidas y una decisión sobre la frontera de Pareto.

### 1. Congelar el Protocolo
* Reutiliza dataset, target, exclusiones y test del LAB02.
* No cambies la partición para favorecer un modelo.
* Declara la métrica principal y la clase prioritaria antes de comparar.
* Conserva el conjunto de prueba sin tocar hasta el cierre del experimento.
