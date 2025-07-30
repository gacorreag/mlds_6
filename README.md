# Predicción de Susceptibilidad a Deslizamientos en la Zona Cafetera

<div align="center">
    <img src="public/Logo_SCM.jpg" alt="Logo" width="180" />
</div>

## 🌄 Hackatón Cafetera 2025 — Equipo Support Coffee Machine

**Proyecto de inteligencia artificial para la mitigación del riesgo por deslizamientos en el Eje Cafetero de Colombia.**

---

### ¿En qué consiste nuestro reto?

Desarrollamos una solución basada en Deep Learning y datos geoespaciales para predecir zonas susceptibles a deslizamientos en áreas cafeteras. El objetivo es apoyar la toma de decisiones y la prevención de desastres en comunidades rurales y productoras de café.

- **¿Por qué es importante?**
  - Los deslizamientos afectan vidas, infraestructura y la economía cafetera.
  - Anticipar zonas de riesgo permite actuar antes y proteger a las familias y cultivos.

---

### ¿Cómo lo hicimos?

- **Integración de datos ambientales y geológicos** (pendiente, vegetación, precipitación, geología, etc.)
- **Procesamiento y alineación de datos ráster** para crear un stack multibanda homogéneo.
- **Extracción de cubos de datos** centrados en zonas con y sin deslizamiento histórico.
- **Entrenamiento de una red neuronal convolucional (CNN)** para identificar patrones de riesgo.
- **Evaluación y ajuste** para lograr un modelo robusto y generalizable.

> **Resultado:** El modelo predice con un 76% de precisión las zonas susceptibles, superando ampliamente los métodos tradicionales.

---

### ¿Qué impacto tiene?

- Permite **mapear zonas críticas** y priorizar acciones de prevención.
- Facilita la **planificación territorial** y la gestión del riesgo en la caficultura.
- Es una herramienta **escalable** a otras regiones y adaptable a nuevos datos.

---

### Demo interactiva

La visualización y exploración de resultados se realiza en una app web interactiva construida con **Streamlit**, que permite navegar el mapa de susceptibilidad, consultar estadísticas y descargar información relevante.

---


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

### Equipo de trabajo


- **David Granados**
- **Gabriela Correa**
- **Iván Sotelo**
- **Juan Martínez**
- **Juan Mosquera**
- **Kevin Murillo**



---

### Presentaciones y recursos

<div align="center">
    <a href="https://drive.google.com/file/d/1WkZqU_FvzwcvztASg2qDHuQEVAGA2-rX/view?usp=drive_link">
        <img src="https://img.icons8.com/ios-filled/100/FFFFFF/video.png" alt="🎥 Ver el Video" />
    </a>
    &nbsp;&nbsp;&nbsp;&nbsp;
    <a href="https://www.canva.com/design/DAGspkveOAg/dUBalb3yPo_Iaznoo7DBlw/view?utm_content=DAGspkveOAg&utm_campaign=designshare&utm_medium=link2&utm_source=uniquelinks&utlId=h28d4018f55">
        <img src="https://img.icons8.com/ios-filled/100/FFFFFF/presentation.png" alt="📑 Ver la Presentación" />
    </a>
</div>

- [Enlace a todos los recursos y resultados (Drive)](https://drive.google.com/drive/folders/19IrDKVTtjPZG48GnoWkf8Fudcyu_2aCI?usp=drive_link)

---

<sub>Desarrollado por el equipo Support Cofee Machine para la Hackatón Cafetera 2025. App web construida en Streamlit. Contacto y detalles en la presentación.</sub>

