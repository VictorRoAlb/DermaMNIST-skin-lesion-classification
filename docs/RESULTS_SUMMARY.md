# Resumen de resultados

## Tabla principal

| Modelo | Acc. | Bal. Acc. | Macro F1 | Kappa | Macro Rec. |
|---|---|---|---|---|---|
| M1: CNN propia | 0.711 Â± 0.008 | 0.450 Â± 0.018 | 0.419 Â± 0.016 | 0.435 Â± 0.016 | 0.450 Â± 0.018 |
| M2: ResNet50 ImageNet shallow | 0.812 Â± 0.008 | 0.649 Â± 0.023 | 0.645 Â± 0.020 | 0.642 Â± 0.015 | 0.649 Â± 0.023 |
| M3: ResNet50 ImageNet deep | 0.850 Â± 0.008 | 0.706 Â± 0.022 | 0.736 Â± 0.019 | 0.706 Â± 0.015 | 0.706 Â± 0.022 |
| M4: ResNet50 RadImageNet/RAC shallow | 0.723 Â± 0.008 | 0.416 Â± 0.018 | 0.417 Â± 0.017 | 0.450 Â± 0.016 | 0.416 Â± 0.018 |
| M5: ResNet50 RadImageNet/RAC deep | 0.728 Â± 0.008 | 0.468 Â± 0.018 | 0.445 Â± 0.016 | 0.482 Â± 0.015 | 0.468 Â± 0.018 |
| M6: EfficientNet-B1 ISIC frozen | 0.872 Â± 0.006 | 0.631 Â± 0.011 | 0.619 Â± 0.015 | 0.753 Â± 0.012 | 0.631 Â± 0.011 |

## Qué significa cada métrica

- **Accuracy**: proporción total de aciertos.
- **Balanced Accuracy**: media del recall por clase, útil cuando las clases están desbalanceadas.
- **Macro F1**: media no ponderada del F1 por clase.
- **Cohen's Kappa**: acuerdo corregido por azar.
- **Macro Recall**: media no ponderada del recall por clase.

## Conclusión técnica

Hemos observado que **M3: ResNet50 ImageNet deep** es el mejor modelo comparable si priorizamos Macro F1 y Balanced Accuracy. **M6: EfficientNet-B1 ISIC frozen** alcanza la mayor Accuracy y el mayor Kappa, pero no supera a M3 en las métricas macro.

## Figuras recomendadas para el informe

- Distribución de clases.
- Curvas de entrenamiento.
- Matriz de confusión del mejor modelo comparable.
- Comparación final de métricas.
- Dos ejemplos Grad-CAM seleccionados de M3: un caso correctamente clasificado y un caso incorrecto.

Como apoyo interpretativo, incluimos dos ejemplos Grad-CAM seleccionados del modelo M3: un caso correctamente clasificado y un caso incorrecto. Estas visualizaciones se emplean únicamente como ejemplos cualitativos para comprobar si la activación del modelo se concentra en regiones visualmente relevantes.
