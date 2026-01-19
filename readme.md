
---

# ☀️ Predicción de Producción Solar Basada en el Clima

## 📌 Descripción general del proyecto

Este proyecto tiene como objetivo **predecir la potencia eléctrica producida por paneles solares** utilizando datos meteorológicos como temperatura, humedad, presión atmosférica y velocidad del viento.

La predicción se realiza mediante **modelos de Machine Learning**, entrenados a partir de datos históricos reales de producción solar y condiciones climáticas. El resultado final es un sistema capaz de **estimar cuánta energía puede producir un panel solar bajo ciertas condiciones meteorológicas**, incluso en tiempo real.

Este tipo de predicción es especialmente útil para:

* Planificación energética
* Optimización de sistemas solares
* Reducción de incertidumbre en la generación renovable

---

## 📊 Datos utilizados

El dataset contiene más de **21.000 registros** provenientes de **12 ubicaciones del hemisferio norte**, recopilados durante **14 meses**.

Cada fila representa una medición real de:

* Condiciones meteorológicas
* Momento temporal
* Potencia generada por el panel solar

### Variables principales

* **Temperatura ambiente**
* **Humedad**
* **Presión atmosférica**
* **Velocidad del viento**
* **Potencia solar generada (PolyPwr)** ← variable que queremos predecir

---

## 🔍 Análisis Exploratorio de Datos (EDA)

Antes de entrenar cualquier modelo, se analizó el dataset para **entender su comportamiento**.

### ¿Qué se revisó?

* Tamaño del dataset
* Tipos de datos
* Valores faltantes
* Datos duplicados
* Distribución de la potencia solar
* Relación entre clima y producción solar

### Conclusiones clave del análisis

* La **temperatura** tiene una relación clara con la producción solar.
* La **humedad alta** suele reducir la potencia generada.
* La **presión atmosférica** muestra relación indirecta con días despejados.
* La **velocidad del viento** tiene un impacto menor, pero no nulo.
* La producción solar varía mucho según **hora del día y mes del año**.

Este análisis permitió **justificar qué variables usar y cómo tratarlas**.

---

## 🧹 Preprocesamiento de datos

Antes de entrenar modelos, los datos se prepararon cuidadosamente.

### Acciones realizadas:

* Eliminación de columnas irrelevantes (ubicación, fechas crudas, coordenadas)
* Conversión correcta de fechas y horas
* Verificación de consistencia
* Creación de nuevas variables útiles

---

## 🧠 Ingeniería de características (Feature Engineering)

Para mejorar la capacidad predictiva de los modelos, se crearon nuevas variables que capturan **relaciones más complejas**:

### Interacciones entre variables

Ejemplos:

* Temperatura × Humedad
* Temperatura × Velocidad del viento

Estas combinaciones ayudan a reflejar cómo **el clima actúa de forma conjunta**, no aislada.

### Variables no lineales

Ejemplos:

* Temperatura al cuadrado
* Humedad al cuadrado

Esto permite que los modelos capten comportamientos donde **los efectos no son proporcionales**.

---

## ✂️ División del dataset (Data Splitting)

Para evaluar correctamente los modelos, los datos se dividieron en:

* **70% entrenamiento**
* **15% validación**
* **15% test**

La división se realizó de forma **estratificada**, asegurando que todos los niveles de producción solar estuvieran bien representados en cada conjunto.

Esto evita evaluaciones engañosas y asegura resultados realistas.

---

## 🤖 Modelos entrenados

Se entrenaron y compararon **cinco modelos distintos**:

1. **Regresión Lineal**
   Modelo simple y fácil de interpretar.

2. **Support Vector Regression (SVR)**
   Modelo más complejo, pero con bajo rendimiento en este problema.

3. **Árbol de Decisión**
   Capaz de aprender reglas, pero sensible al ruido.

4. **Random Forest** ⭐
   Conjunto de árboles, muy estable y preciso.

5. **XGBoost**
   Modelo avanzado basado en boosting, con excelente rendimiento.

---

## 📈 Evaluación de modelos

Los modelos se evaluaron usando métricas claras:

* Error medio
* Error porcentual
* Capacidad para explicar la variación real de los datos

### Resultados principales

* **Random Forest** y **XGBoost** fueron los mejores modelos.
* Random Forest logró explicar **más del 94%** de la variación real de la producción solar.
* SVR mostró un rendimiento muy bajo y fue descartado.

---

## 🛠 Selección de características

Se aplicó un proceso automático para:

* Identificar las variables más importantes
* Eliminar las menos relevantes
* Reducir complejidad sin perder precisión

El modelo siguió funcionando casi igual de bien **con menos variables**, lo que demuestra que:

> No todas las variables aportan valor real al modelo.

---

## 💾 Guardado del modelo

El modelo Random Forest final se guardó en disco para poder:

* Reutilizarlo sin reentrenar
* Integrarlo en aplicaciones reales
* Usarlo para predicciones futuras

---

## 🎯 Inferencia y predicción

### Predicción sobre datos históricos

Se compararon valores reales vs predichos, observando que:

* El modelo sigue bien la tendencia real
* Existen pequeñas desviaciones normales por la variabilidad climática

### Predicción en tiempo real

El proyecto incluye un sistema que:

1. Obtiene datos meteorológicos actuales desde **OpenWeatherMap**
2. Procesa esos datos
3. Genera una predicción instantánea de potencia solar en **vatios (W)**

Esto permite estimar producción solar **en tiempo real**, solo introduciendo una ciudad.

---

## ✅ Conclusiones finales

* Es posible predecir la producción solar con **alta precisión** usando solo datos climáticos.
* La **calidad del análisis y del preprocesamiento** es tan importante como el modelo.
* Random Forest ofrece un excelente equilibrio entre:

  * Precisión
  * Estabilidad
  * Interpretabilidad
* El sistema es extensible a:

  * Predicciones horarias
  * Integración con sistemas reales
  * Optimización energética

---

