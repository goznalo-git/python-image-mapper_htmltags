# Generador de mapas de imágenes (tags de html) automático

## Introducción
Cuando pasamos el ratón por encima de una web, en ocasiones se topa con links (URLs) a otras webs. En texto esto es sencillo, pero puede darse la situación de que tengamos una imagen, y dependiendo de dónde clickemos dentro de ella vayamos a una web u otra.

Esto se hace mediante un 'image-map', generado por un programa de edición de imagen (e.g. GIMP > Filters > Image Map). Cuando hemos de crear unos pocos rectángulos o círculos con URLs, esto es fácil de hacer a mano, pero más allá de unos pocos se vuelve una tarea tediosa y time-consuming. Ese es el caso de mapear bocas de switches, en especial en switches con más de 600 bocas (ver el SX6536).

Afortunadamente, las bocas de switches están repartidas de forma regular (aproximadamente, ver la sección de discusión). Por tanto, podemos entender la estructura en la que se reparten en cada switch (número de filas de bocas, columnas de bocas, número de grupos en los que dichas filas y columnas están, etc), y calcular, basándonos en unas posiciones iniciales que nos dicen cómo dar 'saltos', la posición de todas y cada una de las bocas existentes.

## El programa
Para llevar a cabo esta tarea he decidido usar Python, por su fácil manejo, y por la posibilidad de usar Jupyter Notebooks, que permiten testear cada parte del código por separado, poco a poco. Aun así, una vez terminado, junté cada pieza en una clase 'mapeador(...)', con sus atributos y métodos necesarios. 

La clase es usada para generar los mapeos .map resultantes, instanciando en cada caso (varios switches y dos CPDs) objetos que llevan a cabo la tarea, de forma elegante. Inicialmente sencilla, poco a poco he ido introduciendo más piezas a esta clase, desde particularidades y excepciones hasta opciones (enseñar ciertos outputs o no, empezar a contar bocas desde un número...). Al final ha quedado más complicada de lo que me gustaría, pero lleva a cabo su tarea.

## Contenido del repositorio
El repositorio contiene:
* Carpeta de imágenes `imagenes` (salvo las dos de los CPDs, por ser información confidencial)
* Carpeta de mapeos `mapeos`
* Carpeta `html_mapper` del virtual environment necesario
* Archivo `requirements.txt` para generar el virtual environment de cero
* Jupyter Notebook `html_tags_generator.ipynb` con el programa y los use-cases
* El presente `README.md`.

## Discusión

La vida, tristemente, no es idílica. Las imágenes de los switches no son perfectas milímetro a milímetro, y las capturas de los rectángulos/círculos iniciales es aun más imperfecta. Por ello, aunque el programa es de gran ayuda, no es la panacea, al final siempre me han hecho falta algunos retoques manuales (ligeros).


