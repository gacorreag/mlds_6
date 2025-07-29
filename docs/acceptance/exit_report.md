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

![Mapa de susceptibilidad a deslizamientos](Mapa.jpg)

## Lecciones aprendidas

Mostrar siempre los detalles

Copiar
from pathlib import Path

# Contenido del archivo Markdown con lecciones aprendidas
contenido_md = """
# Lecciones aprendidas

## Identificación de los principales desafíos y obstáculos encontrados durante el proyecto

Durante el desarrollo del proyecto se presentaron diversos desafíos, entre ellos:

- La integración de múltiples fuentes de datos geoespaciales con diferentes resoluciones y formatos (raster y vector).
- El manejo de grandes volúmenes de información satelital (NDVI, CHIRPS, geología, etc.) en Google Earth Engine y su posterior descarga para entrenamiento local.
- La necesidad de reescalar imágenes para que tuvieran coherencia espacial (e.g., precipitación CHIRPS de 5 km a 30 m).
- La validación y reentrenamiento del modelo CNN para adaptarse a la estructura espacial de los cubos 13x13x7.
- La serialización y uso correcto del modelo en un entorno de despliegue mediante FastAPI y Railway, así como el manejo de formatos de entrada JSON.

## Lecciones aprendidas en relación al manejo de los datos, el modelamiento y la implementación del modelo

- **Datos:** Es crucial contar con un pipeline sólido de preprocesamiento geoespacial que incluya reproyección, normalización, codificación y verificación visual antes del entrenamiento. La calidad y coherencia del stack multibanda influye directamente en el desempeño del modelo.
- **Modelamiento:** La arquitectura CNN mostró buenos resultados para identificar patrones espaciales relacionados con la ocurrencia de deslizamientos. La forma del input (13x13x7) fue clave para capturar contexto geográfico local.
- **Implementación:** El uso de FastAPI permitió plantear una API que si bien requiere muchisimo mas trabajo, tiene un gran potencial como aplicativo para la prevencion de desastres naturales por movimientos en masa en Colombia especialmente en la región cafetera.
- **Pruebas:** Las pruebas con ejemplos reales extraídos del dataset permitieron verificar la coherencia del modelo y detectar errores en el preprocesamiento de la entrada.

## Recomendaciones para futuros proyectos de machine learning

- Definir desde el inicio una convención clara para los datos (nombres de capas, resoluciones, codificaciones) y usar scripts reproducibles.
- Incluir tests automáticos para verificar que los datos de entrada cumplen los requisitos del modelo.
- Implementar notebooks o scripts de validación para probar la API antes del despliegue.
- Usar herramientas de versionamiento como DVC o MLflow desde fases tempranas para tener trazabilidad.
- Validar el modelo con múltiples ejemplos de cada clase para evitar sobreajuste y mejorar generalización.
- Documentar el flujo completo desde la recolección de datos hasta la predicción, incluyendo ejemplos de uso reales para facilitar la apropiación por terceros.


## Impacto del proyecto

- Descripción del impacto del modelo en el negocio o en la industria.
- Identificación de las áreas de mejora y oportunidades de desarrollo futuras.

## Conclusiones

- Resumen de los resultados y principales logros del proyecto.
- Conclusiones finales y recomendaciones para futuros proyectos.

## Agradecimientos

- Agradecimientos al equipo de trabajo y a los colaboradores que hicieron posible este proyecto.
- Agradecimientos especiales a los patrocinadores y financiadores del proyecto.
