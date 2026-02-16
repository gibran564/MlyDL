# Practica 1 — Data Wrangling

<div align="center">

![Python](https://img.shields.io/badge/Python-3.13-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completada-10b981?style=for-the-badge)

---

| | |
|---|---|
| **Alumno** | Christian Gibrán Espituñal Villanueva |
| **No. de Control** | 20041243 |
| **Docente** | Dr. José Gabriel Rodríguez Rivas |
| **Asignatura** | Machine Learning y Deep Learning |
| **Unidad** | 1 — Introducción a Machine Learning y Deep Learning |
| **Instituto** | Instituto Tecnológico de Durango |

</div>

---

## Objetivo

Aplicar técnicas básicas de **Data Wrangling** para cargar, explorar, limpiar y transformar un conjunto de datos crudos, con el fin de prepararlo para su posterior análisis y uso en modelos de *Machine Learning* y *Deep Learning*.

El resultado del proceso es un conjunto de datos corregido y estructurado, almacenado en formato CSV.

---

## Conjunto de Datos

| | |
|---|---|
| **Archivo original** | `datasets/AutosDatosSucios.csv` |
| **Archivo procesado** | `datasets/AutosDatosLimpios.csv` |
| **Registros originales** | 205 filas × 26 columnas |
| **Registros finales** | 201 filas × 28 columnas |
| **Dominio** | Información automotriz sin preprocesar |

El dataset contiene especificaciones técnicas y precios de automóviles, con valores faltantes representados como `?` y tipos de datos inconsistentes que requirieron tratamiento previo al análisis.

---

## Contenido del Notebook

El notebook documenta el proceso completo de *Data Wrangling* siguiendo el flujo:

| # | Sección | Descripción |
|---|---------|-------------|
| 1 | Carga y diagnóstico inicial | Inspección de estructura, tipos de datos y calidad general del dataset |
| 2 | Tratamiento de valores faltantes | Imputación vectorizada y eliminación de registros incompletos en `price` |
| 3 | Corrección y normalización de tipos de datos | Conversión explícita a `float` e `int` según la naturaleza de cada variable |
| 4 | Conversión de unidades | Transformación de `city-mpg` y `highway-mpg` a **L/100 km** |
| 5 | Normalización de variables numéricas | Escalado al rango [0, 1] para `length`, `width` y `height` |
| 6 | Discretización de variables continuas | Categorización de `horsepower` en niveles Bajo / Medio / Alto |
| 7 | Codificación de variables categóricas | *One-hot encoding* de la variable `fuel-type` |
| 8 | Almacenamiento del dataset limpio | Exportación a `datasets/AutosDatosLimpios.csv` |

---

## Detalle Tecnico

### Valores faltantes detectados

| Variable | Valores faltantes | Estrategia aplicada |
|----------|------------------|---------------------|
| `normalized-losses` | 41 | Imputación por media |
| `price` | 4 | Eliminación del registro |
| `bore` | 4 | Imputación por media |
| `stroke` | 4 | Imputación por media |
| `horsepower` | 2 | Imputación por media |
| `peak-rpm` | 2 | Imputación por media |
| `num-of-doors` | 2 | Imputación por moda (`four`) |

### Transformaciones aplicadas

**Conversión de unidades**

```
city-L/100km    = 235 / city-mpg
highway-L/100km = 235 / highway-mpg
```

**Normalización (escala 0–1)**

```python
autos[["length", "width", "height"]] /= autos[["length", "width", "height"]].max()
```

**Discretización de horsepower**

```
Bajo   → 153 registros
Medio  →  43 registros
Alto   →   5 registros
```

**Variables dummy generadas**

```
fuel-type_gas    → 181 registros
fuel-type_diesel →  20 registros
```

---

## Librerias Utilizadas

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

---

## Archivos

| Archivo | Descripcion |
|---------|-------------|
| `1_Data_Wrangling.ipynb` | Notebook principal con el desarrollo completo |
| `datasets/AutosDatosSucios.csv` | Dataset original con valores sucios |
| `datasets/AutosDatosLimpios.csv` | Dataset limpio generado al final del proceso |

---

## Ejecucion

```bash
jupyter notebook 1_Data_Wrangling.ipynb
```

---

<div align="center">

*Practica 1 — Unidad 1 | Machine Learning y Deep Learning*

*Instituto Tecnológico de Durango — 2024*

</div>