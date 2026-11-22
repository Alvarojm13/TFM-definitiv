# Clasificación de enfermedad coronaria con el conjunto de datos Cleveland (UCI)

Código del Trabajo Fin de Máster de Álvaro Jiménez (Máster en Inteligencia Artificial, CEMP).

El trabajo desarrolla y evalúa modelos de predicción de enfermedad coronaria angiográfica (estenosis > 50 %) en los 303 pacientes de la Cleveland Clinic del repositorio UCI. Los compara con la probabilidad pretest de Diamond y Forrester (1979) y sigue la guía TRIPOD+AI.

## Contenido

| Fichero | Qué hace | Lee | Genera |
|---|---|---|---|
| `01_datos_y_eda.ipynb` | Control de calidad, Tabla 1 y figuras descriptivas | `processed.cleveland.data` (y `heart.csv`, opcional) | `datos_cleveland_limpios.csv`, `figures/` |
| `02_modelos.ipynb` | Partición 80/20, ajuste con validación cruzada y umbrales de descarte | `datos_cleveland_limpios.csv` | `modelos_tfm.joblib`, `resumen_entrenamiento.csv` |
| `03_evaluacion.ipynb` | AUC con IC por bootstrap, calibración y rendimiento clínico en test | los dos anteriores | tablas y figuras en `figures/`, `predicciones_test.csv` |
| `04_interpretacion_y_simulacion.ipynb` | Odds ratios, importancia por permutación y tres pacientes simulados | los dos anteriores | tablas y figuras en `figures/` |
| `modelos_tfm.joblib` | Modelos entrenados, umbrales e índices de la partición | | |
| `requirements.txt` | Versiones con las que se obtuvieron los resultados | | |

## Cómo reproducirlo

1. Descargar `processed.cleveland.data` del repositorio UCI: https://archive.ics.uci.edu/dataset/45/heart+disease
2. Abrir los cuadernos en Google Colab y ejecutarlos en orden (01 → 04). Cada uno pide subir los ficheros que necesita.
3. Para reproducir solo la evaluación con el modelo publicado, ejecutar 03 y 04 subiendo `datos_cleveland_limpios.csv` y `modelos_tfm.joblib`. Requiere scikit-learn 1.6.1; con otra versión, volver a ejecutar el cuaderno 02.

Semilla fija (42) en todos los procesos aleatorios.

## Aviso

Trabajo académico. Los modelos no están validados externamente ni certificados como producto sanitario y no deben usarse para decisiones clínicas.

## Datos

Janosi, A., Steinbrunn, W., Pfisterer, M., & Detrano, R. (1989). *Heart Disease* [Conjunto de datos]. UCI Machine Learning Repository. https://doi.org/10.24432/C52P4X
