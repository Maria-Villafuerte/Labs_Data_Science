# Análisis Geoespacial y Sensores Remotos - Petén, Guatemala

## 📋 Información del Proyecto

**Autores:** Fabiola Contreras (22787), María José Villafuerte (22129)  
**Universidad:** Universidad del Valle de Guatemala  
**Curso:** Data Science - Laboratorio 3  
**Sección:** 21  

## 🎯 Objetivo

Realizar un análisis temporal de la cobertura vegetal en la región de Petén, Guatemala, utilizando datos satelitales Sentinel-2 para detectar cambios en la vegetación entre abril de 2020 y abril de 2024 mediante el cálculo del Índice de Vegetación de Diferencia Normalizada (NDVI).

## 🛰️ Datos Utilizados

- **Fuente:** Sentinel-2 L2A
- **Periodo:** Abril 2020 vs Abril 2024
- **Bandas espectrales:**
  - Banda 4 (Rojo): 665 nm
  - Banda 8 (Infrarrojo cercano): 842 nm
- **Región de estudio:** Petén, Guatemala
- **Resolución espacial:** 10m

## 🔧 Metodología

### 1. Procesamiento de Datos
- Carga y alineación de imágenes satelitales de diferentes fechas
- Reproyección utilizando `rasterio.warp.reproject`
- Cálculo del NDVI: `(NIR - Red) / (NIR + Red + 1e-10)`

### 2. Análisis Temporal
- Generación de mapas NDVI para 2020 y 2024
- Cálculo de diferencias temporales (NDVI₂₀₂₄ - NDVI₂₀₂₀)
- Aplicación de umbral de deforestación (-0.2)
- Creación de máscara binaria de pérdida vegetal

### 3. Cuantificación
- Cálculo del área total deforestada
- Estimación del porcentaje de pérdida de cobertura
- Análisis espacial de patrones de cambio

## 📊 Resultados Principales

### Métricas Cuantitativas
- **Área de pérdida:** 0.26 m²
- **Porcentaje de deforestación:** 5.93%
- **Periodo analizado:** 4 años (2020-2024)

### Hallazgos Clave
1. **Estabilidad general** con cobertura vegetal predominantemente saludable
2. **Deforestación fragmentada** distribuida de manera dispersa
3. **Zonas críticas** identificadas en el centro y sur de Petén
4. **Procesos dinámicos** con áreas de pérdida y recuperación simultánea

## 🗺️ Productos Generados

1. **Mapa NDVI 2020:** Línea base de cobertura vegetal
2. **Mapa NDVI 2024:** Estado actual de la vegetación
3. **Mapa de diferencias:** Cambios temporales (azul = pérdida, rojo = ganancia)
4. **Máscara de deforestación:** Áreas con pérdida significativa (umbral < -0.2)

## 🔍 Análisis de Recuperación Vegetal

### Factores que Explican las Mejoras Detectadas:
- **Concesiones forestales comunitarias** con tasas de deforestación de 0.1% anual
- **Programas de reforestación** gubernamentales (>1 millón de árboles plantados)
- **Regeneración natural asistida** en áreas de abandono de actividades extractivas
- **Políticas internacionales** como el programa "Petén más sostenible"
- **Incentivos forestales** del Instituto Nacional de Bosques (INAB)

## 🚨 Implicaciones Ecológicas

### Desafíos Identificados:
- La **fragmentación dispersa** genera mayor impacto ecológico que la deforestación concentrada
- Riesgo para la **conectividad del corredor biológico** de la Reserva de Biosfera Maya
- Amenaza potencial para la **movilidad de especies** y biodiversidad regional

### Zonas Prioritarias:
- Centro y sur de Petén requieren **atención inmediata**
- Implementación de **estrategias de conservación específicas**
- Monitoreo continuo de **presiones antropogénicas**

## 🛠️ Tecnologías Utilizadas

```python
# Librerías principales
import rasterio
from rasterio.warp import reproject, Resampling
import numpy as np
import matplotlib.pyplot as plt
```

### Funciones Clave:
- `alinear_raster()`: Reproyección y alineación espacial
- `calcular_ndvi_archivos()`: Cálculo automatizado del NDVI
- Análisis de umbrales para detección de cambios

## 📋 Conclusiones

1. **Deforestación moderada** (5.93%) pero con patrones preocupantes de fragmentación
2. **Éxito parcial** de modelos de conservación comunitaria
3. **Necesidad urgente** de estrategias de conservación en zonas críticas
4. **Importancia del monitoreo continuo** para la Reserva de Biosfera Maya
5. **Potencial de recuperación** demostrado en áreas con manejo sostenible

## 📚 Referencias y Fuentes

- Datos satelitales: European Space Agency (ESA) - Sentinel-2
- Información contextual: CONAP, ACOFOP, MARN Guatemala
- Metodología: Literatura científica en teledetección forestal