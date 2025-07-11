# Definición de los datos
---
## Origen de los datos

Los datos utilizados en este proyecto provienen de fuentes públicas y confiables:

Datos raster: Variables geoespaciales extraídas desde Google Earth Engine (GEE) y otros portales satelitales. Estas incluyen NDVI (MODIS), precipitación (CHIRPS), elevación, pendiente, TRI, TWI y geología (SGC).

Datos vectoriales: Mapa de deslizamientos históricos del SIMMA (Servicio Geologico Colombiano).

Datos derivados: A partir de los rásters se generó un stack multibanda para facilitar la integración y análisis.

La zona de estudio se ubica en el eje cafetero colombiano, específicamente en el departamento de Caldas. 

## Especificación de los scripts para la carga de datos
---

- Los siguientes scripts se implementaron para la carga, procesamiento y transformación de los datos:

scripts/eda/Analisis_exploratorio.ipynb: Carga y apilamiento de bandas raster en un archivo .tif multibanda, exploración estadística de bandas y etiquetas.

(Hasta ahora)

### Rutas de origen de datos
---

Ubicación: Los archivos ráster originales fueron descargados y almacenados en el directorio:

**"https://drive.google.com/drive/u/1/folders/19IrDKVTtjPZG48GnoWkf8Fudcyu_2aCI"**

Estructura: Cada archivo corresponde a una variable distinta y está en formato .tif. Ejemplos:

slope.tif

ndvi.tif

chirps_precip.tif

geology.tif

Procedimientos de transformación y limpieza:

Resampleo a resolución común (30 m).

Normalización de bandas (min-max).

Eliminación de bandas redundantes o con bajo aporte (ej. Banda 2).

Apilamiento de todas las capas en un único stack multibanda: stack_landslide_def.tif.

### Base de datos de destino
---

Ubicación: El stack multibanda final fue almacenado como:

**"stack_landslide_def.tif"**

Estructura: Archivo raster multibanda con tamaño espacial uniforme y 6 bandas útiles para la predicción.

Procedimientos de carga y transformación:

Extracción de parches 13x13 píxeles con ventana deslizante.

Asignación de etiqueta binaria según ocurrencia de deslizamiento en el centro del parche.

Conversión a archivos .npy para entrenamiento eficiente: X_cubos.npy y y_etiquetas.npy.
