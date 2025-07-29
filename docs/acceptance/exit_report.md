# Informe de salida

## Resumen Ejecutivo

Este informe describe los resultados del proyecto de machine learning y presenta los principales logros y lecciones aprendidas durante el proceso.

## Resultados del proyecto

# 🧾 Resultados del proyecto

## ✅ Resumen de los entregables y logros alcanzados en cada etapa del proyecto

A lo largo del proyecto se logró construir un sistema funcional de predicción de deslizamientos mediante aprendizaje profundo, específicamente con una red neuronal convolucional (CNN), aplicando imágenes multibanda extraídas de sensores satelitales en la zona cafetera de Colombia.  
Los principales entregables fueron:

- Recolección y procesamiento de datos satelitales de múltiples fuentes (CHIRPS, MODIS, SRTM, etc.).
- Generación de un stack multibanda con 7 capas rasterizadas, normalizadas y alineadas espacialmente.
- Construcción de cubos 13x13x7 a partir del stack, asociados a una etiqueta binaria (deslizamiento o no deslizamiento).
- Entrenamiento y evaluación de un modelo CNN.
- Despliegue de una API funcional en Railway usando FastAPI.
- Validación de la API con cubos reales serializados desde imágenes `.tif`.
- Generación de un nuevo `.tif` con los resultados de predicción espacial de susceptibilidad.

## 📊 Evaluación del modelo final y comparación con el modelo base

El modelo final logró una capacidad adecuada para diferenciar zonas con presencia de deslizamientos frente a zonas estables, mejorando el desempeño del modelo base que simplemente asumía distribuciones balanceadas o reglas heurísticas.  
La evaluación se realizó con métricas como precisión, recall y AUC, y se observó que la CNN permite captar patrones espaciales multivariados de manera robusta.  
Además, se construyó un *pipeline* desde el preprocesamiento hasta la predicción automática vía API, facilitando su reutilización.

## 🌍 Descripción de los resultados y su relevancia para el negocio

Como producto final, se generó un mapa de susceptibilidad a deslizamientos en la región cafetera de Colombia, con una resolución de 30 metros. Este resultado es particularmente valioso para:

- **Planeación territorial** y gestión del riesgo en áreas rurales de alta pendiente.
- **Infraestructura crítica**, permitiendo priorizar tramos viales o zonas de intervención.
- **Alertas tempranas**, si se integra con series temporales de precipitación y sensores en tiempo real.

A continuación, se adjunta el mapa generado a partir de la inferencia masiva sobre el stack multibanda. El resultado se almacenó como un archivo `.tif` georreferenciado y visualizado en el siguiente producto cartográfico:

![Mapa de susceptibilidad a deslizamientos](Mapa_de_susceptibilidad_a_deslizamientos_CNN.jpg)

## Lecciones aprendidas

- Identificación de los principales desafíos y obstáculos encontrados durante el proyecto.
- Lecciones aprendidas en relación al manejo de los datos, el modelamiento y la implementación del modelo.
- Recomendaciones para futuros proyectos de machine learning.

## Impacto del proyecto

- Descripción del impacto del modelo en el negocio o en la industria.
- Identificación de las áreas de mejora y oportunidades de desarrollo futuras.

## Conclusiones

- Resumen de los resultados y principales logros del proyecto.
- Conclusiones finales y recomendaciones para futuros proyectos.

## Agradecimientos

- Agradecimientos al equipo de trabajo y a los colaboradores que hicieron posible este proyecto.
- Agradecimientos especiales a los patrocinadores y financiadores del proyecto.
