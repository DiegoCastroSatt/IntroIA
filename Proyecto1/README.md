# Titulo del Proyecto: Análisis y Predicción del Impacto del COVID-19
### Autor: Diego Castro

## Descripción del problema: 
El objetivo es clasificar el nivel de riesgo de distintos países utilizando indicadores relacionados con casos confirmados, fallecidos, recuperados y casos activos de COVID-19 en el 2020.
## Descripción del Dataset:
El dataset utilizado corresponde a `country_wise_latest.csv`, sacado desde https://www.kaggle.com/datasets/imdevskp/corona-virus-report compuesto por 187 paises y 15 variables. Algunas de las variables son:
1. Country/Region es el nombre del pais y/o región que fue analizada.
2. Confirmed son los casos confirmados en el 2020 por el COVID-19.
3. Deaths son el total de fallecidos hasta la fecha que fue realizado el Dataset (Enero 2020).
4. Recovered son las personas recuperadas.
5. Active son los casos que estaban activos al momento de recabar los datos.

## Justificación de los modelos seleccionados.
Para abordar este problema de clasificación de riesgo de los paises, seleccione tres modelos para analizar los datos.
El **PCA** fue usado para la reducción de dismensionalidad, para disminuir la redundancia entre algunas variables.
La **Regresión Logística** me permitio estimar la probabilidad de que una observación pertenezca a una determinada categoría de riesgo. 
**Random Forest** al combinar múltiples árboles de decisión, este modelo reduce el riesgo de sobreajuste.

## Metodología aplicada (paso a paso).
 1. **Carga y Visualización de los Datos:** Se utilizó el dataset country_wise_latest.csv, el cual contiene información de 187 países, incluyendo variables relacionadas con casos confirmados, fallecidos, recuperados y casos activos.
 2. **EDA:** Se hizo un análisis exploratorio para ver las estadisticas descriptivas, histogramas, diagramas de caja y una matriz de correlación para reconocer e identificar como se distribuyen los datos.
 3. **Feature Engineering:** Se calculó la tasa de mortalidad, tasa de recuperación y la tasa de casos activos, lo que nos permite representar como estaba la situación sanitaria en cada país. Aparte fue construida una variable (Risk_Level), que se encargo de clasificar en las categorias Bajo, Medio y Alto según los niveles que se pueden observar. Luego se aplico un StandarScaler para normalizar las variables.
 4. **PCA:** Se redujo la dimensionalidad del conjuhto de datos, y así nos permitió seleccionar cuatro componentes principales, para conseervar aproximadamente el 98% de la varianza total de los datos.
 5. **Logistic Regresion:** Se entrenó un modelo de Regresión Logística utilizando los componentes obtenidos mediante PCA. Posteriormente se evaluó su desempeño mediante Accuracy, Precision, Recall y F1-Score.
 6. **Random Forest:** Se entrenó un modelo Random Forest utilizando los mismos datos procesados y componentes principales. El modelo fue evaluado utilizando las mismas métricas para permitir una comparación objetiva con la Regresión Logística.
 7. **Comparación de Resultados:** Se comparó el desempeño de ambos modelos utilizando métricas de clasificación y matrices de confusión, permitiendo identificar cuál de ellos entregó mejores resultados para la clasificación del nivel de riesgo.
 
## Resultados obtenidos
Se aplicó PCA para reducir la dimensionalidad de los datos antes de entrenar los modelos. El análisis permitió seleccionar 4 componentes principales, conservando aproximadamente el 98.62% de la varianza total.
Los modelos de Regrersión Logisica y Random Forest entregaron:
| Modelo | Accuracy | Precision | Recall | F1-Score |
|---------|----------|-----------|--------|----------|
| Logistic Regression | 52.63% | 55.81% | 52.63% | 53.63% |
| Random Forest | 86.84% | 86.81% | 86.84% | 86.74% |

Los resultados muestran que Random Forest obtuvo un mejor desempeño en todas las métricas evaluadas.

## Conclusiones

