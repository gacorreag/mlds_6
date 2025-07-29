# Informe de salida

## Resumen Ejecutivo

En Colombia, los deslizamientos de tierra representan una de las amenazas naturales más frecuentes y devastadoras, especialmente en regiones de compleja fisiografía como el departamento de Caldas. Estos eventos ponen en riesgo permanente la vida humana, la infraestructura vial y los desarrollos urbanos, particularmente en zonas rurales y de montaña. Frente a esta problemática, la integración de tecnologías de punta en ciencia de datos y teledetección se presenta como una oportunidad estratégica para fortalecer las capacidades locales de gestión del riesgo y planificación territorial.

En este contexto, nuestro equipo de tres geólogos con fortalezaas y formación en Sistemas de Información Geográfica (SIG) y ciencia de datos, emprendimos el desarrollo de una solución tecnológica enfocada en la predicción de deslizamientos mediante redes neuronales convolucionales (CNN). El propósito central fue diseñar un mapa de susceptibilidad a deslizamientos generado por lar red neuronal convolucional y basado en datos geoespaciales abiertos y accesibles, que pueda ser utilizada por instituciones gubernamentales, entes territoriales y comunidades vulnerables como herramienta de prevención y toma de decisiones.

El sistema se fundamenta en la integración y análisis de múltiples variables físicas, climáticas y geológicas, tales como precipitación máxima mensual histórica, cobertura vegetal (NDVI), distancia a fallas geológicas, litología, pendiente, elevación e índice topográfico de humedad. Estas variables fueron procesadas a partir de fuentes como CHIRPS, MODIS, SRTM y el inventario SIMMA de deslizamientos históricos realizado por el Servicio Geológico Colombino. El procesamiento y entrenamiento de los modelos se realizó utilizando Google Earth Engine y herramientas en Python como scikit-learn, rasterio y TensorFlow/Keras.

El modelo CNN desarrollado alcanzó un desempeño destacado, con una precisión del 74%, un recall del 83% y un F1-score de 0.79, permitiendo generar mapas de clasificación de riesgo con alta capacidad predictiva. La aplicación fue desplegada mediante una API, lo que garantiza su escalabilidad y adaptabilidad a nuevas regiones o escenarios.

Esta plataforma constituye un aporte significativo al uso de tecnologías accesibles y de código abierto para la prevención de desastres naturales, y plantea una ruta viable para el fortalecimiento de las políticas de ordenamiento territorial y mitigación del riesgo en Colombia y América Latina..

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

- Esta plataforma puede escalarse fácilmente a otras regiones andinas o latinoamericanas.
Puede complementarse con un sistema de alertas tempranas, conectando sensores en
tiempo real.
- Promueve la ciencia abierta y el uso de tecnología accesible para gobiernos locales y
comunidades.

## Conclusiones

1. **Integración exitosa de datos geoespaciales y modelado con aprendizaje profundo**  
   El proyecto logró consolidar un pipeline completo, desde la recopilación y procesamiento de datos satelitales y geológicos hasta el entrenamiento e implementación de una red neuronal convolucional. Esto permitió generar un mapa de susceptibilidad a deslizamientos con una resolución espacial de 30 metros y métricas destacadas de desempeño (**precisión: 0.74, recall: 0.83, F1-score: 0.79**), lo que evidencia la viabilidad de aplicar técnicas de *deep learning* en la gestión del riesgo geológico.

2. **Despliegue de una API funcional para predicción automatizada**  
   La creación y validación de una API basada en FastAPI permitió materializar un producto tecnológico práctico y escalable, capaz de recibir cubos multibanda como entrada y entregar predicciones de susceptibilidad en tiempo real.

3. **Relevancia territorial y aplicabilidad del producto final**  
   El mapa generado ofrece un insumo valioso para la **planeación territorial** y la gestión de **infraestructura crítica** en regiones montañosas como Caldas. La herramienta puede ser utilizada por alcaldías, gobernaciones y organismos de emergencia como soporte técnico para la toma de decisiones y priorización de zonas de riesgo.

4. **Lecciones clave para el manejo de datos y modelos en geociencias**  
   El proyecto reafirmó la importancia de un preprocesamiento riguroso y reproducible, especialmente en contextos donde se integran fuentes heterogéneas (raster y vector, con distintas resoluciones). La arquitectura CNN demostró ser una opción eficaz para capturar patrones espaciales complejos, siempre que se realicen pruebas con casos reales y balanceo adecuado de las clases.

5. **Recomendaciones para proyectos futuros**  
    Se sugiere incorporar sensores en tiempo real y series temporales en futuras versiones para fortalecer las capacidades de alerta temprana y respuesta ante emergencias.


## Agradecimientos

- Agradecimientos al equipo de trabajo del Diplomado MLDS en especial a los profesores y auxiliares que acompañaron nuestro proceso durante el modulo 6.

