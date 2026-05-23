# Checkpoints y pesos

En nuestro trabajo hemos generado checkpoints finales para las seis configuraciones principales. En esta versión pública del repositorio hemos decidido compartir esos checkpoints finales mediante Git LFS para facilitar su reutilización, pero seguimos sin redistribuir pesos externos de terceros.

## Checkpoints publicados

- `M1_CNN_PROPIA_224_seed123_best.keras`
- `M2_RESNET50_IMAGENET_SHALLOW_seed123_best.keras`
- `M3_RESNET50_IMAGENET_DEEP_seed123_best.keras`
- `M4_RESNET50_RADIMAGENET_RAC_SHALLOW_seed123_best.pt`
- `M5_RESNET50_RADIMAGENET_RAC_DEEP_seed123_best.pt`
- `M6_MAXNET_ISIC_DERMATOLOGY_FROZEN_BASELINE_seed123_best.pt`

## Ruta del repositorio

```text
models/checkpoints/
├── M1_CNN_PROPIA_224_seed123_best.keras
├── M2_RESNET50_IMAGENET_SHALLOW_seed123_best.keras
├── M3_RESNET50_IMAGENET_DEEP_seed123_best.keras
├── M4_RESNET50_RADIMAGENET_RAC_SHALLOW_seed123_best.pt
├── M5_RESNET50_RADIMAGENET_RAC_DEEP_seed123_best.pt
└── M6_MAXNET_ISIC_DERMATOLOGY_FROZEN_BASELINE_seed123_best.pt
```

## Uso

- Hemos versionado estos checkpoints con Git LFS.
- Tras clonar el repositorio, conviene ejecutar `git lfs install` y `git lfs pull`.
- Los checkpoints permiten reutilizar directamente los modelos finales entrenados en nuestro trabajo.

## Alcance de la redistribución

- Compartimos únicamente los checkpoints finales entrenados por nosotros.
- No redistribuimos pesos externos de ImageNet, RadImageNet/RAC ni EfficientNet-B1 en entorno ISIC como archivos independientes.
- Si se desean regenerar los modelos desde cero, debe seguirse el notebook principal y obtener los pesos externos desde sus fuentes oficiales.
