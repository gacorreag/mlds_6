# Predicción de Deslizamientos mediante Machine Learning

Este repositorio fue creado para desarrollar un proyecto basado en CNN con el objetivo de utilizar imagenes satelitales para la predicción y/o estimacion de movimientos en masa en la zona cafetera de Colombia. El proyecto fue desarrolla en el marco del "Programa de Formación en Machine Learning y Data Science" de la Universidad Nacional de Colombia.

Proporciona las siguientes carpetas y archivos:

* `docs`: En esta carpeta se encuentran las plantillas de los documentos definidos en la metodología.
* `scripts`: Esta carpeta contiene los scripts/notebooks que se ejecutaron durante el proyecto
* `Proyecto_despliegue`: Aqui se encontraran los archivos utilizados para el desarrollo de la API
* `pyproject.toml`: archivo de definición del proyecto en Python.


## Variables utilizadas
---

Se genero un archivo raster .tif multibanda (stack_landslide_def.tif) compuesto por 8 bandas, cada una representando una variable relevante para la modelación de la susceptibilidad a deslizamientos. Las bandas fueron reescaladas a una resolución común (30 m/pixel) y alineadas espacialmente. De allí fue donde se obtuvieron los datos para hacer el entrenamiento del modelo.

| Banda | Variable original  | Descripción breve                                       | Tipo de dato | Rango/Valores observados | Fuente de datos                 |
| ----- | ------------------ | ------------------------------------------------------- | ------------ | ------------------------ | ------------------------------- |
| 1     | Pendiente          | Inclinación del terreno calculada a partir del DEM      | float32      | 0.0 – 84.12              | Derivado de SRTM                |
| 2     | TRI                | Índice de Rugosidad Topográfica (con outliers extremos) | float32      | -3.40e+38 – 259.73       | Derivado de SRTM                |
| 3     | DEM                | Modelo digital de elevación                             | float32      | 0.0 – 5287.0             | SRTM                            |
| 4     | Distancia a fallas | Distancia en grados a la falla más cercana              | float32      | 0.0 – 0.16296            | Fallas geológicas (SGC)         |
| 5     | NDVI               | Índice de vegetación normalizada                        | float32      | -0.026 – 0.8685          | MODIS (2009–presente, promedio) |
| 6     | Precipitación      | Promedio anual histórico de precipitación               | float32      | 0.0 – 233.87             | CHIRPS (vía GEE)                |
| 7     | Geología           | Codificación raster de unidades geológicas              | float32      | 1.0 – 127.0              | Mapa Geológico (SGC)            |
| 8     | TWI clasificado    | Índice topográfico de humedad categorizado              | float32      | 0.0 – 3.0                | Derivado de TWI                 |
