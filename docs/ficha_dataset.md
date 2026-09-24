# Ficha del dataset : Impacto de la IA en los Estudiantes
- Dominio: Educación y Bienestar Estudiantil
- Unidad de análisis: Estudiantes
- Decisión: Implementar IA para mejorar el bienestar estudiantil
- Target: Nivel de riesgo de agotamiento o Burnout (Burnout_Risk_Level).
- Error más costoso: Falso negativo (no detectar un estudiante en riesgo de burnout).
- Usuario: Decisores institucionales, consejeros académicos y estudiantes.


# 2. Procedencia y Licencia (Requerido en el Paso 2 y 11)

Fuente: Kaggle.

URL de descarga: https://www.kaggle.com/api/v1/datasets/download/laveshjadon/ai-impact-on-students

Licencia: [CC0: Public Domain - Uso público y académico permitido]

Tamaño: 50,000 filas y 16 columnas (Apto para procesar en Google Colab/CPU gratuita).

# 3. Diccionario de Datos 
* **Columna:** `Burnout_Risk_Level`
  * **Significado:** Nivel evaluado de riesgo de agotamiento o cansancio extremo del estudiante.
  * **Unidad:** Categórica (Low, Medium, High).
  * **Fuente:** Kaggle (Lavesh Jadon).
  * **Momento de disponibilidad:** Al finalizar la evaluación del semestre.
  * **Transformación prevista:** Ninguna. Se separará como la variable objetivo (`y`).
  * **Riesgo:** Es el Target, no debe incluirse en los datos de entrenamiento (`X`).

* **Columna:** `Student_ID`
  * **Significado:** Identificador numérico único asignado a cada estudiante.
  * **Unidad:** Número entero.
  * **Fuente:** Kaggle (Lavesh Jadon).
  * **Momento de disponibilidad:** Al momento de la inscripción.
  * **Transformación prevista:** Eliminar (`drop`).
  * **Riesgo:** Riesgo de sobreajuste. Al ser un ID, no aporta valor predictivo y la IA podría intentar memorizar los números de los estudiantes en lugar de aprender patrones reales.

* **Columna:** `Weekly_GenAI_Hours`
  * **Significado:** Promedio de horas por semana que el estudiante pasa usando herramientas de IA generativa.
  * **Unidad:** Horas (Numérica, Flotante / Decimal).
  * **Fuente:** Kaggle (Lavesh Jadon).
  * **Momento de disponibilidad:** Durante el transcurso del semestre.
  * **Transformación prevista:** Estandarización matemática (`StandardScaler`).
  * **Riesgo:** Ninguno.

* **Columna:** `Primary_Use_Case`
  * **Significado:** Propósito principal para el cual el estudiante usa la IA (ej. Resumir lecturas, Depurar código, Redactar).
  * **Unidad:** Categórica (Texto).
  * **Fuente:** Kaggle (Lavesh Jadon).
  * **Momento de disponibilidad:** Durante el transcurso del semestre.
  * **Transformación prevista:** Codificación binaria (`OneHotEncoder`).
  * **Riesgo:** Ninguno.

* **Columna:** `Perceived_AI_Dependency`
  * **Significado:** Nivel de dependencia hacia la IA que siente el propio estudiante (en una escala del 1 al 10).
  * **Unidad:** Numérica (Entero).
  * **Fuente:** Kaggle (Lavesh Jadon).
  * **Momento de disponibilidad:** Durante el transcurso del semestre (vía encuesta/evaluación).
  * **Transformación prevista:** Estandarización matemática (`StandardScaler`).
  * **Riesgo:** Ninguno. Es un fuerte indicador de comportamiento.

* **Columna:** `Traditional_Study_Hours`
  * **Significado:** Horas semanales dedicadas a estudiar de forma tradicional (sin usar herramientas de IA).
  * **Unidad:** Horas (Numérica, Flotante / Decimal).
  * **Fuente:** Kaggle (Lavesh Jadon).
  * **Momento de disponibilidad:** Durante el transcurso del semestre.
  * **Transformación prevista:** Estandarización matemática (`StandardScaler`).
  * **Riesgo:** Ninguno.

* **Columna:** `Post_Semester_GPA`
  * **Significado:** Calificación o Índice Académico (GPA) obtenido al final del semestre.
  * **Unidad:** Puntuación decimal (1.0 - 4.0).
  * **Fuente:** Kaggle (Lavesh Jadon).
  * **Momento de disponibilidad:** ¡Después de que el semestre termine!
  * **Transformación prevista:** Eliminar (`drop`).
  * **Riesgo:** **ALTA FUGA DE DATOS (Data Leakage).** Como nuestro objetivo es tomar una decisión anticipada (ayudar al estudiante antes de que colapse), no podemos usar sus notas de final de semestre porque en el mundo real, en el momento de tomar la decisión, esa nota aún no existe.
