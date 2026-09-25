# CNN y Transfer Learning con DermMNIST

En este taller se desarrolló un modelo de clasificación de imágenes médicas utilizando el dataset **DermMNIST**, compuesto por imágenes dermatoscópicas de lesiones cutáneas pertenecientes a siete clases diferentes. Se implementó una **Red Neuronal Convolucional (CNN)** desde cero y un modelo basado en **Transfer Learning utilizando ResNet18** para realizar la clasificación multiclase.

Se evaluó el rendimiento de los modelos mediante métricas como **Accuracy, ROC-AUC multiclass, matriz de confusión y clasificación por clase**. Además, se analizaron diferentes estrategias de mejora del entrenamiento, incluyendo la modificación de la arquitectura CNN mediante **Batch Normalization, Dropout y aumento del número de filtros convolucionales**, junto con la aplicación de **Data Augmentation y Learning Rate Scheduler** para mejorar la capacidad de generalización del modelo y analizar posibles problemas de *overfitting*.

Finalmente, se realizaron experimentos de **calibración de probabilidades** y análisis mediante **curvas ROC multiclass**, permitiendo evaluar no solo la capacidad predictiva de los modelos, sino también la confiabilidad de sus probabilidades estimadas. También se compararon las diferentes configuraciones implementadas para identificar el impacto de cada técnica en la clasificación de imágenes médicas.
