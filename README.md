# Traductor de lengua de signos con IA

Web para aprender el alfabeto dactilológico (letras con la mano) y modelo de visión por computador que reconoce letras signadas a partir de una foto de la webcam.

> Mi Treball de Recerca de bachillerato (2022-2023). Fue mi primer proyecto grande con IA.

<!-- TODO: añade una captura de la web y una imagen de la detección (la caja sobre la mano con la letra). -->

## Qué hace

**Web de aprendizaje** (hecha con [Anvil](https://anvil.works), en Python)
- Teoría inicial, vocales y consonantes del alfabeto, con imágenes de cada signo.
- **Examen** con preguntas aleatorias que no se repiten y nota al final.

**Reconocimiento de signos con IA**
1. **Captura del dataset**: un script con OpenCV hace fotos con la webcam para cada letra (`0.5_version/training/recordScript`).
2. **Etiquetado** de las imágenes con [labelImg](https://github.com/HumanSignal/labelImg) (cajas en formato Pascal VOC).
3. **Entrenamiento** de un modelo [YOLOv5](https://github.com/ultralytics/yolov5) en Google Colab.
4. **Conexión con la web** mediante Anvil Uplink: la web envía la foto, el modelo detecta la letra y devuelve el resultado.

Antes de YOLOv5 probé TensorFlow Object Detection (SSD MobileNet), en `PaginaWeb/Codi_IA_experimental`.

## Versiones

| Carpeta | Versión |
|---|---|
| `PaginaWeb/` | v0.21: web de aprendizaje y primeros experimentos de IA |
| `0.5_version/` | v0.5: web conectada al modelo YOLOv5 |
| `TR_V.0.5_English_American/` | v0.5 adaptada a la lengua de signos americana (ASL) |

## Tecnologías

Python · Anvil · YOLOv5 (PyTorch) · OpenCV · labelImg · Google Colab · Jupyter

## Limitaciones

- El dataset es muy pequeño (pocas fotos por letra, todas hechas por mí) y solo cubre algunas letras (en el repo, la I, la O y la U), así que el modelo no generaliza bien a otras manos ni fondos.
- Reconoce letras estáticas en una foto, no signos en movimiento ni vídeo en tiempo real.

## Lo que haría hoy

- Usar puntos clave de la mano (por ejemplo, MediaPipe Hands) en lugar de detección de objetos, que pide muchos menos datos.
- Ampliar el dataset con más personas y fondos.
- Reconocimiento en tiempo real con vídeo.
