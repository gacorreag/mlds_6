# Entendimiento del Negocio

## Predicción de Deslizamientos mediante Machine Learning
Las alcaldias y gobernaciones, dentro de su Plan de Ordenamiento Territorial y Planes de Prevención de Riesgos, necesitan diseñar Sistemas de Información Geográfica y/o mapas de clasificación del riesgo y modelos de predicción de ocurrencia de desastres naturales. Uno de los principales desastres naturales en Colombia son los deslizamientos de laderas, esto debido la compleja fisiografia y clima tropical. El desarrollo de modelos clasificatorios y predictivos basados en información satelital y directa de las zonas de impacto se presenta como una solución no solo para ser una guia de organización urbanística y de infraestrucutra vial sino también para salvar vidas.


## Objetivo del Proyecto
El objetivo principal del proyecto es realizar un modelo de clasificación del riesgo por deslizamiento e implementar un sistema de predicción con alertas tempranas para el departamento de Caldas.Todo integrado en una intrfase para el usuario. 

## Alcance del Proyecto

**Incluye:**
- Recopilación, Análisis y estandarización de datos geoespaciales y datos tabulares
- Propuesta de variables clave y metodología para la predicción de deslizamientos.
- Implementación de un modelo de ML supervisado de clasificación.
- Validación del modelo con métricas de desempeño.
- Despliegue del modelo en una interfase dinámica.
- Informe final de clasificación del riesgo sísmico en formato PDF.

**Excluye:**
- Soporte técnico y actualizaciones

## Metodología

1) Aquisición de datos geoespaaciales (Modelos de elevacion digital, Mapas geológicos, Cartografica de fallas gelógicas, usos del suelo, registros de precipitaciones)
2) Organizacion de las etiquetas positivas (donde si hay deslizamientos) a partir de la base de datos de registros historicos de deslizamientosSIMMA del Servicio Gelógico Colombiano 
3) Generación aleatoria de puntos con etiquetas negativas (donde no hay deslizamientos) y la asignación de sus respectivas variables 
4) balanceo y preprocesamiento de la matriz de valores
5) entrenamiento de tres modelos de ML 
6) evaluación de los respectivos modelos
7) Desarrollo web (HTML) de una interface para la interacción de usuario modelo 
8) Generar mapa de clasificación e informe del riesgo por deslizamiento a partir de los resultados arrojados por el modelo.  


## Cronograma


| **Etapa**                                                       | **Descripción**                                                                                                         | **Duración (días)** | **Fecha de inicio** | **Fecha de finalización** |
| --------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ------------------- | ------------------- | ------------------------- |
| **1. Adquisición de datos geoespaciales**                       | Recolección de información geográfica como DEM, mapas geológicos, fallas, coberturas del suelo, datos de precipitación. | 3 días              | 1 de julio          | 3 de julio                |
| **2. Organización de etiquetas positivas**                      | Filtrado y organización de los registros históricos de deslizamientos del SIMMA. Georreferenciación y validación.       | 2 días              | 4 de julio          | 5 de julio                |
| **3. Generación de puntos negativos y asignación de variables** | Generación de puntos aleatorios en zonas sin deslizamiento y extracción de variables geográficas correspondientes.      | 3 días              | 6 de julio          | 8 de julio                |
| **4. Preprocesamiento y balanceo de la matriz de datos**        | Limpieza, normalización y balanceo de clases para la matriz final usada en el modelado.                                 | 2 días              | 9 de julio          | 10 de julio               |
| **5. Entrenamiento de modelos de ML**                           | Entrenamiento de al menos tres modelos (por ejemplo, Random Forest, SVM, XGBoost) para clasificación del riesgo.        | 3 días              | 11 de julio         | 13 de julio               |
| **6. Evaluación y selección del mejor modelo**                  | Comparación del desempeño de los modelos con métricas (precisión, recall, F1, AUC). Selección del más eficiente.        | 2 días              | 14 de julio         | 15 de julio               |
| **7. Desarrollo de la interfaz web**                            | Desarrollo en HTML (u otro framework web ligero) para visualización de resultados y mapas interactivos.                 | 4 días              | 16 de julio         | 19 de julio               |
| **8. Generación del informe final y mapa de clasificación**     | Elaboración de mapa final de clasificación del riesgo y redacción de informe PDF. Integración de visualizaciones.       | 3 días              | 20 de julio         | 22 de julio               |


## Equipo del Proyecto

- Nixon Iván Sotelo Figueroa
- David Mateo Granados Sarmiento
- Juan Andres Martinez Moreno

## Presupuesto

| **Ítem**                                                        | **Descripción**                                                                      | **Horas estimadas** | **Valor hora (COP)** | **Valor total (COP)** |
| --------------------------------------------------------------- | ------------------------------------------------------------------------------------ | ------------------- | -------------------- | --------------------- |
| **1. Recolección de datos geoespaciales**                       | Búsqueda, descarga y procesamiento de DEM, geología, fallas, lluvias, uso del suelo. | 12 h                | \$60.000             | \$720.000             |
| **2. Organización de registros SIMMA**                          | Limpieza, validación y georreferenciación de registros históricos.                   | 10 h                | \$60.000             | \$600.000             |
| **3. Generación de puntos negativos y asignación de variables** | Automatización de puntos sin deslizamiento y extracción de variables geográficas.    | 12 h                | \$60.000             | \$720.000             |
| **4. Preprocesamiento y balanceo de datos**                     | Normalización, balanceo, codificación y consolidación del dataset final.             | 10 h                | \$60.000             | \$600.000             |
| **5. Entrenamiento y evaluación de modelos ML**                 | Random Forest, SVM, XGBoost; evaluación de métricas y selección del mejor modelo.    | 16 h                | \$60.000             | \$960.000             |
| **6. Desarrollo de interfaz web**                               | Interfaz HTML/CSS/JS para visualización del modelo y mapa de riesgo.                 | 18 h                | \$60.000             | \$1.080.000           |
| **7. Generación de mapas y visualizaciones**                    | Exportación de mapas de clasificación, elaboración de gráficos.                      | 10 h                | \$60.000             | \$600.000             |
| **8. Redacción del informe técnico final (PDF)**                | Análisis, resultados, metodología, gráficas y mapa final.                            | 12 h                | \$60.000             | \$720.000             |
| **9. Gestión del proyecto y reuniones**                         | Coordinación, comunicación con el cliente, seguimiento de cronograma.                | 10 h                | \$60.000             | \$600.000             |
| **10. Infraestructura y licencias menores**                     | Hosting temporal, APIs externas o suscripciones necesarias.                          | 6 h                 | \$60.000             | \$360.000             |


## Stakeholders

- Funcionarios de gobernaciones y acaldias encargados del Plan de Odenamietno Territorial y Gestion del Riesgo. En general todas las comunidades qe viven en zonas suceotsuceptibles a deslizaientos 

## Aprobaciones

-  Juan Andres Martinez Moreno
- JM
- 3 de julio de 2025
