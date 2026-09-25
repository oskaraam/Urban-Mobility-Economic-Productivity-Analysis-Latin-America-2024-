# 🌎 Análisis de Movilidad Urbana y Productividad Económica — América Latina (2024)

## 🎯 Objetivo del Proyecto

Evaluar cómo **la movilidad urbana se relaciona con la productividad económica** en las principales ciudades de América Latina utilizando datos reales de **TomTom Traffic Index** y **OECD Cities**. El objetivo es identificar qué ciudades se beneficiarían más de la inversión en infraestructura de transporte.

---

## 📂 Datasets Utilizados

| Archivo | Descripción |
|---|---|
| `tomtom_traffic.csv` | Datos de tráfico histórico y en tiempo real por ciudad (congestión, tiempos de viaje, conteo de embotellamientos) |
| `oecd_city_economy.csv` | Indicadores económicos por ciudad (PIB per cápita, desempleo, población, PM2.5) |

---

## 🧩 Etapas del Análisis

1. **Cargar y explorar** — Cargar ambos datasets, inspeccionar la estructura, tipos de datos y primeras filas.
2. **Limpiar y preparar datos** — Corregir formatos de fecha, ajustar separadores numéricos, estandarizar nombres de columnas a `snake_case` y gestionar conversiones de tipo.
3. **Extraer año y filtrar** — Extraer el año de las marcas de tiempo y filtrar registros únicamente para el 2024 utilizando `.copy()` para preservar los originales.
4. **Agregar datos de movilidad** — Agrupar datos de tráfico por `city`, `country` y `year`, calculando promedios para métricas clave (retraso por embotellamientos, tiempos de viaje, conteo de embotellamientos).
5. **Unir datasets (Merge)** — Unir (inner join) los datos de tráfico y economía en función de `city` y `year` para conservar solo las ciudades presentes en ambas fuentes.
6. **Visualizar relaciones** — Diagrama de caja (boxplot) para la distribución del tráfico, histograma para el PIB per cápita y gráfico de barras comparativo.
7. **Exportar y documentar** — Exportar el dataset final limpio y redactar un resumen ejecutivo con hallazgos y recomendaciones.

---

## 🔁 Guía de Reproducción

1. Colocar ambos archivos CSV en el directorio `/datasets/`
2. Ejecutar las celdas **en orden secuencial** — cada paso depende del anterior
3. DataFrames clave creados a lo largo del cuaderno:

| Variable | Contenido |
|---|---|
| `traffic` | Datos crudos de tráfico (+1M de filas) |
| `eco` | Indicadores económicos por ciudad |
| `traffic_2024` | Datos de tráfico filtrados para el año 2024 |
| `eco_2024` | Datos económicos filtrados para el año 2024 |
| `traffic_city_year_2024` | Métricas promedio de tráfico agregadas por ciudad y año |
| `merged` | Dataset final — inner join de tráfico + economía |

4. El dataset final limpio se exporta como `ladb_mobility_economy_2024_clean.csv`

---

## 🛠️ Librerías Requeridas

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
