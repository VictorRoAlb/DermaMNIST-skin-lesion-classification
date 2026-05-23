# Checkpoints y pesos

En este trabajo hemos generado checkpoints intermedios y modelos finales para cada configuración. No los redistribuimos directamente en este repositorio cuando su tamaño o su origen externo no lo hacen recomendable.

## Ruta sugerida

```text
models/checkpoints/
├── M1_CNN_PROPIA_224_seed123_best.keras
├── M2_RESNET50_IMAGENET_SHALLOW_seed123_best.keras
├── M3_RESNET50_IMAGENET_DEEP_seed123_best.keras
├── M4_RESNET50_RADIMAGENET_RAC_SHALLOW_seed123_best.pt
├── M5_RESNET50_RADIMAGENET_RAC_DEEP_seed123_best.pt
└── M6_MAXNET_ISIC_DERMATOLOGY_FROZEN_BASELINE_seed123_best.pt
```

## Reutilización local

- Si se quieren reutilizar checkpoints ya entrenados, recomendamos colocarlos en `models/checkpoints/`.
- Si se utilizan rutas externas en Google Drive, conviene mantener la misma convención de nombres del notebook para evitar cambios adicionales.
- En el caso de pesos externos de ImageNet, RadImageNet/RAC o EfficientNet-B1 en entorno ISIC, deben obtenerse desde la fuente oficial utilizada en el trabajo o desde un almacenamiento externo propio.

## Nota

- No subimos directamente al repositorio pesos o checkpoints grandes.
- Si se desean compartir, recomendamos utilizar Google Drive, GitHub Releases o un almacenamiento equivalente.
