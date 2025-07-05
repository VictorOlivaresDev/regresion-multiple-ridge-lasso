# Predicción de Emisiones de CO2 con Regresión Múltiple, Ridge y Lasso

## 📝 Descripción del Proyecto

Este proyecto se enfoca en predecir las emisiones de dióxido de carbono (CO2) de vehículos utilizando diversas características de los mismos, como el tamaño del motor, el número de cilindros y el consumo de combustible. Se implementan y comparan tres modelos de regresión lineal para determinar cuál ofrece la predicción más precisa: Regresión Lineal Múltiple, Regresión Ridge con validación cruzada y Regresión Lasso con validación cruzada.

---

## 📊 Datos Utilizados

El conjunto de datos utilizado es `FuelConsumptionCo2.xlsx`, que contiene información sobre el consumo de combustible y las emisiones de CO2 de diferentes modelos de vehículos del año 2022.

### **Características Relevantes**

Para el modelado, se utilizaron las siguientes características numéricas:

- `ENGINESIZE`: Tamaño del motor.
- `CYLINDERS`: Número de cilindros.
- `FUELCONSUMPTION_CITY`: Consumo de combustible en ciudad (L/100 km).
- `FUELCONSUMPTION_HWY`: Consumo de combustible en carretera (L/100 km).
- `FUELCONSUMPTION_COMB`: Consumo de combustible combinado (L/100 km).
- `FUELCONSUMPTION_COMB_MPG`: Consumo de combustible combinado (millas por galón).

La variable objetivo a predecir es:

- `CO2EMISSIONS`: Emisiones de CO2 (g/km).

---

## 🛠️ Técnicas y Metodología

El enfoque metodológico del proyecto se puede resumir en los siguientes pasos:

### **1. Preprocesamiento de Datos**

-
