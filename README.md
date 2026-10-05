# telecom-analysis
# 📊 Análisis Exploratorio de Datos (EDA) y Segmentación de Clientes - ConnectaTel

## 🎯 Objetivo del Proyecto
El objetivo principal de este proyecto es llevar a cabo un **Análisis Exploratorio de Datos (EDA)** exhaustivo y desarrollar un **modelo de segmentación de clientes** para la compañía de telecomunicaciones **ConnectaTel**. 

A través del procesamiento, limpieza y análisis del comportamiento de consumo y datos demográficos de los usuarios, se buscan identificar patrones de uso, evaluar anomalías en los datos y generar **insights estratégicos orientados al negocio** para optimizar la oferta comercial, diseñar estrategias de *upselling* y mejorar la retención de clientes.

---

## 📁 Datasets Utilizados

* **`user` (Perfil de Usuarios):** Contiene la información demográfica y de registro de los clientes de ConnectaTel (como edad y ciudad de residencia), permitiendo caracterizar la base de usuarios y segmentarla por rangos etarios.
* **`usage` (Consumo de Servicios):** Registra la actividad operativa de los clientes en la red, detallando el volumen de llamadas realizadas, los minutos acumulados de conversación y la cantidad de mensajes de texto enviados.
* **`plans` (Oferta Comercial):** Define las tarifas, límites de consumo y condiciones comerciales de los planes ofertados, sirviendo como marco de referencia para evaluar la rentabilidad y el comportamiento de los clientes frente a sus cuotas contratadas.
---

## 🛠️ Etapas del Análisis

### 1. Diagnóstico y Calidad de Datos
* **Identificación de Anomalías:** Se detectó el valor `-999` en la columna `age` como un error de captura de sistema (afectando a menos del 1% del dataset). Se decidió aislar e ignorar estos valores en los cálculos de edad para no distorsionar las métricas demográficas.
* **Normalización de Faltantes:** Se reemplazaron caracteres comodín (como `?` en la variable `city`) por valores nulos reales (`np.nan`) utilizando herramientas nativas de `pandas` para garantizar la integridad analítica.

### 2. Análisis Exploratorio de Consumo (EDA) y Outliers
* Evaluación de métricas numéricas de consumo mediante el Rango Intercuartílico (IQR).
* **Tratamiento de Outliers:** Se identificaron *heavy users* con consumos extremos (p. ej., hasta 155.7 minutos de llamada o volúmenes altos de mensajes). Se determinó **mantener todos los outliers** por representar comportamiento comercial auténtico y clave para la retención de clientes de alto valor.

### 3. Ingeniería de Características y Segmentación
Se crearon dos nuevas variables categóricas mediante lógica condicional anidada (`apply`):
* **`grupo_uso`:** Clasificación en *Bajo uso*, *Uso medio* y *Alto uso* según umbrales de llamadas y mensajes (<5 y <10).
* **`grupo_edad`:** Clasificación en *Joven* (<30 años), *Adulto* (<60 años) y *Adulto Mayor* (≥60 años).

### 4. Visualización e Insights Ejecutivos
* Construcción de gráficos de distribución (`countplot` con `seaborn` y `matplotlib`) para analizar el volumen de cada segmento.
* Análisis cruzado de patrones de uso y perfil demográfico para derivar recomendaciones estratégicas de negocio.

---

## 🚀 Cómo Ejecutar el Notebook

### Opción 1: Google Colab (Recomendado)
1. Abre [Google Colab](https://colab.research.google.com/).
2. Selecciona la pestaña **GitHub** e ingresa la URL de este repositorio.
3. Abre el archivo `.ipynb` correspondiente.
4. Ejecuta las celdas en orden (`Shift + Enter`) o selecciona `Entorno de ejecución > Ejecutar todas`.

### Opción 2: Entorno Local (Jupyter / VS Code)
1. Clona el repositorio:
   ```bash
   git clone [https://github.com/tu-usuario/connectatel-eda-segmentacion.git](https://github.com/tu-usuario/connectatel-eda-segmentacion.git)
   cd connectatel-eda-segmentacion
