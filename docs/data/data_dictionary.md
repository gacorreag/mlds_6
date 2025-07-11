# Diccionario de datos

## Base de datos 1: Stack ráster multibanda
---

Archivo raster .tif multibanda (stack_landslide_def.tif) compuesto por 8 bandas, cada una representando una variable relevante para la modelación de la susceptibilidad a deslizamientos. Las bandas fueron reescaladas a una resolución común (30 m/pixel) y alineadas espacialmente.

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


## Base de datos 2
---

Archivos NumPy generados para entrenamiento y evaluación del modelo CNN. Incluyen parches de entrada 13x13x6 y etiquetas binarias.

| Variable         | Descripción                                          | Tipo de dato         | Rango/Valores posibles                    | Fuente de datos               |
| ---------------- | ---------------------------------------------------- | -------------------- | ----------------------------------------- | ----------------------------- |
| X\_cubos.npy     | Matriz de entrada con cubos 13x13 píxeles y 6 bandas | float32\[𝑛,13,13,6] | 0.0 – 1.0 (normalizado)                   | Derivado del stack multibanda |
| y\_etiquetas.npy | Etiqueta binaria del centro del parche               | int64\[𝑛]           | 0 = No deslizamiento<br>1 = Deslizamiento | SIMMA (puntos de ocurrencia)  |


