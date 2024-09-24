# Descripción General

El proyecto tiene como objetivo predecir el precio del oro utilizando técnicas de regresión lineal con machine learning tradicional. Para lograrlo, se utiliza un dataset histórico que contiene información sobre los precios y el volumen de oro mes a mes. El flujo del proyecto está dividido en tres etapas principales, distribuidas en las siguientes notebooks: Feature Pipeline, Training Pipeline, y Batch Inference Pipeline.

1. Feature Pipeline Notebook
Esta notebook está dedicada al preprocesamiento de datos y la creación de características útiles para el modelo.

Pasos principales:

- Carga de datos: El archivo gold.csv es cargado y se muestran las primeras filas del dataset.
Transformación de fechas: La columna "Date" es convertida a un formato de fecha apropiado y se extraen las características de día, mes y año para un mejor análisis temporal. Se eliminan todos los registros previos al año 2015.
- Análisis Exploratorio de Datos (EDA): Se exploran las variables, revisando las estadísticas descriptivas y visualizando las relaciones entre las columnas. Esto incluye gráficas de líneas para observar la evolución de los precios del oro.
- Ganancia de Información Mutua: Se utiliza esta técnica para evaluar la relevancia de las características con respecto a la variable objetivo (precio del oro).
- LazyPredict: Se comparan diferentes modelos de machine learning tradicionales para identificar los que tengan mejor desempeño en la predicción del precio, con métricas como el MSE (error cuadrático medio).
- Reducción de datos: Se reduce el dataset a 100,000 registros para optimizar el procesamiento.
Almacenamiento de Características: Los datos preprocesados y las etiquetas (precio del oro) se guardan en archivos .pkl para su uso en la siguiente fase.

2. Training Pipeline Notebook
Esta notebook se centra en el entrenamiento de un modelo de regresión para predecir el precio del oro.

Pasos principales:

- Carga de datos preprocesados: Se cargan los archivos de características y etiquetas generados en la notebook de Feature Pipeline.
- División de los datos: Se dividen los datos en conjuntos de entrenamiento y prueba (80% y 20%, respectivamente).
- Selección del Modelo: Se utiliza el modelo HuberRegressor, conocido por ser robusto a valores atípicos y adecuado para problemas de regresión.
- Entrenamiento del modelo: El modelo es entrenado usando los datos de entrenamiento.
- Evaluación del modelo: Se calculan métricas de desempeño como el Mean Squared Error (MSE) y el Mean Absolute Error (MAE) sobre el conjunto de prueba.
- Registro en MLFlow: El modelo entrenado y las métricas de evaluación son registrados en MLFlow para un seguimiento adecuado.
- Guardado del modelo entrenado: El modelo final se guarda en un archivo .pkl para su uso posterior en la inferencia.

3. Batch Inference Pipeline Notebook
La notebook de inferencia por lotes está dedicada a realizar predicciones sobre nuevos datos o lotes de datos históricos no vistos previamente.

Pasos principales:

- Carga del modelo entrenado: Se carga el modelo guardado desde la fase de entrenamiento.
- Carga de nuevos datos: Se cargan nuevos datos o datos históricos para los cuales se desea predecir el precio del oro.
- Realizar predicciones: El modelo realiza predicciones sobre los datos ingresados.
- Almacenamiento de predicciones: Las predicciones se guardan en un archivo CSV para su análisis o posterior uso.

Resultados Esperados

a) Modelo de Regresión Robusto: El proyecto debe producir un modelo basado en HuberRegressor que pueda predecir el precio del oro de manera eficiente, incluso en presencia de valores atípicos.

b) Métricas de Desempeño: Las métricas esperadas para evaluar el modelo incluyen MSE y MAE. Se espera que el modelo logre minimizar estos errores para obtener una alta precisión en la predicción del precio del oro.

c) Pipeline de Inferencia por Lotes: Un pipeline funcional para realizar predicciones en lotes grandes de datos históricos o nuevos, utilizando el modelo previamente entrenado.

Este proyecto está orientado a la creación de un flujo de trabajo completo y reproducible, desde la ingeniería de características hasta la inferencia por lotes, aplicable a predicciones financieras y económicas, como la estimación del precio del oro.

Base de datos empleada en el proyecto: [Kaggle Link](https://www.kaggle.com/datasets/sid321axn/gold-price-prediction-dataset)