# 📈 Análisis y pronóstico del precio del dólar mediante modelos de series de tiempo

## Descripción general

Este proyecto analiza la evolución del **precio de cierre del dólar estadounidense** a partir de una serie histórica diaria, utilizando técnicas de **análisis de series de tiempo** y **modelos estadísticos clásicos**. El estudio se enfoca en comprender la dinámica temporal del tipo de cambio, evaluar sus propiedades estadísticas y generar **pronósticos a corto plazo**.

El análisis se basa en datos financieros reales comprendidos entre **2012 y 2025**, los cuales reflejan distintos contextos económicos, incluyendo periodos de estabilidad y alta volatilidad. A partir de este conjunto de datos, se estudian características como **no estacionariedad, autocorrelación y volatilidad**, propias de las series financieras.

El objetivo principal es **comparar el desempeño de modelos ARMA, ARIMA y SARIMA** para determinar cuál describe mejor el comportamiento del precio del dólar y ofrece mayor precisión predictiva en el corto plazo.

El problema se aborda desde un enfoque de **modelado estadístico para series de tiempo**, considerando tanto la serie completa como un segmento específico con comportamiento más estable.

---

## Objetivos

- Analizar el comportamiento temporal del precio de cierre del dólar.
- Evaluar la estacionariedad, autocorrelación y volatilidad de la serie.
- Aplicar técnicas exploratorias como medias móviles y descomposición en componentes.
- Implementar modelos ARMA, ARIMA y SARIMA para el pronóstico del tipo de cambio.
- Comparar los modelos mediante métricas de error y diagnóstico de residuos.
- Identificar el modelo con mejor desempeño predictivo a corto plazo.

---

## Dataset

El conjunto de datos corresponde a una **serie histórica diaria del precio del dólar**, obtenida a partir de un repositorio público y descargada directamente en el entorno de trabajo para garantizar la reproducibilidad del análisis.

**Características del dataset:**

- Periodo: enero de 2012 – septiembre de 2025  
- Observaciones: 3,585  
- Frecuencia: diaria (días hábiles)  
- Variable utilizada:
  - `Cierre`: precio de cierre diario del dólar  

Aunque el archivo original contiene variables adicionales (apertura, máximo, mínimo, volumen y variación porcentual), el análisis se centra exclusivamente en el **precio de cierre**, por ser el indicador más representativo del comportamiento del mercado.

---

## Metodología y modelos implementados

### 1. Preprocesamiento y análisis exploratorio (EDA)

- Conversión de la variable fecha a formato `datetime`.
- Selección de la variable de interés (precio de cierre).
- Verificación de valores faltantes.
- Visualización de la serie de tiempo completa.
- Cálculo de media y varianza móviles.
- Descomposición aditiva en tendencia, estacionalidad y residuos.
- Análisis de volatilidad mediante modelos ARCH.
- Evaluación de autocorrelación (ACF, PACF y mapas de calor).
- Pruebas estadísticas:
  - Dickey-Fuller Aumentada (ADF)
  - Ljung-Box

---

### 2. Segmento seleccionado para modelado: año 2015

Con el fin de reducir la complejidad del problema y trabajar con un periodo más homogéneo, se seleccionó el **año 2015**, el cual presenta:

- Menor volatilidad relativa.
- Ausencia de picos extremos.
- Dinámica más estable y regular.

Este segmento permite un análisis más controlado y facilita el cumplimiento de los supuestos de los modelos clásicos de series de tiempo.

---

### 3. Transformaciones

- Aplicación de **diferenciación de primer orden** para eliminar la tendencia.
- Verificación de estacionariedad posterior mediante la prueba ADF.
- Confirmación de estacionariedad en la serie diferenciada.

---

### 4. Modelos de series de tiempo

#### 4.1 Modelo ARMA(2,1)

- Ajustado sobre la serie diferenciada.
- Buen diagnóstico de residuos (ruido blanco).
- Buen desempeño en validación cruzada.
- Limitación: interpretación en términos de variaciones y no en niveles del precio.

#### 4.2 Modelo ARIMA(2,1,1)

- Ajustado sobre la serie original.
- Excelente diagnóstico de residuos.
- Mayor error predictivo relativo en comparación con otros modelos.

#### 4.3 Modelo SARIMA(1,1,0)(0,1,1,5)

- Incorporación de estacionalidad semanal (5 días hábiles).
- Mejor desempeño en términos de MAPE.
- Mayor precisión en el pronóstico a corto plazo.
- Presencia de ligera autocorrelación residual.

---

## Resultados principales

- El modelo **SARIMA(1,1,0)(0,1,1,5)** obtuvo el **menor error porcentual (MAPE)**.
- La incorporación de un componente estacional mejoró la capacidad predictiva.
- ARMA mostró excelente ajuste estadístico, pero menor aplicabilidad práctica.
- ARIMA presentó un diagnóstico sólido, aunque con menor precisión predictiva.

---

## Estructura del repositorio

```text
├── data/               # Dataset utilizado
├── notebooks/          # Análisis en Google Colab
├── figures/            # Gráficas y visualizaciones
├── report/             # Documento final del proyecto
└── README.md           # Descripción general del proyecto
```
###Requisitos

Para ejecutar el proyecto se requiere:

-Python 3.8 o superior

Librerías:

- pandas
- numpy
- matplotlib
- seaborn
- statsmodels
- scipy

###Notebook

El análisis completo se encuentra disponible en Google Colab:

🔗 [https://colab.research.google.com/drive/1YXY3tVxsqeWnNa-h1d4Wpjy8g9oSR48L?usp=sharing]

Autores:
Sharon Xolocotzi Castillo

Proyecto académico – Análisis de Series de Tiempo
Licenciatura en Ciencia de Datos
Escuela Superior de Cómputo (ESCOM – IPN)
