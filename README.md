# Clasificación multiclase de lesiones cutáneas en DermaMNIST

Autores: Víctor Rodríguez Albendea y Patricia Rodrigo Barrio

## Resumen

En este repositorio presentamos nuestro trabajo académico sobre clasificación multiclase de lesiones cutáneas con DermaMNIST. Hemos comparado una CNN propia entrenada desde cero, dos variantes de transferencia con ResNet50 e ImageNet, dos variantes con inicialización médica RadImageNet/RAC y una referencia dermatológica basada en EfficientNet-B1 preentrenada en el entorno ISIC.

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

## Configuración resumida de modelos

| ID | Backbone | Inicialización | Tipo de ajuste | Parámetros entrenables |
|---|---|---|---|---:|
| M1 | CNN propia | Aleatoria | Entrenamiento completo | 157.159 |
| M2 | ResNet50 | ImageNet | Shallow tuning | 526.343 |
| M3 | ResNet50 | ImageNet | Deep tuning parcial | 15.479.815 |
| M4 | ResNet50 | RadImageNet / RAC | Shallow tuning | 526.343 |
| M5 | ResNet50 | RadImageNet / RAC | Deep tuning parcial | 15.468.551 |
| M6 | EfficientNet-B1 | ISIC / entorno dermatológico | Backbone congelado | 8.967 |

## Resultados finales en test

| Modelo | Acc. | Bal. Acc. | Macro F1 | Kappa | Macro Rec. |
|---|---|---|---|---|---|
| M1: CNN propia | 0.711 ± 0.008 | 0.450 ± 0.018 | 0.419 ± 0.016 | 0.435 ± 0.016 | 0.450 ± 0.018 |
| M2: ResNet50 ImageNet shallow | 0.812 ± 0.008 | 0.649 ± 0.023 | 0.645 ± 0.020 | 0.642 ± 0.015 | 0.649 ± 0.023 |
| M3: ResNet50 ImageNet deep | 0.850 ± 0.008 | 0.706 ± 0.022 | 0.736 ± 0.019 | 0.706 ± 0.015 | 0.706 ± 0.022 |
| M4: ResNet50 RadImageNet/RAC shallow | 0.723 ± 0.008 | 0.416 ± 0.018 | 0.417 ± 0.017 | 0.450 ± 0.016 | 0.416 ± 0.018 |
| M5: ResNet50 RadImageNet/RAC deep | 0.728 ± 0.008 | 0.468 ± 0.018 | 0.445 ± 0.016 | 0.482 ± 0.015 | 0.468 ± 0.018 |
| M6: EfficientNet-B1 ISIC frozen | 0.872 ± 0.006 | 0.631 ± 0.011 | 0.619 ± 0.015 | 0.753 ± 0.012 | 0.631 ± 0.011 |

## Interpretación breve

- Hemos observado que **M3: ResNet50 ImageNet deep** es el mejor modelo comparable por Macro F1 y Balanced Accuracy.
- **M6: EfficientNet-B1 ISIC frozen** obtiene la mayor Accuracy y el mayor valor de Kappa, pero no alcanza el mejor Macro F1 ni la mejor Balanced Accuracy.
- En conjunto, la comparación muestra que la transferencia desde ImageNet con deep tuning parcial fue la estrategia más equilibrada para este experimento.

## Reproducción

1. Instalar las dependencias con `pip install -r requirements.txt`.
2. Abrir `notebooks/Trabajo_Deep_Learning_2026_Victor_Patri_FINAL.ipynb` en Google Colab.
3. Activar GPU y montar Google Drive si se quieren reutilizar cachés o checkpoints.
4. Ejecutar las secciones en orden.

## Regeneración de figuras

Para regenerar las figuras principales del informe:

```bash
python scripts/make_paper_figures.py
```

## Inspección rápida de resultados

```bash
python scripts/inspect_results.py
```

## Licencias, datos y pesos preentrenados

Los datos y pesos preentrenados utilizados en este trabajo proceden de fuentes externas y no se redistribuyen en este repositorio. El repositorio contiene el código, resultados agregados, figuras y documentación generada para el estudio. Para reproducir el trabajo, los datasets y pesos deben obtenerse desde sus fuentes oficiales respetando sus licencias correspondientes.

DermaMNIST deriva de HAM10000. Por ello, el modelo EfficientNet-B1 preentrenado en el entorno ISIC se mantiene congelado y solo se entrena la cabeza de clasificación. Sus resultados se interpretan como una referencia dermatológica de dominio cercano, no como una comparación completamente independiente.

## Checkpoints

Los pesos y checkpoints grandes no se versionan directamente en git. Hemos documentado su uso en `docs/WEIGHTS.md`.
