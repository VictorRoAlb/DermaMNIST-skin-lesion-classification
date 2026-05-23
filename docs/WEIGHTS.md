# Checkpoints y pesos

En nuestro trabajo hemos generado checkpoints finales para las seis configuraciones. Git LFS está disponible en el entorno local, pero en esta versión pública del repositorio hemos optado por no versionar los checkpoints pesados para mantener el repositorio ligero y evitar redistribuir pesos externos o derivados.

## Checkpoints finales disponibles localmente

- `M3_RESNET50_IMAGENET_DEEP_seed123_best.keras`
- `M1_CNN_PROPIA_224_seed123_best.keras`
- `M6_MAXNET_ISIC_DERMATOLOGY_FROZEN_BASELINE_seed123_best.pt`
- `M2_RESNET50_IMAGENET_SHALLOW_seed123_best.keras`
- `M5_RESNET50_RADIMAGENET_RAC_DEEP_seed123_best.pt`
- `M4_RESNET50_RADIMAGENET_RAC_SHALLOW_seed123_best.pt`

## Ruta local esperada

```text
models/checkpoints/
├── M1_CNN_PROPIA_224_seed123_best.keras
├── M2_RESNET50_IMAGENET_SHALLOW_seed123_best.keras
├── M3_RESNET50_IMAGENET_DEEP_seed123_best.keras
├── M4_RESNET50_RADIMAGENET_RAC_SHALLOW_seed123_best.pt
├── M5_RESNET50_RADIMAGENET_RAC_DEEP_seed123_best.pt
└── M6_MAXNET_ISIC_DERMATOLOGY_FROZEN_BASELINE_seed123_best.pt
```

## Criterio de publicación

- Hemos extraído los checkpoints finales al directorio local `models/checkpoints/`.
- No los hemos incluido en el repositorio público, aunque Git LFS podría utilizarse en una versión futura si se quisiera compartir únicamente los modelos entrenados por nosotros.
- No redistribuimos pesos externos de ImageNet, RadImageNet/RAC ni EfficientNet-B1 en entorno ISIC.
- Si alguien quiere reutilizar los checkpoints, debe colocarlos manualmente en `models/checkpoints/` o trabajar con una ruta externa equivalente.
