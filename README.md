# Draw_the_criminal
Este proyecto fue originalmente creado para participar en el reto #RetoDotCSV2080Super y possteriormente se continuara la mejoria para hacer una aportacion a la sociedad


Introducción: La idea surge a partir de el robo de celulares, un delito bastante común, por lo menos en México, donde la forma de proceder es hacer una denuncia en linea y entregarla a las autoridades, la denuncia es una breve descripción de los hechos, la hora, lugar, etc. etc. y a pesar de que existen camaras en el transporte publico, pareciera que no hay nada que se pueda hacer, la propuesta es permitir a los afectados, dibujar, a grandes rasgos como luce la persona que cometió el delito (en este punto se generaliza, asaltos, robos, vandalismo, etc) y a partir de ese bosquejo, se genera una imagen realista que tendría algún parecido a la persona que se describe, para facilitar su búsqueda, identificación e investigación.

Hacer una denuncia es algo parecido a lo siguiente.

![Encuesta de denunca anonima](./img_git_readme/CP_encuesta.png?raw=true "Encuesta")

En este repositorio hay unicamente la parte del modelo propuesto para generar las imagenes a partir de el bosquejo de las denuncias.

El dataset usado tiene por nombre CelebA, se puede consultar aqui http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html
El dataset contiene casi 200'000 imagenes, por temas de recursos y tiempo, se usaron solo mil de estas
Se descargo el archivo del dataset de nombre img_align_celeba, que contiene imagenes con caras centradas y se recorto la parte de la cara.
(para esto se uso el siguiente script de bash).

for x in $(ls img_align_celeba | head -n 1000); do python3 face_cropper_crop.py $x ; done

El resultado fue el siguiente:

Imagen antes del proceso:
<p align="center" font>
  Imagen original<br>
  <img src="./img_git_readme/000001.jpg">
</p>

Imagen despues del proceso:
<p align="center" font>
  Imagen recortada<br>
  <img src="./img_git_readme/000001_tg.jpg">
</p>

Preparacion del dataset:Se uso un pequeno programa de python que hace uso de OpenCV para aplicar un tratamiento a las imagenes, y fue ejecutado a travez de un ciclo de bash.
El procesamiento consistio en detectar los bordes de las caras,para asi simular un bosquejo de las caras y evitar hacerlo a mano.

for x in $(ls img_align_celeba | head -n 1000); do python3 face_cropper_border.py $x ; done

El resultado fue el siguiente:
<p align="center" font>
  Bordes de la imagen<br>
  <img src="./img_git_readme/000001_tg.jpg">
  <img src="./img_git_readme/000001_bor.jpg">
</p>

Posteriormente se hiceron pequenos cambios a el codigo propuesto por DOTCSV en su video (https://www.youtube.com/watch?v=YsrMGcgfETY&t=2691s) y se comenzo el entremamiento, a continuacion se presentan los resultados

<p align="center" font>
  Imagen generada<br>
  <img src="./img_git_readme/000005.jpg">
  <img src="./img_git_readme/Generada.jpg">
  <img src="./img_git_readme/000005_tg .jpg">
</p>
