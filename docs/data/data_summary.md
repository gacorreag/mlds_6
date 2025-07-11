Mostrar siempre los detalles

Copiar
from IPython.display import Markdown

reporte = """
# 🧾 Reporte de Datos

Este documento contiene los resultados del análisis exploratorio de datos del modelo de susceptibilidad a deslizamientos basado en imágenes ráster y etiquetas asociadas.

---

## 📌 Resumen general de los datos

- **Número de observaciones:** 851
- **Número de variables (características por píxel):** 1353
- **Tipo de variables:** 
  - Continuas (pendiente, NDVI, precipitación, distancia a fallas, DEM, TWI)
  - Categóricas codificadas (geología, TWI clasificado)
- **Variables por banda (stack multibanda de 8 bandas):**
  - Banda 1: Pendiente
  - Banda 2: TRI
  - Banda 3: DEM
  - Banda 4: Distancia a fallas
  - Banda 5: NDVI
  - Banda 6: Precipitación
  - Banda 7: Geología
  - Banda 8: TWI clasificado
- **Presencia de valores faltantes:** No se encontraron valores nulos o vacíos.
- **Distribución inicial:** Las variables presentan distintas escalas, fueron normalizadas para análisis exploratorios posteriores.

---

## ✅ Resumen de calidad de los datos

- **Valores faltantes:** 0 columnas con valores nulos.
- **Duplicados:** Se identificaron 19 duplicados exactos (2.23% del total).
- **Valores extremos:** Más de 100 columnas presentaron outliers >5% (concentrados especialmente en elevación y NDVI). Estos se visualizaron mediante boxplots.
- **Errores:** La banda TRI muestra valores corruptos o erráticos (rango desde -3.4e+38 hasta 259.7). Fue identificada como variable potencialmente problemática.
- **Acciones tomadas:**
  - Se escalaron y normalizaron los datos.
  - Se documentó la anomalía en TRI para su posible exclusión o tratamiento posterior.

<img width="1322" height="262" alt="image" src="https://github.com/user-attachments/assets/44e16c31-fe98-45b5-a142-4da975ae4e70" />


---

## 🎯 Variable objetivo

- **Tipo:** Variable binaria (0 = No deslizamiento, 1 = Deslizamiento)
- **Distribución:**
  - No deslizamiento: 404 observaciones
  - Deslizamiento: 447 observaciones
  - Distribución balanceada (~50/50)
- **Visualización:** Se graficó la frecuencia de cada clase y se analizaron las métricas de clasificación (precision, recall, f1-score) para evaluar la calidad predictiva del modelo.

<img width="1318" height="551" alt="image" src="https://github.com/user-attachments/assets/663f322f-c742-44cc-8e00-bc8e134f3af1" />

---

## 📊 Variables individuales

Se analizaron estadísticamente las 8 bandas del stack ráster:

- **Pendiente:** Alta dispersión. Ligera correlación positiva con el DEM. Alta importancia en modelos predictivos.
- **TRI:** Presencia de valores anómalos. Débil correlación con otras variables. Considerar imputación o exclusión.
- **DEM:** Elevación hasta 5287 m. Correlación inversa fuerte con NDVI (-0.71).
- **Distancia a fallas:** Baja correlación con todas las variables, lo cual es valioso como predictor independiente.
- **NDVI:** Rango normalizado, correlacionado con precipitación (0.37). Relacionado con cobertura vegetal.
- **Precipitación:** Aporta señal adicional, correlacionada con NDVI.
- **Geología:** Variable categórica, importante en la clasificación.
- **TWI clasificado:** Baja correlación, pero contiene información única.

---

## 🏅 Ranking de variables

Se utilizó Random Forest, PCA y correlación para identificar las variables más relevantes:

| Banda | Variable original | Grado de importancia |
|-------|-------------------|----------------------|
| 0     | Pendiente         | Muy alta             |
| 1     | TRI               | Baja / problemática  |
| 2     | DEM               | Alta                 |
| 3     | Distancia a fallas| Media                |
| 4     | NDVI              | Alta                 |
| 5     | Precipitación     | Media-Alta           |
| 6     | Geología          | Media                |
| 7     | TWI Clasificado   | Media-Baja           |

- **PCA:** Los primeros 5 componentes explican la mayor varianza.
- **Correlación con variable objetivo:** Se identificaron múltiples variables con r > 0.25 como predictoras útiles.

<img width="1316" height="432" alt="image" src="https://github.com/user-attachments/assets/dced7770-1d69-4fdc-9856-1d2b0f1e2950" />

---

## 🔁 Relación entre variables explicativas y variable objetivo

- **Matriz de correlación:** Se calculó la correlación entre cada variable y la variable objetivo. Las más relacionadas superan r = 0.3.
- **Diagrama de dispersión (resumen):** Mostró que valores de pendiente, NDVI y DEM tienden a diferenciar zonas con deslizamiento.
- **Regresión lineal (opcional):** Permitió evidenciar tendencias, aunque la relación no es completamente lineal.
- **Correlación entre bandas del raster:** DEM y NDVI tienen alta correlación inversa. Geología y TWI muestran independencia.
  
<img width="695" height="589" alt="image" src="https://github.com/user-attachments/assets/52599430-6805-4169-9c92-6cde746ff93f" />

---

**Conclusión:** El análisis exploratorio permitió identificar la calidad de los datos, variables relevantes y redundantes, y proporciona evidencia sólida para el entrenamiento y ajuste de modelos predictivos de deslizamientos.
"""

En esta sección se presenta un análisis de la relación entre las variables explicativas y la variable objetivo. Se utilizan gráficos como la matriz de correlación y el diagrama de dispersión para entender mejor la relación entre las variables. Además, se pueden utilizar técnicas como la regresión lineal para modelar la relación entre las variables.
