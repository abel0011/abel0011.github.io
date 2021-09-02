---
title: Scripting Bash
published: true
---

Bash interfaz de usuario de linea de comandos, especificamente una shell de unix,
asi como un lenguaje de scripting, es el caparazón del proyexto GNU


El contenido presentado es una recopilación de <https://www.youtube.com/watch?v=RUorAzaDftg>

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

<br>
<hr>
**Sesión Tres**
==============
<hr>

~~~
~$ ls -a => listar ficheros ocultos 
~~~

~~~
~$ find . => mustrame todo el contenido partiendo de la ruta actual
~~~

~~~
~$ find -type f => encuentrame solo los ficheros
~~~

~~~
~$ find -type f -printf "%f\t%u\t%g\t%m\n" | column -t 
   => -printf : me imprima
   => %f : ficheros
   => t%p : de forma tabula me indiques la ruta absoluta
   => t%u : de forma tabulada  me indiques el usuario propietario
   => t%g : de forma tabulada me indiques el  grupo asignado
   => t%m : de forma tabulada me indiques el modo (permiso asignado a niver numerico )
   => \n : salto de linea, para formatear el output 
   => -t : formatea el output en una tabla
~~~

~~~
~$ touch .hidden => crear un fichero oculto
~~~

~~~
~$ echo "este fichero no es visible" > .hidden => agregando cadena de caracteres al fichero
~~~ 

~~~
~$ cd / => cambiando de directorio a la ruta raiz
~~~

~~~
~$ find . -name .hidden 2>/dev/null => encuentrame el fichero ".hidden" partiendo del directorio actual
~~~

~~~
xargs: ejecuta un comando de forma paralela, con el output del comando ejecutado anteriormente
~~~

~~~
~$ find . -name .hidden | xargs cat => encuntrame el fichero ".hidden" y asu vez muestrame su contenido
~~~

~~~
~$ find . -type f | xargs grep "este fichero" 2>/dev/null => encuentra el fichero con el contenido "este fichero"
~~~

<br>
<hr>
**Sesión Cuatro**
==============
<hr>

~~~
permisos en linux
.rwxrwxrwx .hidden 
r - 4 => read
w - 2 => write
x - 1 => execute
(rwx)  (--x) (--x)
 111    001   001 
 2^0=1  2^0   2^0
 2^1=2
 2^2=4
   6     1      1
~~~

~~~
~$ sudo useradd pepito => creando usuario pepito (por defecto se crea un grupo con su mismo nombre)
~~~

~~~
~$ mkdir directorio_pepito => creando directorio
~~~

~~~
~$ chgrp pepito directorio_pepito => change group, asignando el grupo pepito a la carpeta "directorio_pepito"
~~~

~~~
~$ chown pepito directorio_pepito => asignando a pepito como usuario propietario de la carpeta
~~~

~~~
~$ chown pepito:pepito directorio_pepito => asignando usuario y grupo a la carpeta "directorio_pepito"
~~~

~~~
~$ chattr +i -V .hidden => asignando privilegio especial para no eliminar el archivo (ni siquiera root)
~~~

~~~
~$ lsattr => ver los privilegios especiales
~~~

~~~
~$ touch fichero2 && cd / => creando el "fichero2" y a su vez dirigiendome a la ruta raiz
~~~

~~~
~$ find . -name "fich*" => encuntrame al fichero que comience con "fich" y cualquier cosa "*"
~~~


~~~
~$ which file => mostrar la ruta absoluta del binario "file" dentro del PATH
~~~

~~~
~$ echo $PATH => mostrar la ruta del PATH
~~~

~~~
~$ sudo apt install mlocate => instalando herramienta en ubuntu
~~~

~~~
~$ sudo updatedb => creando la base de datos de los ficheros del sistema
~~~

~~~
~$ locate fichero => realizando busqueda de "fichero"
~~~

~~~
~$ touch script.sh && chmod +x script.sh && nano script.sh => creando archivo "script", asignando permiso de ejecución y editando el archivo
~~~

~~~bash
#!/bin/bash
echo -e "te encuentras en esta ruta [ $(pwd) ]"
~~~

~~~
~$ file script.sh=> determina el tipo y formato de un archivo (para realizar esto, hace uso de los "magic numbers")
~~~

~~~
~$ touch fichero.txt && nano fichero.txt => creando "fichero.txt" y editando fichero
~~~

~~~
GIF8; => ingresa esto en el "fichero.txt"
~~~

~~~
~$ file fichero.txt => nos mostrar un fichero GIF, esto se debe a los "magic numbers" (47 49 46 38 3B ...	)
~~~

<hr>
**Scrub**: escribe patrones de forma iterativa en archivos o dispositivos de disco para dificultar la recuperación de los datos


**Shred**: herramienta de eliminación de archivos de modo seguro

Fuente: <https://www.computertechblog.com/using-scrub-command-to-secure-erase-data-in-redhat-linux/>
				<https://www.welivesecurity.com/la-es/2014/11/24/como-hacer-borrado-seguro-shred-linux/>
<hr>

~~~bash
function rmk(){
  scrub -p dod $1
  shred -zun 10 -v $1
}
# ingresar el el ~/.bashrc o ~/.zshrc
# z: zero, sobreescribe 0 para evitar dejar rastro
# u: trunca y elimina el archivo después de sobrescribirlo
# n: número de veces a sobrescribir el archivo o partición 
#(3 veces por defecto). Cuanto mayor sea este número, más difícil será su recuperación
# v: verbose o verborragico, muestra el progreso en pantalla

~~~
<br>
<hr>
**Sesión Cinco**
==============
<hr>

~~~
~$ file directorio/* => mostrar que tipo y formato de archivos hay en "directorio"
~~~

~~~
~$  mkdir example && cd example && touch fichero.jpg fichero.png fichero.txt fichero2.txt && echo "texto" > fichero2.txt && cd ..
=>creando directorio, con ficheros
~~~

~~~
~$ find . -name "ficher*" | xargs file 
=> encontrar desde la ruta actual todos los ficheros que coincidan con "ficher",
y cualquier cosa "*". A su vez me muestre el formato y tipo de archivo
~~~

~~~
~$ time find . -name "ficher*" | xargs file 
=> time: nos muestra el tiempo de computo del comando
~~~

~~~
~$ time find example/* => disminuye el tiempo de computo de computo 
~~~

~~~
~$  find . -name fichero2.txt | xargs cat
=> realizando una busqueda de "fichero2.txt" y mostrando su contenido
~~~

~~~
~$ cat $(find . -name fichero2.txt) 
=>mostrando el contenido del output del comando entre "$()"
~~~

~~~
ctrl + r => realizando búsqueda de comandos previamente ejecutados
~~~
<br>
<hr>
-writable => ficheros en los se puede escribir


-executable => ficheros que se pueden ejecutar


-readable => ficheros que se pueden leer
<hr>
~~~
~ $
~~~
