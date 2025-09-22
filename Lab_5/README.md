# Laboratorio 5 - Redes Neuronales Recurrentes (RNN) para Series de Tiempo

## Descripción del Proyecto

Este proyecto implementa un modelo de Red Neuronal Recurrente (LSTM) para la predicción de series temporales utilizando datos reales de producción industrial. Específicamente, se analiza la producción de helados y postres congelados en Estados Unidos usando datos del portal FRED de la Reserva Federal de St. Louis.

## Objetivos

- Comprender y aplicar conceptos básicos del preprocesamiento de series de tiempo
- Implementar un generador de secuencias temporales para entrenamiento de redes neuronales
- Diseñar, entrenar y evaluar un modelo LSTM para predicción temporal
- Analizar el desempeño del modelo mediante métricas y visualizaciones

## Datos Utilizados

**Fuente:** Federal Reserve Economic Data (FRED)  
**Serie:** IPN31152N - Industrial Production: Nondurable Goods: Ice cream and frozen dessert  
**Período:** Enero 2000 - Presente  
**Frecuencia:** Mensual  
**Unidades:** Índice 2012=100, No Ajustado Estacionalmente

## Estructura del Proyecto

```
├── Laboratorio_5_RNN.ipynb
├── README.md
└── requirements.txt
```

## Metodología

### 1. Obtención y Exploración de Datos
- Descarga automática desde FRED usando `pandas_datareader`
- Visualización de la serie temporal completa
- Análisis estadístico descriptivo

### 2. Preparación de Datos
- **División:** Últimos 24 meses como conjunto de prueba
- **Normalización:** MinMaxScaler para escalar datos al rango [0,1]
- **Generación de secuencias:** TimeseriesGenerator con ventana de 12 meses

### 3. Arquitectura del Modelo
```
Modelo Sequential:
├── LSTM(64 neuronas, activation='relu', return_sequences=True)
├── Dropout(0.2)
├── LSTM(32 neuronas, activation='relu')
├── Dropout(0.2)
└── Dense(1)  # Predicción un paso adelante
```

**Parámetros de Entrenamiento:**
- Optimizador: Adam
- Función de pérdida: MSE (Mean Squared Error)
- Épocas: 30
- Batch size: 16 (entrenamiento), 1 (prueba)
