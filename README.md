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

- **Limpieza de datos:** Se verificó la ausencia de datos nulos en el conjunto de datos.
- **Selección de características:** Se eliminaron las columnas categóricas (`MODELYEAR`, `MAKE`, `MODEL`, `VEHICLECLASS`, `TRANSMISSION`, `FUELTYPE`) para centrarse únicamente en las variables numéricas.

### **2. División del Conjunto de Datos**

Los datos se dividieron en dos subconjuntos para el entrenamiento y la evaluación de los modelos:

- **70% para entrenamiento.**
- **30% para pruebas**.

### **3. Modelado**

Se entrenaron y evaluaron tres modelos de regresión diferentes:

1.  **Regresión Lineal Múltiple:** Un modelo de regresión lineal estándar para establecer una línea base de rendimiento.
2.  **Regresión Ridge con Validación Cruzada (RidgeCV):** Se utilizó para manejar la multicolinealidad entre las características. El modelo `RidgeCV` fue empleado para encontrar el valor óptimo del hiperparámetro de regularización `alpha` dentro de un rango predefinido (`10.0 ** np.arange(-2,3)`), resultando en un `alpha` óptimo de **100.0**.
3.  **Regresión Lasso con Validación Cruzada (LassoCV):** Este modelo también aplica regularización y puede realizar selección de características al reducir algunos coeficientes a cero. Se utilizó `LassoCV` para determinar el `alpha` óptimo, que resultó ser **0.4544**.

---

## 📈 Resultados y Comparación

A continuación, se presenta una tabla comparativa con las métricas de rendimiento para cada uno de los modelos evaluados sobre el conjunto de prueba:

| Métrica                                    | Regresión Lineal Múltiple | Regresión Ridge (α=100.0) | Regresión Lasso (α=0.454) |
| :----------------------------------------- | :-----------------------: | :-----------------------: | :-----------------------: |
| **R²**                                     |          0.9775           |        **0.9780**         |          0.9776           |
| **MAE** (Error Absoluto Medio)             |           6.418           |         **6.349**         |           6.406           |
| **MSE** (Error Cuadrático Medio)           |          85.979           |        **84.326**         |          85.898           |
| **RMSE** (Raíz del Error Cuadrático Medio) |           9.272           |         **9.183**         |           9.268           |

_MAE: Mean Absolute Error, MSE: Mean Squared Error, RMSE: Root Mean Squared Error_

## ⭐ Conclusiones

Los tres modelos implementados mostraron un rendimiento muy alto y resultados bastante similares en la predicción de las emisiones de CO2. Sin embargo, al analizar las métricas en detalle, se puede concluir lo siguiente:

- El modelo de **Regresión Ridge con Validación Cruzada fue la opción más precisa**.
- Obtuvo el valor de **R² más alto** (0.9780), lo que indica que explica ligeramente mejor la variabilidad de los datos.
- Presentó los **valores más bajos en todas las métricas de error** (MAE, MSE y RMSE), lo que se traduce en un menor margen de error en las predicciones y una menor penalización por errores grandes.

Aunque las diferencias son marginales, la regularización aplicada por el modelo Ridge logró una ligera mejora en la generalización y precisión del modelo en comparación con la regresión lineal múltiple y la regresión Lasso.
