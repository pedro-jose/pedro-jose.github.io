### Creación de blogs con Jekyll y GitHub Pages

Jekyll es un generador de sitios web estáticos que nos permite crear de forma sencilla blogs, sitios webs personales o webs para proyectos. En esta practica vamos a postear dos de las practicas hechas en este curso.

##  Tareas a realizar
## 1. Paso1
Crearemos la estructura de directorios y los archivos necesarios de un nuevo proyecto Jekyll, para ello utilizaremos este comando.

`docker run -it --rm -v "$PWD:/srv/jekyll" jekyll/jekyll jekyll new blog`

## 2. Paso 2
 Generaremos un sitio HTML estático a partir del contenido del proyecto Jekyll mediante este comando.

 `docker run -it --rm -v "$PWD:/srv/jekyll" jekyll/jekyll jekyll build`

 ## 3. Paso 3
 Por último serviremos un sitio HTML estático generado a partir del contenido del proyecto Jekyll, ejecutando este comando.

 `docker run -it --rm -p 4000:4000 -v "$PWD:/srv/jekyll" jekyll/jekyll jekyll serve --force_polling`
