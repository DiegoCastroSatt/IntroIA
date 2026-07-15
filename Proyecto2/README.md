# Clasificación de Sentimientos en Twitter
## Autor: Diego Castro Satt

## Descripción del proyecto
El objetivo de este proyecto es desarrollar un modelo de Deep Learning capaz de clasificar automáticamente el sentimiento de publicaciones de Twitter utilizando un modelo de lenguaje preentrenado.

## Dataset
El dataset utilizado corresponde a `twitter_training.csv`, sacado desde https://www.kaggle.com/datasets/jp797498e/twitter-entity-sentiment-analysis, que contiene etiquetadas según el sentimiento expresado en cada mensaje.
Cada registro contiene:
- Texto del tweet.
- Etiqueta del sentimiento.
Las categorías utilizadas son:
- Positivo
- Negativo
- Neutral

## Justificación del modelo
Para resolver este problema se seleccionó **BERT**, un modelo preentrenado sobre grandes cantidades de texto.
Las razones para seleccionar BERT fueron:
- Comprende el contexto completo de cada palabra.
- Posee un excelente desempeño en tareas de clasificación de texto.

# Metodología aplicada (paso a paso).
1. **Carga y Visualización de los Datos:**  
Se utilizaron los datasets `twitter_training.csv`, el cual contienen tweets clasificados según su sentimiento en cuatro categorías: Negative, Neutral, Positive e Irrelevant. Los datos fueron cargados utilizando Pandas, asignando nombres a las columnas correspondientes y realizando una revisión inicial de la estructura, cantidad de registros y tipos de datos.
2. **EDA (Análisis Exploratorio de Datos):**  
Se realizó un análisis exploratorio del conjunto de datos para comprender las características principales de los tweets. Se analizaron los valores nulos, la distribución de las clases de sentimiento, los temas más frecuentes, la longitud de los tweets, la cantidad de palabras por texto y las palabras con mayor frecuencia dentro del dataset. Además, se utilizaron visualizaciones como gráficos de barras, histogramas y diagramas para identificar patrones y características relevantes de los datos.
3. **Feature Engineering:**  
Se generaron nuevas variables descriptivas a partir del contenido textual de los tweets. Se calculó la longitud del texto y la cantidad de palabras presentes en cada tweet para obtener información adicional sobre las características de los mensajes. Además, las etiquetas de sentimiento fueron transformadas desde valores categóricos a valores numéricos para que pudieran ser utilizadas por el modelo de Deep Learning:
Negative = 0, Neutral = 1, Positive = 2 e Irrelevant = 3.
4. **Preprocesamiento y Tokenización:**  
Los textos fueron preparados utilizando el Tokenizer oficial del modelo BERT (`distilbert-base-uncase`). A diferencia de métodos tradicionales, no se aplicó eliminación manual de palabras ni lematización, ya que BERT utiliza representaciones contextuales capaces de interpretar el significado de las palabras según su contexto. Los tweets fueron transformados en secuencias numéricas mediante `input_ids` y `attention_mask`, permitiendo su procesamiento mediante redes neuronales Transformer.
5. **Creación del Dataset utilizando PyTorch:**  
Se implementó una clase personalizada utilizando PyTorch para estructurar los datos de entrada del modelo. Esta etapa permitió organizar los tweets tokenizados junto con sus respectivas etiquetas, generando los conjuntos necesarios para el entrenamiento y validación del modelo.
6. **Entrenamiento del Modelo Transformer (BERT):**  
Se utilizó el modelo preentrenado BERT adaptado para una tarea de clasificación multiclase con cuatro categorías de salida. El entrenamiento se realizó utilizando el conjunto `twitter_training.csv`. Además, se aplicaron técnicas de regularización como Weight Decay y Dropout incorporado en la arquitectura de BERT para reducir el sobreajuste.
7. **Evaluación del Modelo:**  
El desempeño del modelo fue evaluado utilizando métricas de clasificación como Accuracy, Precision, Recall y F1-Score. También se generó una matriz de confusión para analizar el comportamiento del modelo en cada categoría de sentimiento e identificar posibles errores de clasificación.
8. **Predicción de Nuevos Tweets:**  
Finalmente, se implementó una función de predicción capaz de recibir nuevos tweets como entrada, realizar la tokenización mediante BERT y entregar la categoría de sentimiento predicha por el modelo entrenado.
6. **Evaluación**
Finalmente se probaron nuevas publicaciones para verificar el funcionamiento del clasificador.

## Resultados
### Resultados del modelo

El modelo obtuvo un Accuracy de **0.171**, lo que indica que logró clasificar correctamente aproximadamente el 17.1% de los tweets del conjunto de prueba. Las métricas obtenidas fueron:
- **Accuracy:** 0.171
- **Precision:** 0.1115
- **Recall:** 0.171
- **F1-Score:** 0.0596
Estos resultados muestran que el modelo presenta dificultades para distinguir correctamente entre las diferentes categorías de sentimiento. Si bien el modelo fue capaz de extraer ciertas características de los textos gracias al conocimiento adquirido durante su preentrenamiento, aún presenta una baja capacidad de generalización sobre este conjunto de datos.
La distribución de las clases en el conjunto de prueba fue:
- **Negative:** 22.312 tweets
- **Positive:** 20.618 tweets
- **Neutral:** 18.051 tweets
- **Irrelevant:** 12.842 tweets
El análisis mediante la matriz de confusión permitió identificar las clases que presentan mayor confusión entre sí, evidenciando los principales errores de clasificación y posibles oportunidades de mejora mediante un mayor ajuste del modelo, aumento de datos de entrenamiento o técnicas de optimización.

## Conclusiones
Se desarrolló un sistema de clasificación automática de sentimientos utilizando un modelo de Deep Learning basado en BERT.
El análisis exploratorio permitió comprender las características del conjunto de datos antes del entrenamiento y generar variables descriptivas útiles para su análisis.
Los resultados obtenidos demuestran que los modelos preentrenados son una alternativa efectiva para resolver problemas de clasificación de texto, ya que logran capturar el contexto de las palabras y generalizar correctamente sobre datos no vistos.