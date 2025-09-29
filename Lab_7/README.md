# Laboratorio 7: Predicción de Diabetes con AutoGluon

## Descripción del Proyecto

Este laboratorio implementa un modelo de predicción de diabetes utilizando AutoGluon, una herramienta de AutoML que automatiza el proceso de entrenamiento y optimización de modelos de machine learning. Se compara el rendimiento de AutoGluon contra un modelo base de regresión logística.

## Dataset

**Fuente:** Diabetes Dataset  
**Registros:** 768 pacientes  
**Variables:** 9 características predictivas

### Variables del Dataset:

- **Pregnancies:** Número de embarazos
- **Glucose:** Concentración de glucosa en plasma
- **BloodPressure:** Presión arterial diastólica (mm Hg)
- **SkinThickness:** Grosor del pliegue cutáneo del tríceps (mm)
- **Insulin:** Insulina sérica 2 horas (mu U/ml)
- **BMI:** Índice de masa corporal
- **DiabetesPedigreeFunction:** Función de pedigrí de diabetes
- **Age:** Edad en años
- **Outcome:** Variable objetivo (0: No diabetes, 1: Diabetes)

## Estructura del Proyecto

```
├── diabetes.csv                 # Dataset principal
├── Analisis.ipynb               # Análisis exploratorio de datos
├── Modelo.ipynb                 # Entrenamiento con AutoGluon
└── README.md                    # Este archivo
```

## Instalación y Dependencias

```bash
# Instalar AutoGluon
pip install autogluon.tabular

# Otras dependencias
pip install pandas seaborn matplotlib scikit-learn
```

## Configuración de AutoGluon

```python
predictor = TabularPredictor(
    label='Outcome',
    eval_metric='accuracy',
    path='./autogluon_models'
)

predictor.fit(
    train_data=train_data,
    presets='best_quality',    # Prioriza calidad sobre velocidad
    time_limit=300,            # 5 minutos de entrenamiento
    verbosity=2
)
```

## Ventajas de AutoGluon

- Automatización completa del pipeline de ML
- Evaluación de múltiples algoritmos (37 modelos en 5 minutos)
- Optimización automática de hiperparámetros
- Ensemble de modelos sin configuración manual
- Resultados superiores al baseline con mínimo esfuerzo


## Conclusiones

AutoGluon demostró ser una herramienta efectiva para el desarrollo rápido de modelos predictivos de alta calidad, superando significativamente el modelo baseline y proporcionando insights valiosos sobre la importancia de las variables en la predicción de diabetes. La automatización del proceso permite enfocarse en la interpretación clínica y validación médica de los resultados.

## Autores

* María Villafuerte  22129
* Fabiola Contreras 22787
