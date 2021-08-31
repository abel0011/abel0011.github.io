---
title: Scripting Bash
published: true
---

Bash interfaz de usuario de linea de comandos, especificamente una shell de unix,
asi como un lenguaje de scripting, es el caparazón del proyexto GNU

<hr>
**Movilidad en gnu/linux**
==========================
<hr>
~~~
~$ mkdir bash => creando directorio "bash"
~~~

~~~
~$ cd !$ => ingresando al directorio recién creado "bash"
~~~

~~~
~$ touch - => crear fichero "-"
~~~

~~~
~$ echo "cadena de caracteres" > - => ingresando cadena de caracteres al fichero "-"
~~~

~~~
~$ cat ./- => mostrar contenido del fichero que esta en "-"
~~~

~~~
~$ pwd => print working directory, imprimir directorio de trabajo
~~~

~~~
~$ cat /home/user/carpeta/bash/- => mostrando el archivo desde su ruta absoluta
~~~

~~~
~$ $(pwd) => recepciona el output de pwd
~~~

~~~
~$ cat $(pwd)/- => mostrar el contenido de "-"
~~~

~~~
~$ cat $(pwd)/* => mostrar el contenido de todos los ficheros que se encuentren en esa ruta
~~~

~~~
~$ time $(pwd) => muestra el tiempo de ejecución de un comando
~~~

<br>
<hr>
**Sesión Dos**
==============
<hr>

~~~
~$ mkdir "espacio en blanco" => creando un directo con espacios en blanco
~~~

~~~
~$ cd "espacio en blanco" => change directory, cambiamos de directorio
~~~

~~~
~$ cd espacio\ en\ blanco  => cambiando de directorio
~~~

~~~
~$ touch "fichero con espacios" => creando fichero
~~~

~~~
~$ echo $(cat /etc/hosts) > fichero\ con\ espacios => redirigiendo la salida del comando al fichero con espacios
~~~

<br>
<hr>
**Expreciones Regulares**: secuencia de caracteres y metacaracteres que forma un patrón de búsqueda, para la búsqueda de patrones de cadenas de caracteres u operaciones de sustituciones.


Fuente <https://francisconi.org/linux/expresiones-regulares>
<hr>
<br>
~~~
~$ cat "fichero con espacios" => mostrar el contenido del fichero
~~~

~~~
~$ cat fichero\ con\ espacios => mostrar el contenido del fichero
~~~

~~~
~$ cat fi* => mostrar el contenido del fichero que comienze con "fi" y posteriormente cualquier cosa "*"
~~~

~~~
~$ cat *os => mostrar el contenido del fichero que comienze con cualquier cosa "*" y termine en "os"
~~~

~~~
~$ cat /home/user/carpeta/bash/"espacio en blanco"/* => mostrar el contenido de todos los ficheros de la ruta actual
~~~

~~~
~$ cat "$(pwd)"/* =>mostrar todo el contenido de todos los ficheros de la ruta actual
~~~

~~~
~$ cat * => mostar todo lo que se encuntre en este directorio o ruta
~~~

~~~
~$ =>
~~~

~~~
~$ =>
~~~

~~~
~$ =>
~~~

~~~
~$ =>
~~~

~~~
~$ =>
~~~

~~~
~$ =>
~~~

~~~
~$ =>
~~~

~~~
~$ =>
~~~
