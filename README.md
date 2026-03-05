# 📡 Telecom X — Análisis y Predicción de Cancelación de Clientes (Churn)

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.0-150458?style=flat&logo=pandas&logoColor=white)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-1.8-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualización-4C72B0?style=flat)
![Status](https://img.shields.io/badge/Estado-Completado-brightgreen?style=flat)

---

## 📌 Descripción del Proyecto

Este proyecto fue desarrollado como parte de un desafío de análisis de datos para **Telecom X**, una empresa de telecomunicaciones que enfrenta un problema crítico de cancelación de clientes (**churn**).

El trabajo se divide en **dos partes**:

- **Parte 1 — ETL y EDA:** Extracción, limpieza y análisis exploratorio de los datos para entender el perfil de los clientes que cancelan.
- **Parte 2 — Machine Learning:** Preparación de datos, entrenamiento de modelos predictivos y generación de insights estratégicos para reducir el churn.

---

## 🗂️ Estructura del Repositorio

```
telecom-x-churn/
│
├── datos_tratados.csv           # Dataset limpio generado en la Parte 1
├── TelecomX_Part1_EDA.ipynb     # Notebook Parte 1: ETL y Análisis Exploratorio
├── TelecomX_Part2_Final.ipynb   # Notebook Parte 2: Modelado Predictivo
└── README.md
```

---

## 🔧 Parte 1 — ETL y Análisis Exploratorio (EDA)

### Objetivos
- Extraer y cargar los datos crudos desde la fuente original.
- Limpiar el dataset: valores nulos, duplicados, tipos de datos incorrectos.
- Estandarizar nombres de columnas y valores categóricos.
- Analizar el perfil de los clientes que cancelan mediante visualizaciones.

### Principales Hallazgos del EDA

| Factor | Observación |
|---|---|
| **Antigüedad** | Los clientes con menor permanencia tienen mayor tasa de churn |
| **Tipo de contrato** | Los contratos mensuales concentran la mayor cantidad de cancelaciones |
| **Cargo mensual** | Los clientes que cancelan tienden a tener cargos más elevados |
| **Demografía** | Clientes sin pareja ni dependientes muestran mayor inestabilidad |

---

## 🤖 Parte 2 — Predicción de Churn con Machine Learning

### Pipeline Completo

```
Carga de datos tratados
        ↓
Limpieza y encoding (One-Hot)
        ↓
Verificación del balance de clases
        ↓
Train / Test Split (80/20 estratificado)
        ↓
Normalización (StandardScaler para LR)
        ↓
Entrenamiento de modelos
        ↓
Evaluación y comparación
        ↓
Interpretación de variables + Conclusiones
```

### 📊 Resultados de los Modelos

| Modelo | Accuracy | Precision | Recall | F1-Score | Train Acc. |
|---|:---:|:---:|:---:|:---:|:---:|
| **Regresión Logística** | 0.801 | 0.656 | **0.529** | **0.586** | 0.808 |
| Random Forest | 0.788 | 0.636 | 0.468 | 0.539 | 0.998 |

> ✅ **Modelo seleccionado para producción: Regresión Logística.**
> Logra mejor Recall y F1-Score sin presentar overfitting (Train ≈ Test).
> El Random Forest muestra sobreajuste evidente (Train 99.8% vs Test 78.8%).

---

## 🔍 Variables Más Influyentes

Tres métodos coinciden en los mismos factores determinantes:

| Variable | Correlación | Coef. LR | Import. RF | Efecto |
|---|:---:|:---:|:---:|:---:|
| `Antiguedad_Meses` | −0.35 | −1.32 | 15.7% | ↓ Reduce churn |
| `Contract_Two year` | — | −0.57 | 5.4% | ↓ Reduce churn |
| `InternetService_Fiber optic` | — | +0.64 | 3.5% | ↑ Aumenta churn |
| `Cargo_Total` | — | +0.62 | 17.0% | ↑ Aumenta churn |
| `Cargo_Mensual` | +0.19 | — | 14.0% | ↑ Aumenta churn |
| `Metodo_Pago_Electronic check` | — | +0.17 | 4.1% | ↑ Aumenta churn |

---

## 💡 Estrategias de Retención Propuestas

### 🎯 1. Programa de Acompañamiento para Clientes Nuevos
Los primeros meses son el período de mayor riesgo de abandono.
- Descuentos progresivos durante los primeros 6–12 meses.
- Onboarding activo: seguimiento personalizado, soporte prioritario.
- Activación de campañas proactivas basadas en el score del modelo.

### 💰 2. Revisión de la Propuesta de Valor en Fibra Óptica
Los clientes con fibra óptica presentan mayor probabilidad de churn, posiblemente por percepción de costo elevado.
- Ofrecer planes combinados con mayor valor percibido.
- Benchmarking de precios frente a la competencia.

### 📄 3. Incentivos para Contratos de Largo Plazo
Los contratos mensuales concentran el mayor riesgo.
- Descuentos por contrato anual o bianual (ej. 2 meses bonificados).
- Beneficios exclusivos por permanencia: upgrades, soporte premium.

### 📊 4. Implementación del Modelo en Producción
- Scoring mensual de clientes con la Regresión Logística.
- Umbral de riesgo sugerido: probabilidad de churn > 0.60.
- Ciclo de monitoreo y reentrenamiento trimestral.

---

## 🛠️ Tecnologías Utilizadas

| Librería | Uso |
|---|---|
| `pandas` | Manipulación y análisis de datos |
| `numpy` | Operaciones numéricas |
| `matplotlib` / `seaborn` | Visualizaciones |
| `scikit-learn` | Modelos, métricas y preprocesamiento |

---

## ▶️ Cómo Ejecutar el Proyecto

1. Clonar el repositorio:
```bash
git clone https://github.com/ernes2111/Challenge-Telecom-X-part2.git
cd Challenge-Telecom-X-part2
```

2. Instalar dependencias:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

3. Ejecutar los notebooks en orden:
   - `TelecomX_LATAM.ipynb`
   - `TelecomX_Part2_Final.ipynb`

---

## 📝 Conclusión

La cancelación de clientes en Telecom X está **fuertemente determinada por la antigüedad del cliente, el tipo de contrato y el nivel de gasto mensual**. Los modelos desarrollados permiten anticipar con buena capacidad qué clientes presentan mayor riesgo, brindando una herramienta estratégica para implementar acciones preventivas y mejorar la retención.

La aplicación práctica de este pipeline puede generar un impacto directo en la reducción del churn y en la mejora del **Customer Lifetime Value (CLV)** de Telecom X.

---
