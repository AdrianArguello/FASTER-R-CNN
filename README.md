Descripción del Proyecto

Este proyecto implementa un modelo de detección de objetos basado en Faster R-CNN para identificar aviones en imágenes estáticas.
El enfoque es principalmente exploratorio, buscando comprender:

El funcionamiento de la RPN
El impacto de los anchors
El rol del backbone y FPN
La influencia del fondo en la detección


Arquitectura Utilizada

Backbone convolucional
Feature Pyramid Network (FPN)
Region Proposal Network (RPN)
ROI Heads (clasificación + refinamiento)

Configuración Técnica

PyTorch / torchvision
Modelo: fasterrcnn_resnet50_fpn
Pesos preentrenados en COCO
Imagen de prueba personalizada

Análisis de Anchors

Se evaluó cómo los parámetros de anchors afectan la detección:

Tamaños (sizes)
Proporciones (aspect_ratios)

Se observó que una mala configuración genera propuestas irrelevantes, mientras que un ajuste adecuado mejora significativamente la alineación con el objeto.


Análisis de Resultados

Durante la inferencia, el modelo logró localizar correctamente el objeto en la imagen, generando bounding boxes precisas. Sin embargo, la etiqueta asignada no fue la esperada. En algunos casos, el objeto fue clasificado como bird en lugar de airplane.

Interpretación

La detección espacial fue correcta (localización del objeto)
El modelo captó características estructurales relevantes
La discrepancia ocurre en la etapa de clasificación, donde se asigna la clase con mayor probabilidad según el entrenamiento previo

Esto demuestra que un modelo puede localizar correctamente un objeto incluso cuando la clasificación no coincide con la categoría esperada.

La correcta detección espacial sugiere que el modelo está aprendiendo patrones relevantes; sin embargo, la clasificación responde a una asignación probabilística basada en sus representaciones internas.

Aunque la clase airplane está presente en el entrenamiento, el modelo no ha generalizado adecuadamente este tipo de imagen en particular, por lo que asigna la clase más probable según su aprendizaje previo.

Conclusión

Esto refleja una limitación en la capacidad de generalización del modelo más que un problema estructural.

Para mejorar la clasificación, se recomienda realizar fine-tuning con un dataset específico, adaptado al dominio de las imágenes utilizadas.





