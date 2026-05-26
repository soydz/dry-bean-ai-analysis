# Dry Bean Classification — Modelos y Simulación II

**Universidad de Antioquia** — Departamento de Ingeniería de Sistemas

**Autores:** Joseph Roldán Ramírez, Duban Zuluaga, Carlos Andrés Zuluaga

**Profesor:** Julián David Arias Londoño

## Video de sustentación

[![Ver video del proyecto](https://github.com/Josephroldanr/sistemas-operativos-labs/blob/17450123468e0c0a16161d83c3f5ff52592d050c/Sustentaci%C3%B3n%20del%20Proyecto%20Dry%20Bean%20ML.png)](https://www.youtube.com/watch?v=JT7ZIwZISag)

## Descripción

Sistema de clasificación automática de 7 variedades de frijol seco (Dermason, Sira, Seker, Horoz, Cali, Barbunya y Bombay) usando técnicas de aprendizaje supervisado sobre el [Dry Bean Dataset](https://archive.ics.uci.edu/dataset/602/dry+bean+dataset) de UCI Machine Learning.

## Estructura del repositorio

```
.
├── README.md                       # Este archivo
├── informe final                   # Informe IEEE
├── requirements.txt                # Dependencias Python
│── 1_eda.ipynb                     # Análisis exploratorio
│── 2_modelos.ipynb                 # Entrenamiento y evaluación de 7 modelos
│── 3_reduccion_dim.ipynb           # PCA y UMAP
├── data/
│   └── Dry_Bean_Dataset.xlsx       # Dataset original (UCI)
├── results/                        # Salidas generadas por los notebooks
│   ├── results_all.csv             # Métricas de las 21 configuraciones
│   ├── pca_results.csv             # Resultados de PCA
│   ├── umap_results.csv            # Resultados de UMAP
│   ├── comparison_final.csv        # Tabla comparativa final
│   ├── variable_importance.csv     # Información mutua y Spearman
│   └── per_class_svm.csv           # Reporte por clase del mejor modelo
└── figures/                        # Figuras del informe
    ├── fig1_class_distribution.png
    ├── fig2_correlation_matrix.png
    ├── fig3_histograms_by_class.png
    ├── fig4_boxplots_key_features.png
    ├── fig5_pairplot.png
    ├── fig6_skewness_kurtosis.png
    ├── fig7_comparison_f1.png
    ├── fig8_cm_svm.png
    ├── fig9_heatmap.png
    ├── fig10_variable_importance.png
    ├── fig11_pca_variance.png
    ├── fig12_pca_2d.png
    ├── fig13_umap_2d.png
    └── fig14_comparison_dim_reduction.png
```

## Instalación

### Requisitos
- Python 3.10 o superior
- pip

### Pasos
```bash
# Clonar el repositorio
git clone https://github.com/soydz/dry-bean-ai-analysis
cd dry-bean-classification

# Crear entorno virtual (opcional pero recomendado)
python -m venv .venv
source .venv/bin/activate    # Linux/Mac
# .venv\Scripts\activate     # Windows

# Instalar dependencias
pip install -r requirements.txt
```

## Cómo reproducir los resultados

Ejecutar los notebooks en orden:

1. `notebooks/01_eda.ipynb` — Genera las figuras del análisis exploratorio.
2. `notebooks/02_modelos.ipynb` — Entrena y evalúa las 21 configuraciones (7 modelos × 3 estrategias de balanceo). Genera `results_all.csv` y las figuras 7, 8 y 9.
3. `notebooks/03_reduccion_dim.ipynb` — Aplica PCA y UMAP sobre los 2 mejores modelos. Genera las figuras 10 a 14.

Para abrirlos localmente:
```bash
jupyter notebook notebooks/
```

O súbelos a [Google Colab](https://colab.research.google.com/) junto con el archivo `Dry_Bean_Dataset.xlsx`. En Colab, agrega al inicio una celda con:
```python
!pip install imbalanced-learn xgboost lightgbm umap-learn -q
```

> **Nota:** todos los experimentos usan `random_state=42`, por lo que los resultados son reproducibles y deben coincidir con los reportados en el informe.

## Resumen de resultados

| Modelo | Balanceo | Accuracy | F1-macro |
|---|---|---|---|
| **SVM** | **None** | **0,9254** | **0,9358** |
| SVM | SMOTE | 0,9243 | 0,9353 |
| MLP | SMOTE | 0,9228 | 0,9336 |
| MLP | None | 0,9225 | 0,9331 |
| LightGBM | SMOTE | 0,9206 | 0,9318 |

**Mejor configuración:** SVM con kernel RBF (`C=10`, `gamma=0.1`) sin balanceo de clases.

**Reducción de dimensión:** PCA con 7 componentes mantiene prácticamente el mismo desempeño (F1=0,9350) usando 56 % menos dimensiones.

## Referencias

- M. Koklu y I. A. Ozkan, "Multiclass Classification of Dry Beans Using Computer Vision and Machine Learning Techniques," *Computers and Electronics in Agriculture*, vol. 174, 105507, 2020.
- A. Mukherjee et al., "SMOTE-ENN resampling technique with Bayesian optimization for multi-class classification of dry bean varieties," *Applied Soft Computing*, vol. 181, 113467, 2025.

Ver el informe en PDF para la lista completa de referencias.
