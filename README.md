# Medidor de distancia social (PoC)

<p align="center">
<img src="temple_bar.gif" width="600">
</p>

De manera muy rápida se investiga la posibilidad de medir la distancia social COVID-19 usando OpenCV, Deep Learning y Computer Vision.
Este código está basado en el [siguiente artículo](https://www.pyimagesearch.com/2020/06/01/opencv-social-distancing-detector/).

Los pasos para construir un detector de distanciamiento social incluyen:

* Aplicar la detección de objetos para detectar a todas las personas (y solo a las personas) en una transmisión de video 
* Calcular las distancias por pares entre todas las personas detectadas
* De acuerdo a las distancias recogidas, verificar si dos personas están separadas por menos de `N píxeles`.

## Instalación del entorno
Recomendamos ejecutar el código en un `virtualenv` o `conda environment`:

```bash
$ conda env create -f environment.yml
```

```bash
$ pip install -r requirements.txt
```

## Cálculo de las distancias
Para su uso, símplemente ejecutamos:

```bash
python social_distance_detector.py --input input.mp4  \
	--output output.avi --display 0
```

## Aspectos a mejorar
El detector de distanciamiento social no aprovecha una calibración de cámara adecuada, lo que significa que no podíamos (fácilmente) mapear distancias en píxeles a unidades medibles reales (es decir, metros, pies, etc.).

Por lo tanto, el primer paso para mejorar nuestro detector de distanciamiento social es utilizar una calibración de cámara adecuada.

Una vez hecho esto hace, podremos calcular unidades medibles reales (en lugar de píxeles).

En segundo lugar, debe considerar aplicar una transformación de arriba hacia abajo de su ángulo de visión.