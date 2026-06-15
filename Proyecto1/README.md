# Titulo del Proyecto: Análisis de Salud Mental en Adolecentes por uso de Social Media

## Descripción del problema: 
Este proyecto busca analizar algunos factores asociados a la salud mental en adolecentes que considera el uso diario de estas redes sociales, las horas de sueño, la actividad física, el rendimiento académico, los niveles de estrés, tambien los niveles ansiedad y de adicción.

## Descripción del Dataset:
El dataset utilizado corresponde a `Teen_Mental_Health_Dataset.csv`, sacado desde https://www.kaggle.com/datasets/sunil123kumar/social-media-impact-on-mental-health compuesto por más de 1000 registros y 13 variables. Que tiene información relacionada con la salud mental de adolescentes y diversos factores que pueden influir en ella. 

## Justificación del modelo(s) seleccionado.
Se utilizaron los siguientes modelos:

### Modelo 1: Regresión Logistica
Se ocupa la Regresión Logica ya que el problema corresponde a un clasificación binaria. La variable que ocuparé en esta sección es depression_label, la cual indica si existen o no indicadores de depresión en adolescentes.

### Modelo 2: Random Forest
Se ocupa Random Forest debido a que es un algoritmo de clasificación basado en múltiples árboles de decisión, capaz de capturar relaciones complejas entre las variables y reducir el riesgo de la combinación de múltiples predicciones.

### Modelo 3: Naive Bayes
Se ocupa Naive Bayes debido a que es un modelo de clasificación basado en el Teorema de Bayes. Este modelo nos permite estimar la probabilidad de que un adolescente presente o no indicadores de depresión a partir de sus características. 

### Modelo 4: PCA
Se ocupa PCA como técnica de reducción de dimensionalidad para disminuir la cantidad de variables de entrada manteniendo la mayor parte de la información contenida en los datos. 

## Metodología aplicada (paso a paso).

1. Se importaron todas las librerias que fueron necesarias para el desarrollo de los modelos.

2. Se cargó el dataset Teen_Mental_Health_Dataset.csv y se realizó la visualizaación inicial para conocer la cantidad de registros, tipos de datos y valores faltantes.

3. Se llevó a cabo un EDA, utilizando estadísticas descriptivas y visualizaciones para comprender la distribución de las variables.

4. Se transforman las variables categóricas a formato numérico para que pudieran ser utilizadas por los modelos.

5. Las variables numéricas fueron estandarizadas utilizando StandardScaler.

6. El conjunto de datos fue dividido en entrenamiento y prueba.

7. Se entrenó un modelo de Regresión Logística para predecir los indicadores de depresión en adolescentes.

8. Se entrenó un modelo Random Forest para comparar sus resultados con los obtenidos por la Regresión Logística.

9. Se entrenó un modelo Naive Bayes utilizando un enfoque probabilístico basado en el Teorema de Bayes.

10. Se aplicó PCA para reducir la cantidad de variables del conjunto de datos, conservando aproximadamente el 95% de la información original.

11. Finalmente, los modelos fueron evaluados mediante Accuracy, Precision, Recall y F1-Score para comparar su desempeño.

## Resultados obtenidos
### Resultados Regresión Logistica:
Se obtuvo un Accurace de 98.75%, que nos indica un desempeño elevado ya que el modelo realiza una gran cantidad de predicciones correctas. La precisión alcanzó el 100%, por lo que todas las predicciones positivas fueron correctas. Sin embargo, el Recall fue de 50%, indicando que el modelo solo logró identificar la mitad de los adolescentes que efectivamente presentaban indicadores de depresión.

### Resultados Random Forest:
Se obtuvo un Accuracy de 97.92%, lo que indica que clasificó correctamente la gran mayoría de los registros. LLa precisión alcanzó el 100%, por lo que todas las predicciones positivas fueron correctas. Sin embargo, el Recall fue de 16.67%, lo que significa que el modelo identificó solo una pequeña parte de los adolescentes que realmente presentaban indicadores de depresión. Finalmente, pese a su buena precisión, el modelo solo alcanzó un F1-Score del 28.57%, ya que su baja sensibilidad deja fuera demasiados casos positivos.

### Resultados Naive Bayes:
Se obtuvo un Accuracy de 98.75%, logrando clasificar correctamente la mayoría de los datos. La Precision fue de 100%, lo que indica que todas las predicciones positivas realizadas fueron correctas. Por otro lado, el Recall alcanzó un 50%, por lo que solo se detectó la mitad de los casos reales de depresión. Finalmente, el F1-Score fue de 66.67%, reflejando un buen desempeño general del modelo.

### Resultados PCA:
Se logró una reducción efectiva de la dimensionalidad al seleccionar 13 componentes principales que, en conjunto, retienen un 96.87% de la varianza total del conjunto original. Los autovalores reflejan una concentración decreciente de la relevancia estadística, donde el primer componente lidera con un valor de 1.654 y explica por sí solo el 11.80% de la variabilidad. 

## Conclusiones

Los resultados obtenidos muestran que variables como el uso de redes sociales, las horas de sueño, la actividad física, el estrés y la ansiedad pueden estar relacionadas con la presencia de indicadores de depresión en adolescentes.

La Regresión Logística y Naive Bayes fueron los modelos con mejor desempeño, alcanzando un Accuracy de 98.75%, mientras que Random Forest obtuvo un Accuracy de 97.92%, pero con una menor capacidad para detectar casos positivos.

Además, PCA permitió reducir la dimensionalidad del conjunto de datos conservando un 96.87% de la varianza total mediante 13 componentes principales, simplificando el análisis sin perder información relevante.

En conclusión, los modelos aplicados mostraron ser eficientes para reconocer señales de depresión en jóvenes, resaltando la Regresión Logística y Naive Bayes como las mejores opciones para este desafío.