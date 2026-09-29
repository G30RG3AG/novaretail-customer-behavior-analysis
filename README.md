# 📊 NovaRetail+ Customer Behavior Analysis

Proyecto de análisis exploratorio de datos desarrollado como parte del **Sprint 8 del Bootcamp de Data Analyst**, enfocado en identificar relaciones entre el comportamiento de los clientes y su impacto económico dentro de **NovaRetail+**.

El análisis utiliza técnicas estadísticas, visualizaciones y diferentes coeficientes de asociación para estudiar variables relacionadas con compras, visitas, publicidad, satisfacción, membresía premium, abandono e ingreso generado por cliente.

---

## 🎯 Objetivo del proyecto

Analizar los principales factores asociados con el comportamiento de los clientes de NovaRetail+ y evaluar su relación con la métrica principal del proyecto:

`ingreso_anual`

El proyecto busca identificar patrones que permitan comprender mejor:

- La relación entre frecuencia de compra e ingreso.
- La relación entre visitas y comportamiento de compra.
- El impacto asociado a la publicidad dirigida.
- Las diferencias entre clientes premium y no premium.
- La relación entre características categóricas y abandono.
- Posibles variables relevantes para futuros modelos predictivos.

---

## 📁 Dataset

**Archivo utilizado:**

`novaretail_comportamiento_clientes_2024.csv`

El conjunto de datos contiene:

- **15,000 registros**
- **12 variables**
- Sin valores nulos detectados durante la exploración inicial.

### Variables principales

| Variable | Descripción |
|---|---|
| `id_cliente` | Identificador único del cliente |
| `edad` | Edad del cliente |
| `nivel_ingreso` | Ingreso estimado del cliente |
| `visitas_mes` | Número de visitas mensuales |
| `compras_mes` | Número de compras realizadas durante el mes |
| `gasto_publicidad_dirigida` | Gasto publicitario asignado al cliente |
| `satisfaccion` | Nivel de satisfacción del cliente |
| `miembro_premium` | Indica si el cliente tiene membresía premium |
| `abandono` | Indica si el cliente abandonó la plataforma |
| `tipo_dispositivo` | Dispositivo utilizado por el cliente |
| `region` | Región geográfica |
| `ingreso_anual` | Ingreso anual generado por el cliente |

---

## 🛠️ Tecnologías utilizadas

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- SciPy
- Jupyter Notebook

---

## 🔎 Etapas del análisis

### 1. Exploración inicial

Se realizó una revisión general del dataset mediante:

- `df.info()`
- `df.head()`
- estadísticas descriptivas
- identificación de variables numéricas
- identificación de variables binarias
- análisis de variables categóricas

También se corrigió el tipo de dato de la variable `edad`, convirtiéndola a un tipo entero.

---

### 2. Análisis descriptivo

Se analizaron las principales características de las variables numéricas.

Algunos resultados relevantes:

- La edad promedio de los clientes es de aproximadamente **38 años**.
- El promedio de compras mensuales es de aproximadamente **1.21 compras**.
- Al menos el 25% de los clientes registra **0 compras mensuales**.
- El ingreso anual presenta una mayor dispersión y posibles valores extremos.
- La satisfacción promedio se encuentra alrededor de **3.6 sobre 5**.

---

## 📈 Análisis de correlación

Se construyó una matriz de correlación para identificar relaciones entre variables numéricas.

Entre las relaciones más relevantes se encontraron:

| Variables | Correlación aproximada |
|---|---:|
| `compras_mes` vs `ingreso_anual` | **0.97** |
| `visitas_mes` vs `gasto_publicidad_dirigida` | **0.58** |
| `visitas_mes` vs `compras_mes` | **0.35** |
| `visitas_mes` vs `ingreso_anual` | **0.34** |

La relación más fuerte se presentó entre el número de compras mensuales y el ingreso anual generado por el cliente.

---

## 📊 Pearson y Spearman

Se calcularon los coeficientes de Pearson y Spearman para evaluar tanto relaciones lineales como relaciones monótonas.

### `compras_mes` vs `ingreso_anual`

- Pearson: **0.967**
- Spearman: **0.967**

Se observa una asociación positiva muy fuerte y consistente.

### `visitas_mes` vs `gasto_publicidad_dirigida`

- Pearson: **0.579**
- Spearman: **0.559**

La relación es positiva y de magnitud moderada.

### `visitas_mes` vs `compras_mes`

- Pearson: **0.354**
- Spearman: **0.333**

La asociación es positiva, aunque considerablemente más débil.

### `visitas_mes` vs `ingreso_anual`

- Pearson: **0.337**
- Spearman: **0.321**

Se observa una asociación positiva débil a moderada.

---

## 🔵 Correlación punto-biserial

Se utilizó la correlación punto-biserial para estudiar variables binarias frente a `ingreso_anual`.

### `miembro_premium` vs `ingreso_anual`

- Coeficiente: **0.093**
- `p-value`: aproximadamente **0**

Existe una asociación positiva estadísticamente significativa, aunque de magnitud débil.

### `abandono` vs `ingreso_anual`

- Coeficiente: **-0.003**
- `p-value`: **0.72947**

No se encontró una asociación relevante entre abandono e ingreso anual.

---

## 🧩 V de Cramér

Para analizar asociaciones entre variables categóricas se utilizó **V de Cramér**.

| Variables | V de Cramér |
|---|---:|
| `tipo_dispositivo` vs `region` | 0.012 |
| `tipo_dispositivo` vs `miembro_premium` | 0.020 |
| `tipo_dispositivo` vs `abandono` | 0.007 |
| `region` vs `miembro_premium` | 0.013 |
| `region` vs `abandono` | 0.015 |
| `miembro_premium` vs `abandono` | **0.120** |

En general, las asociaciones entre variables categóricas son débiles.

La relación más alta se presenta entre `miembro_premium` y `abandono`, aunque su magnitud continúa siendo baja.

---

## 💡 Principales hallazgos

### 1. Compras mensuales e ingreso anual

La relación entre `compras_mes` e `ingreso_anual` presenta una correlación de aproximadamente **0.967**.

Esto indica que los clientes que realizan más compras mensuales tienden a generar mayores ingresos para NovaRetail+.

Esta asociación es uno de los resultados más relevantes del análisis.

> La correlación encontrada no implica causalidad.

---

### 2. Membresía premium y abandono

Se identificó una relación negativa débil entre `miembro_premium` y `abandono`.

El V de Cramér entre ambas variables fue de aproximadamente **0.120**.

Esto indica que existe cierta asociación entre la membresía premium y el comportamiento de abandono, aunque su intensidad es baja.

La membresía premium podría utilizarse como una variable complementaria en futuros análisis de retención.

---

## ⚠️ Limitaciones

- Correlación no implica causalidad.
- El análisis se basa en un único conjunto de datos.
- Algunas asociaciones estadísticamente significativas tienen una magnitud pequeña.
- Existen posibles valores extremos en variables como `ingreso_anual`.
- El análisis realizado es principalmente bivariado.
- Pueden existir variables externas no incluidas en el dataset que influyan en el comportamiento de los clientes.

---

## 🚀 Próximos pasos

Como continuación del proyecto se propone:

- Segmentar clientes según su frecuencia de compra.
- Comparar clientes premium y no premium.
- Analizar grupos por región y tipo de dispositivo.
- Investigar posibles outliers mediante boxplots e histogramas.
- Crear segmentos de clientes de alto, medio y bajo valor.
- Construir un modelo de regresión para estimar `ingreso_anual`.
- Desarrollar un modelo de clasificación para analizar el riesgo de `abandono`.

---

## 📌 Conclusión

El análisis permitió identificar que la variable con mayor asociación con el ingreso generado por los clientes es `compras_mes`.

También se encontraron relaciones moderadas entre visitas, compras y gasto publicitario, mientras que las variables categóricas mostraron asociaciones considerablemente más débiles.

Estos resultados permiten establecer una base para futuros análisis de segmentación y modelos predictivos orientados a mejorar la comprensión del comportamiento de los clientes y apoyar decisiones de negocio en NovaRetail+.

---

## 👨‍💻 Autor

**Jorge Yahir Bedolla Aguilar**

Proyecto desarrollado como parte de mi formación en **Data Analytics**, aplicando Python, análisis exploratorio de datos, visualización y técnicas estadísticas para obtener insights a partir de información de clientes.
