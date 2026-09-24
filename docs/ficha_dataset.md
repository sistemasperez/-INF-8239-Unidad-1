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

* **Columna:** `Major_Category`
  * **Significado:** Campo de estudio o facultad del estudiante (STEM, Negocios, Humanidades, Medicina, Artes).
  * **Unidad:** Categórica (Texto).
  * **Momento de disponibilidad:** Al inicio del semestre.
  * **Transformación prevista:** Codificación binaria (`OneHotEncoder`).
  * **Riesgo:** Ninguno.

* **Columna:** `Year_of_Study`
  * **Significado:** Nivel académico actual del estudiante (Freshman, Sophomore, Junior, Senior, Graduate).
  * **Unidad:** Categórica (Texto).
  * **Momento de disponibilidad:** Al inicio del semestre.
  * **Transformación prevista:** Codificación binaria (`OneHotEncoder`).
  * **Riesgo:** Ninguno.

* **Columna:** `Pre_Semester_GPA`
  * **Significado:** Índice académico (GPA) acumulado que tenía el estudiante antes de empezar el semestre.
  * **Unidad:** Numérica (Decimal / Float).
  * **Momento de disponibilidad:** Al inicio del semestre.
  * **Transformación prevista:** Estandarización matemática (`StandardScaler`).
  * **Riesgo:** Ninguno. Es un dato histórico válido para predecir el futuro.

* **Columna:** `Prompt_Engineering_Skill`
  * **Significado:** Autoevaluación de la habilidad del estudiante para crear prompts efectivos (Beginner, Intermediate, Advanced).
  * **Unidad:** Categórica (Texto).
  * **Momento de disponibilidad:** Durante el transcurso del semestre (vía encuesta).
  * **Transformación prevista:** Codificación binaria (`OneHotEncoder`).
  * **Riesgo:** Ninguno.

* **Columna:** `Tool_Diversity`
  * **Significado:** Cantidad de herramientas de IA diferentes que utiliza el estudiante (ej. ChatGPT, Claude, Midjourney).
  * **Unidad:** Numérica (Entero, 1 a 5).
  * **Momento de disponibilidad:** Durante el transcurso del semestre.
  * **Transformación prevista:** Estandarización matemática (`StandardScaler`).
  * **Riesgo:** Ninguno.

* **Columna:** `Paid_Subscription`
  * **Significado:** Indica si el estudiante paga una suscripción premium por alguna herramienta de IA.
  * **Unidad:** Booleana (True / False).
  * **Momento de disponibilidad:** Durante el transcurso del semestre.
  * **Transformación prevista:** El pipeline lo detectará como categoría y le aplicará `OneHotEncoder`.
  * **Riesgo:** Ninguno.

* **Columna:** `Institutional_Policy`
  * **Significado:** Postura oficial de la universidad frente al uso de IA (Permitido con cita, Prohibido estrictamente, Fomentado activamente).
  * **Unidad:** Categórica (Texto).
  * **Momento de disponibilidad:** Al inicio del semestre (política pública de la institución).
  * **Transformación prevista:** Codificación binaria (`OneHotEncoder`).
  * **Riesgo:** Ninguno.

* **Columna:** `Anxiety_Level_During_Exams`
  * **Significado:** Nivel de ansiedad reportado por el estudiante durante evaluaciones.
  * **Unidad:** Numérica (Entero, escala del 1 al 10).
  * **Momento de disponibilidad:** Durante el transcurso del semestre (evaluación psicológica de rutina).
  * **Transformación prevista:** Estandarización matemática (`StandardScaler`).
  * **Riesgo:** Ninguno, asumiendo que esta métrica evalúa la tendencia general a la ansiedad del estudiante y no se mide exclusivamente en los exámenes finales.

* **Columna:** `Skill_Retention_Score`
  * **Significado:** Puntuación que mide qué tan bien los estudiantes retuvieron las habilidades aprendidas después de terminar el semestre.
  * **Unidad:** Numérica (Decimal / Float, 0 a 100).
  * **Momento de disponibilidad:** ¡Después de que el semestre termine!
  * **Transformación prevista:** Eliminar (`drop`).
  * **Riesgo:** **ALTA FUGA DE DATOS (Data Leakage).** Al igual que Post_Semester_GPA, esta puntuación solo se conoce cuando el semestre ya acabó. Incluirla le daría al modelo información del futuro, invalidando cualquier predicción preventiva de burnout. Debe añadirse a tu lista de DROP_COLUMNS en el código.


