# Clasificación multiclase de lesiones cutáneas en DermaMNIST

Autores: Víctor Rodríguez Albendea y Patricia Rodrigo Barrio

## Resumen

En este repositorio presentamos nuestro trabajo académico sobre clasificación multiclase de lesiones cutáneas con DermaMNIST. Hemos comparado una CNN propia entrenada desde cero, dos variantes de transferencia con ResNet50 e ImageNet, dos variantes con inicialización médica RadImageNet/RAC y una referencia dermatológica basada en EfficientNet-B1 / MaxNet preentrenada en el entorno ISIC.

Hemos ejecutado el trabajo final en Google Colab con GPU NVIDIA T4.

## Objetivo del estudio

Hemos estudiado cómo cambia el rendimiento cuando partimos de distintos niveles de conocimiento previo: entrenamiento desde cero, preentrenamiento generalista, preentrenamiento radiológico y preentrenamiento dermatológico. Aunque el entrenamiento se optimiza mediante la función de pérdida definida en cada modelo, la selección e interpretación del rendimiento se realizó priorizando métricas robustas frente al desbalanceo, especialmente Macro F1 y Balanced Accuracy.

## Dataset

- DermaMNIST, subconjunto de MedMNIST derivado de HAM10000.
- 7 clases.
- Particiones oficiales: train, validation y test.
- Resolución utilizada: 224 x 224 en RGB.

El dataset no se redistribuye en este repositorio. Para reproducir el trabajo debe descargarse mediante MedMNIST o desde las fuentes oficiales correspondientes.

## Modelos comparados

- M1: CNN propia entrenada desde cero.
- M2: ResNet50 ImageNet con shallow tuning.
- M3: ResNet50 ImageNet con deep tuning parcial.
- M4: ResNet50 RadImageNet/RAC con shallow tuning.
- M5: ResNet50 RadImageNet/RAC con deep tuning parcial.
- M6: EfficientNet-B1 / MaxNet preentrenada en entorno dermatológico ISIC, con backbone congelado.

## Métricas principales

Hemos evaluado Accuracy, Balanced Accuracy, Macro F1, Cohen’s Kappa y Macro Recall. Hemos utilizado métricas macro y balanced accuracy porque DermaMNIST presenta desbalanceo entre clases y queríamos evitar una interpretación basada únicamente en accuracy.

## Resultados y conclusiones

- M3 es el mejor modelo comparable por Macro F1 y Balanced Accuracy.
- M6 obtiene la mayor Accuracy y el mayor Kappa, pero no supera a M3 en Macro F1.
- Los resultados principales proceden de métricas agregadas y bootstrap en test.

## Figuras destacadas

- `figures/learning_curves/M3_RESNET50_IMAGENET_DEEP_seed123_learning_curves.png`
- `figures/paper/m3_learning_curves.png`
- `figures/paper/final_metrics_comparison.png`
- `figures/paper/macro_f1_vs_training_time.png`

Como apoyo interpretativo, incluimos dos ejemplos Grad-CAM seleccionados del modelo M3: un caso correctamente clasificado y un caso incorrecto. Estas visualizaciones se emplean únicamente como ejemplos cualitativos para comprobar si la activación del modelo se concentra en regiones visualmente relevantes.

- Ejemplo Grad-CAM correcto seleccionado: `correct_01_idx0.png`
- Ejemplo Grad-CAM incorrecto seleccionado: `incorrect_01_idx3.png`

## Reproducción

1. Instalar las dependencias con `pip install -r requirements.txt`.
2. Abrir `notebooks/Trabajo_Deep_Learning_2026_Victor_Patri_FINAL.ipynb` en Google Colab.
3. Activar GPU y montar Drive si se quieren reutilizar cachés o checkpoints locales.
4. Ejecutar las secciones en orden.

## Checkpoints y pesos

Hemos publicado los seis checkpoints finales entrenados por nosotros en `models/checkpoints/` utilizando Git LFS, de forma que puedan reutilizarse sin incorporar al repositorio pesos externos de terceros. Para descargar estos archivos tras clonar el repositorio recomendamos ejecutar `git lfs install` y `git lfs pull`.


## Reutilización de checkpoints

Los checkpoints finales publicados en Git LFS corresponden únicamente a los modelos entrenados en nuestro trabajo. No redistribuimos pesos externos de ImageNet, RadImageNet/RAC ni EfficientNet-B1 en entorno ISIC fuera del resultado final entrenado.

## Licencias, datos y pesos preentrenados

Los datos y pesos preentrenados utilizados en este trabajo proceden de fuentes externas y no se redistribuyen en este repositorio. El repositorio contiene el código, resultados agregados, figuras y documentación generada para el estudio. Para reproducir el trabajo, los datasets y pesos deben obtenerse desde sus fuentes oficiales respetando sus licencias correspondientes.

DermaMNIST deriva de HAM10000. Por ello, el modelo EfficientNet-B1 preentrenado en el entorno ISIC se mantiene congelado y solo se entrena la cabeza de clasificación. Sus resultados se interpretan como una referencia dermatológica de dominio cercano, no como una comparación completamente independiente.
