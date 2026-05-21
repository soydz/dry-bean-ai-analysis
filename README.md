# Análisis del Dataset de Frijoles Secos (Dry Bean)

Este proyecto se centra en la clasificación de siete tipos diferentes de frijoles secos utilizando diversos algoritmos de aprendizaje automático. El objetivo es identificar el modelo y las técnicas de análisis más efectivos para lograr una alta precisión de clasificación basada en características morfológicas.

## 📋 Objetivos del Proyecto
- Realizar un Análisis Exploratorio de Datos (EDA) exhaustivo para comprender las distribuciones de las variables y sus correlaciones.
- Evaluar múltiples modelos de aprendizaje supervisado (Regresión Logística, kNN, SVM, MLP, Random Forest, XGBoost, LightGBM).
- Implementar y comparar estrategias de balanceo de datos (SMOTE, SMOTE-ENN).
- Analizar la separabilidad de las clases mediante técnicas de reducción de dimensionalidad (PCA, UMAP).
- Documentar todo el proceso siguiendo estándares académicos.

## 📊 Descripción del Dataset
El **Dry Bean Dataset** contiene características morfológicas de 13,611 muestras de frijoles distribuidas en 7 clases:
- **Variables**: Área, Perímetro, Longitud del Eje Mayor, Longitud del Eje Menor, Excentricidad, Área Convexa, Extensión, Relación de Aspecto.
- **Clases**: SIRA, DERMASON, BOMBAY, CALUNGA, HORCALON, CARIOCA, SEYALAN.

## 🚀 Flujo de Ejecución
El proyecto está organizado en tres notebooks principales. Se recomienda abrirlos en un entorno Jupyter (Jupyter Lab, Jupyter Notebook o Google Colab) y ejecutar las celdas en el orden numérico secuencial. Deben ejecutarse en el siguiente orden

1. **`1_EDA.ipynb`**: 
   - Limpieza de datos y descripción de variables.
   - Análisis estadístico y matrices de correlación.
   - Análisis visual de la distribución de variables por clase.

2. **`2_modelos.ipynb`**:
   - Preprocesamiento de datos y división estratificada (80/20).
   - Implementación de 7 modelos con optimización de hiperparámetros vía `RandomizedSearchCV`.
   - Comparación de 3 estrategias de balanceo (Ninguna, SMOTE, SMOTE-ENN) usando Validación Cruzada Estratificada de 5 pliegues.
   - Evaluación final en el conjunto de prueba y selección del mejor modelo.

3. **`03_reduccion_dim.ipynb`**:
   - Aplicación de PCA (Análisis de Componentes Principales) y UMAP (Uniform Manifold Approximation and Projection).
   - Visualización de datos multidimensionales en 2D para analizar el solapamiento entre clases.

## 🛠️ Instalación y Requisitos
Asegúrese de tener instalado Python 3.8+. Instale las dependencias necesarias:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn imbalanced-learn xgboost lightgbm umap-learn
```

## 📈 Resultados Clave
- **Mejor Modelo**: SVM (Support Vector Machine) sin balanceo alcanzó la puntuación F1-macro más alta (~0.936).
- **Observaciones**:
    - La clase `BOMBAY` es perfectamente separable.
    - `SIRA` y `DERMASON` muestran el mayor solapamiento, representando el principal desafío de clasificación.
    - El balanceo de datos proporcionó mejoras insignificantes debido al desbalance moderado de las clases.

## 📁 Estructura del Repositorio
```text
├── 1_EDA.ipynb                # Análisis Exploratorio de Datos
├── 2_modelos.ipynb            # Entrenamiento y Evaluación de Modelos
├── 3_reduccion_dim.ipynb      # Análisis de Reducción de Dimensionalidad
├── data/                      # Dataset y documentación de datos
│   ├── Dry_Beans_Dataset.csv  # Dataset
│   └── README.md              # Detalles específicos de los datos
├── docs/                      # Guías del proyecto y rúbricas
└── README.md                  # Documentación general del proyecto
```

## 👥 Contribuyentes
- Joseph Roldán
- Duban Zuluaga
- Juan Esteban Cardozo
