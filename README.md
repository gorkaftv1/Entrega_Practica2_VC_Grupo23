# Práctica 2: Procesamiento avanzado de imágenes y Detección de características

## Descripción

En esta práctica hemos realizado tareas avanzadas de procesamiento de imágenes utilizando OpenCV y Matplotlib, enfocándonos en la detección de bordes, umbralización, análisis de características y aplicaciones interactivas en tiempo real.

## Autores

- **Wail Ben El Hassane Boudhar**
- **Gorka Eymard Santana Cabrera**

## Requisitos

Para esta práctica se requiere un entorno de Python configurado con **Conda Prompt** y los siguientes paquetes instalados:
- **opencv-python**
- **numpy**
- **matplotlib**
- **PIL (Pillow)**

Para la instalación se utiliza la herramienta **pip**.

A continuación se configura Visual Studio Code para usar el kernel configurado.

## Desarrollo

### Tarea 1: Análisis de píxeles blancos por filas con detector Canny
- **Descripción**: Realizar el conteo de píxeles blancos por filas en la imagen resultante del detector de bordes Canny. Determinar el valor máximo de píxeles blancos por fila (maxfil) y mostrar las filas con un número de píxeles blancos mayor o igual que 0.90*maxfil.
- **Implementación**:
  - Aplicación del detector de bordes Canny a la imagen `mandril.jpg` con parámetros 100 y 200.
  - Uso de `cv2.reduce()` para contar píxeles blancos por filas.
  - Cálculo del porcentaje de píxeles blancos respecto al total de la fila.
  - Identificación y visualización de las filas que superan el 90% del máximo.
  - Visualización simultánea de la imagen Canny y el gráfico de respuesta por filas.
- **Resultado**: Análisis cuantitativo de la distribución de bordes horizontales en la imagen.

### Tarea 2: Umbralización y análisis comparativo con Sobel
- **Descripción**: Aplicar diferentes tipos de umbralización a la imagen en escala de grises y realizar análisis similar al de Canny, comparando los resultados obtenidos con ambos métodos de detección de características.
- **Implementación**:
  - **Umbralización binaria**: Aplicación de `cv2.threshold()` con valor umbral de 130 y tipo `THRESH_BINARY`.
  - Comparación visual entre los resultados de umbralización y Canny.
- **Resultado**: Comprensión de las diferencias entre métodos de segmentación y detección de bordes.

### Tarea 3: Demostrador interactivo multi-modo
- **Descripción**: Crear una aplicación interactiva que capture imágenes de la webcam y permita alternar entre diferentes modos de procesamiento haciendo clic con el ratón, mostrando las técnicas aprendidas en las prácticas.
- **Implementación**:
  - **Modo 0**: Visualización de la imagen original de la webcam.
  - **Modo 1**: Collage 2x2 con efectos de color:
    - Superior izquierda: Imagen original.
    - Superior derecha: Manipulación de canales RGB con inversiones y ajustes.
    - Inferior izquierda: Mosaico de triángulos usando `cv2.fillPoly()`.
    - Inferior derecha: Efectos de color adicionales con inversiones.
  - **Modo 2**: Collage de técnicas de umbralización:
    - Escala de grises, umbral binario, umbral inverso y rango de valores.
  - **Modo 3**: Aplicación del detector Canny en tiempo real.
  - Cambio de modo mediante clic del ratón (`cv2.setMouseCallback()`).
  - Reducción de resolución a la mitad para optimizar rendimiento.
- **Resultado**: Aplicación interactiva que demuestra múltiples técnicas de procesamiento en tiempo real.

### Tarea 4: Sistema de tiro virtual inspirado en instalaciones artísticas
- **Descripción**: Desarrollar un demostrador inspirado en las instalaciones interactivas como "My little piece of privacy", "Messa di voce" y "Virtual air guitar", implementando un sistema de tiro virtual con detección de movimiento.
- **Implementación**:
  - **Detección de movimiento**: Uso del sustractor de fondo MOG2 (`cv2.createBackgroundSubtractorMOG2()`) para detectar objetos en movimiento.
  - **Procesamiento morfológico**: Aplicación de operaciones de apertura y dilatación para limpiar la máscara de detección.
  - **Seguimiento de objetos**: Cálculo del centroide del objeto más grande detectado usando momentos (`cv2.moments()`).
  - **Interfaz de tiro**:
    - Carga y redimensionamiento de una imagen diana (`diana.png`).
    - Visualización en tiempo real del objeto detectado con círculo verde.
    - Sistema de marcado con barra espaciadora para fijar posición de disparo.
    - Sistema de disparo con Enter para registrar impactos.
    - Visualización de disparos acumulados en la diana con círculos rojos.
  - **Collage en tiempo real**: Visualización simultánea de la diana con impactos y la cámara con detección.
  - Controles: ESC para salir, Espacio para marcar posición, Enter para disparar.
- **Resultado**: Sistema interactivo de tiro virtual que combina detección de movimiento y seguimiento de objetos.

## Técnicas y Conceptos Implementados

- **Detección de bordes**: Algoritmo Canny para identificación de contornos.
- **Umbralización**: Técnicas binarias, inversas y por rangos para segmentación.
- **Análisis estadístico**: Conteo y análisis de distribución de píxeles por filas.
- **Sustracción de fondo**: MOG2 para detección de movimiento en tiempo real.
- **Operaciones morfológicas**: Apertura y dilatación para procesamiento de máscaras.
- **Cálculo de momentos**: Determinación de centroides para seguimiento de objetos.
- **Interfaz interactiva**: Manejo de eventos de ratón y teclado con OpenCV.
- **Procesamiento en tiempo real**: Optimización de rendimiento para aplicaciones webcam.

## Webgrafía

- [OpenCV Documentation - Canny Edge Detection](https://docs.opencv.org/4.x/da/d22/tutorial_py_canny.html)
- [OpenCV Documentation - Background Subtraction](https://docs.opencv.org/4.x/d1/dc5/tutorial_background_subtraction.html)
- [OpenCV Documentation - Morphological Transformations](https://docs.opencv.org/4.x/d9/d61/tutorial_py_morphological_ops.html)
- [My little piece of privacy - Niklas Roy](https://www.niklasroy.com/project/88/my-little-piece-of-privacy)
- [Messa di voce - Interactive Installation](https://youtu.be/GfoqiyB1ndE?feature=shared)
- [Virtual air guitar](https://youtu.be/FIAmyoEpV5c?feature=shared)
