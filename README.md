# PREDICCIÓN DE FALLOS EN EQUIPOS USANDO APRENDIZAJE SUPERVISADO TEMPORAL

## Contexto del Problema

En muchas industrias (minería, manufactura, energía, logística), los equipos operan de manera continua y se van degradando progresivamente hasta que ocurre una falla.  
Las fallas no planificadas generan altos costos por paradas de operación, riesgos de seguridad y mantenimiento correctivo de emergencia.

La pregunta de negocio que se aborda en este proyecto es:

**¿Es posible anticipar el riesgo de falla de un equipo con suficiente anticipación para tomar acciones preventivas?**

En lugar de predecir el momento exacto de la falla, este proyecto se enfoca en **predecir la probabilidad de que un equipo falle dentro de una ventana futura de tiempo**, lo cual resulta mucho más accionable para la toma de decisiones.

---

## Objetivo

Construir un **modelo de aprendizaje supervisado con estructura temporal** que permita predecir si un equipo tiene **alto riesgo de fallar en los próximos _N_ ciclos**, utilizando únicamente información histórica disponible hasta un determinado momento.

Este enfoque es generalizable a otros problemas de negocio como:
- Predicción de churn de clientes  
- Riesgo de default crediticio  
- Riesgo de obsolescencia de inventario  
- Mantenimiento predictivo  

---

## Enfoque de Modelado

Cada observación del modelo representa:

> **ID del equipo + tiempo (ciclo) → riesgo de falla futuro**

Principios clave del enfoque:
- Las variables (features) se construyen usando **ventanas históricas** (pasado)
- El target se define mirando una **ventana futura**
- La separación de entrenamiento y prueba es **temporal**, no aleatoria
- Se prioriza la **interpretabilidad y la conexión con decisiones de negocio**

---

## Dataset

Este proyecto utiliza el dataset **NASA Turbofan Engine Degradation Simulation (CMAPSS)**.

Características principales:
- Múltiples motores (equipos) operando a lo largo del tiempo
- Mediciones de sensores en cada ciclo de operación
- Trayectorias completas hasta la falla del equipo

El dataset permite simular escenarios reales donde la condición del equipo se deteriora progresivamente.

---

## Definición del Target

El problema se formula como una **clasificación binaria**:

- `1`: El equipo fallará dentro de los próximos _N_ ciclos  
- `0`: El equipo no se espera que falle dentro de ese horizonte  

Este tipo de salida permite apoyar decisiones como:
- Programación de mantenimiento preventivo
- Priorización de inspecciones
- Reducción de paradas no planificadas

---

## Estructura del Repositorio

├── data/
├── notebooks/
│   ├── 01_exploracion_datos.ipynb
│   ├── 02_definicion_target.ipynb
│   ├── 03_feature_engineering.ipynb
│   ├── 04_entrenamiento_modelo.ipynb
│   └── 05_evaluacion.ipynb
├── src/
└── README.md

---

## Propósito del Proyecto

Este repositorio está diseñado como una **implementación de referencia** para quienes deseen aprender a:

- Formular correctamente problemas con estructura temporal
- Definir targets sin incurrir en *data leakage*
- Construir variables relevantes a partir de datos históricos
- Conectar modelos predictivos con decisiones de negocio reales

---

## Nota Importante

Este proyecto **no es un problema clásico de forecasting de series de tiempo**.  
Se trata de un problema de **aprendizaje supervisado con estructura temporal**, donde el tiempo organiza los datos, pero el objetivo es la **clasificación y soporte a la decisión**.

---

## Referencias

- NASA CMAPSS Turbofan Engine Dataset  
- Literatura sobre mantenimiento predictivo y Remaining Useful Life (RUL)
- https://data.nasa.gov/dataset/cmapss-jet-engine-simulated-data

