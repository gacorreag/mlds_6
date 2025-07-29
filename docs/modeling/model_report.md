# Reporte del Modelo Final

## Resumen Ejecutivo

Se desarrolló un modelo de red neuronal convolucional (CNN) para la clasificación binaria de cubos multiespectrales de tamaño 13×13×7. El modelo logró una precisión de validación del 77%, evidenciando un desempeño funcional, aunque con espacio para mejoras.

El proceso de desarrollo incluyó normalización banda a banda, eliminación de una banda con ruido o poca información (banda 2), y el uso de técnicas robustas de regularización y optimización como Dropout, BatchNormalization, EarlyStopping y ReduceLROnPlateau.

Las métricas obtenidas, junto con la inspección visual de curvas de pérdida y precisión, indican un entrenamiento razonablemente estable sin sobreajuste significativo

## Descripción del Problema

El objetivo del proyecto es desarrollar un clasificador capaz de detectar un fenómeno binario (como deslizamiento o no deslizamiento) en un área geográfica, a partir de información espectral en cubos de 13x13 píxeles y 7 bandas.

Cada imagen representa un fragmento georreferenciado del terreno, donde cada canal espectral aporta información como vegetación, humedad, pendiente, entre otros. La clasificación permite generar mapas de susceptibilidad que apoyan la toma de decisiones en prevención de riesgos o planificación territorial.

Este problema es complejo debido a:El alto volumen de datos espectrales, la dimensionalidad espacial y espectral,la posible desbalance en las clases (fenómeno vs no-fenómeno), la necesidad de modelos que aprendan relaciones no lineales entre pixeles y bandas

## Descripción del Modelo

Se utilizó una red neuronal convolucional (CNN) implementada con una arquitectura secuencial en Keras, diseñada para extraer patrones tanto espaciales como espectrales a partir de cubos multibanda de entrada con dimensiones 13×13×7. La arquitectura consta de tres bloques consecutivos de capas convolucionales Conv2D con 32, 64 y 128 filtros respectivamente, cada uno seguido por normalización por lotes (BatchNormalization), una capa de reducción de dimensionalidad (MaxPooling2D) y una capa de regularización mediante abandono (Dropout) con tasas progresivas de 0.25, 0.3 y 0.35. Posteriormente, la salida es aplanada con una capa Flatten y pasada por una capa densa de 128 unidades con activación ReLU, seguida de otra capa Dropout con una tasa de 0.5. Finalmente, se utiliza una capa Dense de salida con una sola neurona y activación sigmoide, adecuada para clasificación binaria. El modelo se entrenó utilizando el optimizador Adam con una tasa de aprendizaje de 0.001, empleando la función de pérdida binary_crossentropy y utilizando la precisión (accuracy) como métrica principal de desempeño. Para evitar el sobreajuste y mejorar la eficiencia del entrenamiento, se incorporaron las técnicas de EarlyStopping con una paciencia de 30 épocas y ReduceLROnPlateau con paciencia de 10, lo que permitió reducir dinámicamente la tasa de aprendizaje si la pérdida de validación se estancaba.

## Evaluación del Modelo

En este caso para mostrar la evaluacion del modelo vamos a mostrar el reporte de clasificación.

<img width="497" height="150" alt="image" src="https://github.com/user-attachments/assets/0cd1b726-9cc2-4172-9a45-57044b495e29" />

  
Buen balance entre precisión y recall.

El modelo generaliza bien con los datos actuales, aunque podría beneficiarse de mayor balanceo de clases o datos aumentados.

## Conclusiones y Recomendaciones

Fortalezas:

- Modelo liviano, con arquitectura clara y eficiente.

- Precisión superior al azar, cercana al 80%.

- Entrenamiento estable y sin sobreajuste.

- Código portable y reutilizable.

Limitaciones:

- No se utilizó validación cruzada.

- El dataset puede estar desbalanceado, afectando métricas por clase.

- No se usaron técnicas de aumento de datos ni modelos alternativos para comparación.

Recomendaciones:

- Incorporar matriz de confusión y análisis por clase.

- Probar modelos alternativos como RandomForest, XGBoost o otras alternativas de ML que quiza muesyten un funcionamiento eficiente

- Implementar k-fold cross-validation para evaluar robustez.

- Hacer tuning de hiperparámetros con KerasTuner o Optuna

## Referencias

En esta sección se deben incluir las referencias bibliográficas y fuentes de información utilizadas en el desarrollo del modelo.
