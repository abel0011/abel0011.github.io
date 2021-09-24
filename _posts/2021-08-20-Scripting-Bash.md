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
**Busqueda de archivos con el comando find**: herramienta que nos permite la busqueda de
archivos, directorios y otros objetos buscando más allá del nombre


Fuente: <https://laguialinux.es/buscar-archivos-comando-find/>


-writable => ficheros en los se puede escribir


-executable => ficheros que se pueden ejecutar


-readable => ficheros que se pueden leer
<hr>
~~~
~$ mkdir example2 && cd example2 && touch script.txt && echo "tengo contenido" > script.txt && cd ..
~~~

~~~
~$ find . -type f -readable ! -executable -size 1k
=> encontrar ficheros, que tengan permiso de lectura,
=> que no se puedan ejecutar y que tengan de tamaño
=> 1 kylobyte
~~~

~~~
~$ find . -type f -readable ! -executable -size 1k | xargs cat 
=> realizando una lectura del output del comando anterior
~~~

~~~
~$ at $(find . -type f -readable ! -executable -size 1k)
=> realizando lectura del comando entre "$()"
~~~

~~~
~$ cat $(find . -type f -readable ! -executable -size 1k) | xargs
=> formateo de la cadena de texto con xargs 
~~~

~~~
~$  cat $(find . -type f -readable ! -executable -size 1k) | tr -d ' ' 
=> tr: sive para realizar sustituciones
=> -d ' ' eliminar los espacios en blanco 
~~~

~~~
~$ nano example2/script.txt => editando archivo (copiar este contenido)
------------------------------------------------
Tr es un comando de linux 

para realizar 

sustituciones
~~~

~~~
~$ cat $(find . -type f -readable ! -executable -size 1k) | tr -d "\n"
=> tr -d "\n" eliminar saltos de linea
=> tr -d "\t" eliminar tabulaciones
~~~

~~~
~$ cat /etc/passwd | head -n 3
=> head -n 3 : muestrame las 3 primeras lineas
=> tail -n 3 : muestrame las 3 ultimas lineas
~~~

~~~
~$ wc -l /etc/passwd
=> (word count, lines) contar el número de linas de 
=> "/etc/passwd" 
~~~

~~~
~$ awk 'NR==3' /etc/passwd
=> mostar solo la tercera linea de "/etc/passwd"
~~~
<br>
<hr>
**sed**: (stream editor) sirve para buscar, buscar y remplazar, insertar o eliminar


Fuente: <https://www.ochobitshacenunbyte.com/2019/05/28/uso-del-comando-sed-en-linux-y-unix-con-ejemplos/>
<hr>
~~~
~$ sed 's/root/bash/' /etc/passwd | head -n 1 
=> 's/root/bash/' remplaznaod la palabra "root" por "bash" de
=> la primera coincidencia
=> head -n 1 mostrando la primera fila de "/etc/passwd"
~~~

~~~
~$ sed 's/root/bash/g' /etc/passwd | head -n 1
=> 's/root/bashh/g' realizar sustitución de manera global
~~~

~~~
~$ nano example2/script.txt 
---------------------------



     aprendiendo script
     en bash
     copialo con espacios y saltos de linea
~~~

~~~
~$ cat $(find . -type f -writable -readable ! -executable -size 1k) | sed 's/^ *//g' 
=> realizando una sustitución por todo lo que conience '^' en " " y cualquier cosa "*",
=> de manera global
~~~

~~~
~$ sudo awk '{print $1}' FS=':' /etc/passwd
=> '{pritn $1}': imprimeme el primer argumento
=> FS=':': utilizando como delimitador ":"
~~~

~~~
~$ cat script.txt | sed '/^\s*$/d' 
^\s => cualquier cosa que empiece por espacios
*   => segido de la que sea
$/d => y que termine en vacio
~~~

~~~

~$ cat aksdf 2>&1 => cambiando el stderr al stdin
~$ firefox >/dev/null  2&>1  &
=> redirigir el flujo del programa al "/dev/null",
convertir sderr al stdin "2&>1",
todo va redirigido al /dev/null, 
el "&" poner el procesos en segundo plano
disown => independizar tareas 
( convertir un procesos hijo a un proceso padre, la terminal proceso padre )
~~~

~~~
~$ find  / -type f -user pepito -group pepito -size 33c 2>/dev/null
find / => partiendo desde la ruta raiz
-type f => busque todo los archivos que sean ficheros
-user pepito => tomando como usuario "pepito"
-group pepito => tomando como grupo "pepito"
~~~

~~~
wc -l => cuentame todas las linas que hay "-l" ( word count )
wc -c => cuentame la cantidad de caracteres "-c"
~$ cat data.txt | wc -l => cuentame el numero de lineas que hay  en el fichero
~$ cat data.txt | grep "millionth" => esto no es optimo, mostrar el contenido de un fichero para luego hacerle un grep
~$ grep "millionth" data.txt => hacer un grep de un criterio en el fichero "data.txt"
~$ awk '/millionth/' data.txt => hacer un grep con awk, con la palabra '/millionth/' en el fichero "data.txt"
~~~

~~~
~$ awk '/millionth/' data.txt | awk '{print $2}' 
=> realizando un filtrado del segundo argumento "'{print $2}'"
~~~

~~~
~$ awk '/millionth/' data.txt | awk 'NF{print $NF}' 
=> "'NF{print $NF}'" filtrando el ultimo elemento de la linea actual en la que me situo
~~~

~~~
~$ echo "hola que tal" | cut -d ' ' -f 2
=> toma como argumento los spacios en blanco
-d ' ' => utilizando como delimitador el espacio en blanco
-f 1 => filtrando solo el primer argumento
~~~

~~~
~$ echo "hol   que tal" | cut -d ' ' -f 2 
=> va devolver un espacio en blanco ya que el segundo argumento,
es un espacio en blanco
~~~

~~~
~$ awk '/millionth/' data.txt | rev | awk '{print $1}' | rev
rev => revertir la cadeana
awk '{print $1}' => impirmiendo el primer agumento
rev => revirtiendo la cadana para que vuelva 
a su estado orginal y no se lea al reves
~~~

~~~
~$ grep "millionth" data.txt -n 
=> realizando un filtrado por "millionth", sobrel el fichero data.xt,
 "-n" muesta el numero de la fila
~~~

~~~
awk 'NR==27262' data.txt 
=> number row (numero de la fila), muestrame lo que haya en la fila 27262 de data.txt
~~~
~~~
awk 'NR==27262{print $2}' data.txt 
=> mostrando el segundo argumento de la fila 27262 del fichero data.txt
~~~

~~~
uniq => comando para ver cadenas unicas, entre otras utilidades (uniq --help)

~$ cat data.txt | wc -l 
=> contar el numero de lineas del fichero data.txt
~~~

~~~
~$ cat data.txt | sort  
=> realizando un ordenamiento alfabetico con "sort"
~~~

~~~
~$ cat data.txt | sort | uniq -u 
=> me muestre solo las cadenas que no re repeten, 
(tenemos que hacer el ordenamiento para facilitar el uso de uniq)
~~~

~~~
~$ sort data.txt | uniq -u 
=> forma mas adecuada de realizar el ordenamiento, "-u" listar cadenas de forma unicas
~~~

~~~
strings data.txt => listar lista de caracteres imprimibles de un fichero
~~~

~~~
strings data.txt | grep "==" | tail -n 1 | awk 'NF{print $NF}'
strings data.txt => mostrar caracteres imprimibles del fichero data.txt
grep "==" => realiza un grep con el elemento "==" (buscar en el archivo con las coincidencias "==")
tail -n 1 => obteniendo la  primera fila de la ultimas lineas
awk 'NF{print $NF}' => obteniendo el ultimo elemento de la fila en la que me situo
~~~

~~~
realizando un bucle read line
-------------------------------
nano bulce.sh
chmod +x !$
nano !$
~~~~

~~~bash
*******************************************************
#!/bin/bash

#while read line
#bucle de read line

#Forma no optima de hacerlo
#============================
#cat /etc/passwd | while read line; do
#       echo "Estamos aqui  => $line"
#done


#Forma optima de hacero
#las variables tienen que estar sin espacios

contador=1

while read line;do
        echo "Linea $contador:  => $line"
        let contador+=1
done < /etc/passwd #Indicando que archivo quieres leer
********************************************************
~~~

~~~bash
contador=1; while read line; do; echo "$contador.-número => $line"; let contador+=1; done < /etc/passwd 
#en una sola linea
~~~

~~~
contador=1; strings data.txt | grep '==' | while read line; do echo "linea $contador : $line"; let contador+=1; done | awk 'NR==4' | awk 'NF{print $NF}'
contador=1; => declarando contador
strings data.txt => mostrando caracteres legibles del fichero data.txt
grep '==' => mostrando lo que coincida de la expreción regula '=='
while read line;do echo "linea $contador: $line"; let contador+=1; done => realizando bulce para mostrar las lineas
awk 'NR==4' => mostrando solo la linea 4
awk 'NF{print $NF}' => mostrando el ultimo argumento, del output de la fila en la que me encuentro situadoo
~~~

~~~
echo "cambiando a base 64" | base64 => convirtiendo a base 64
~~~

~~~
echo "Y2FtYmlhbmRvIGEgYmFzZSA2NAo=" | base64 -d => decodificar base 64
~~~

~~~
echo $(cat data.txt) |base64 -d => utilizando el output anterior, decodificando en base64
~~~

~~~
echo $( cat data.txt ) | base64 -d | tr ' ' '\n' 
=> conviertiendo los espacios en blanco "' '" en saltos de linea "'\n'" (solo acepta un
caracter de sustitucion )
~~~

~~~
echo $( cat data.txt ) | base64 -d | sed 's/ /--/' => sustituyendo los espacios con dos guiones "'--'"
~~~

~~~
echo $( cat data.txt ) | base64 -d | sed 's/ /---/g' => sustituyendo de manera global
~~~

~~~
cat /etc/passwd | head -n 1 | tr 'o' '0'
head -n 1 => seleccionando la primera linea del output
tr 'o' '0' => sustituyendo todas las o por el 0
~~~

~~~
echo $( cat data.txt ) | base64 -d | awk 'NF{print $NF}'
NF{print $NF}  => obtenendo el ultimo elemento de la linea en donde me situo
~~~

~~~
a b c d e f g h i  k  l  m  n  ñ  o  p  q  r  s  t  u  v  w  x  y   z
1 2 3 4 5 6 7 8 9  10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26

~$ cat data.txt | tr '[G-ZA-Fg-za-f]' '[T-ZA-St-za-s]'

[G-ZA-Fg-za-f] => el texto nos muestra que comienza en la g,
(partiendo desde g rote 13 posiciones) haci que partimos de la G a la Z
y lo que caracteres que sobran de la A a la F (repetimos para que haga el mismo proceso en minuscula )

[T-ZA-St-za-s] => contamos las 13 posiciones de la a hasta la T,
entnces de la T hasta la Z y de los caracteres que faltan de la A a la S (lo mismo con minusculas )
~~~

~~~
~$ echo "convirtiendo ha hexadecimal " | xxd => convirtiendo la cadena a hexadecimal con "xxd"
~~~

~~~
~$ echo "hola que tal " | xxd -ps => mostrando solo el formato hexadecimal
~~~

~~~
~$ echo data.txt | xxd -r
-r => revertir el hexadecimal
~~~

~~~
reset => resetear
file fichero => ver con que tipo de archivo estamos tratando
7z => es para descompresión universal
~$ 7z -l data.gzip => listame el contenido que estoy descomprimiendo sobre este comprimido
~$ 7z x data.gzip => extrame el archivo data.gzip
~~~

~~~
~$ 7z l data.gzip | grep "Name" -A 3
grep "Name" -A 3 => desde la concidencia "Name" muestrame 3 lineas hacia abajo 
(-B muestrame hacia arriba) (-C muestramelineas por debajo y por encima )
~~~

~~~
echo $? => bit de estado ( 0 = exitoso ) ( 1 = error )
utilidad decompressed.sh => buscar en github
~~~

~~~
( clave privada ssh ) conceptos de ssh
-----------------------------------------
/root/.ssh => directorio ssh
/etc/ssh/sshd_config => habilitar un component ( indispensable {search = PermitRootLogin }
{agregar = PermitidRootLogin yes} )

service ssh start => iniciar servicio ssh
service ssh restart => resetear servicio ssh
service ssh status => ver el estado del servicio ssh

ssh-keygen => generando clave ssh, se almacenara como /root/.ssh/id_rsa, 
te va pedir que le proporciones una contraseña,
la contraseña se puede romper con a utilidad john (id_rsa clave privada , id_rsa.pub clave publica)


Como administrador de red hay ocaciones en las que proporciono la clave
id_rsa.pub en el directorio /root/.ssh,
con el nombre authorized_keys
ssh-copy-id -i id_rsa root@localhost
ss-copy-id => utilidad para usar la clave privada ssh
-i => identificar el fichero de la clave privada
root@localhost => para el usuario root y la maquina localhost

el otro usuario
----------------
ssh -i id_rsa root@localhost
-i => indicar fichero de identidad
root@localhost => para el usuario root y localhost

ssh -i sshkey.private bandit14@localhost
ssh -i sshkey.private => ingresando desde ssh con el fichero sshkey.private
bandit14@localhost => al usuario bandit14 desde localhost
cat /etc/bandit_pass/bandit14 => ruta del passwd de bandit 14

lsof -i:80 => que procesos estan corriendo bajo el puerto 80

pwdx 1234 => desde que ruta se ha ejecutado el proceso con el numero identificador (PID)
~~~

~~~
~$ echo '' >/dev/tcp/127.0.0.1/30000 
=> enviando una cadena vacia a la ruta por el puerto 30 000
~~~

~~~
~$echo '' >/dev/tcp/127.0.0.1/30000 && echo "[*] Puerto abierto" 
=> si el primer comando es verdadero muestrame el mensaje
~~~
~~~
bash -c "" => modo consola o interactivo, quiero ejecutar un comando englobado entre "", 
con esto ya podemos redirigir el stderr
~~~

~~~
~$ bash -c "echo '' >/dev/tcp/127.0.0.1/30123" 2>/dev/null && echo "[*] Puerto abierto" || echo "[x] Puerto Cerrado"
~~~

~~~
~$ netcat = nc => abreviatura de netcat
~~~

~~~
~$ echo "4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e" | nc localhost 30000
echo "" => enviando una cadena
nc => con netcat
localhost 30000 => a localhost sobre el puerto 30000
~~~
~~~
telnet localhost 30000 => abriendo un conexion con telnet
posteriormente enviamos la cadena "" y presionamos enter
~~~

~~~
En este nivel se utiliza ssl(no podemos utilizar telnet ni netcal ya que la conexion esta cifrada)

~$ openssl s_client -connect localhost:30001

~$ openssl s_client => utilizando openssl, como cliente "s_client"
-connect => quiero conectarme
localhost:30001 => a localhost sobre el puerto 30001
~~~

~~~
nmap --open -T5 -v -n -p31000-32000 127.0.0.1

--open => muestrame todos los puertos que se encuentren abiertos
-T5 => setTimeout de 5 (el modo mas agresivo y ruidoso)
-v => modo verbose para que me reporte el resultado en consola
-n => que no aplique resolución dns
-p31000-32000 => sobre el rando de puertos 31000-32000
127.0.0.1 => sobre la ip local
~~~

~~~
mktemp -d => crear directorio temporal
nos dirigimos al directorio, creamos un fichero id_rsa y pegamos la clave privada
chmod 600 id_rsa => la clave debetener esos permisos para ser utilizasa
~~~

~~~
ssh -i id_rsa bandit17@localhost
-i => proporciono la clave privada que esta en el fichero que le indico
bandit17@localhost => me conecto a bandit17 sobre localhost
~~~

~~~
comparando ficheros con diff
----------------------------

~$ diff password.old password.new => listame las diferencias

< aksldjas => significa que se ha eliminado esa linea
> qkqqqq   => significa que se ha agregado esa linea
~~~

~~~
~$ ps -eo command => listar todos los comandos que se ejecutan a nivel de sistema en nuestro equipo
~~~

~~~
~$ cat /etc/passwd | head -n 5 | grep -v -E "root|sys"
-v => nos quita la linea que tenga el criterio que le indicamos
-E => para filtrar multiples campos
~~~

~~~
~$ cat /etc/passwd | grep -E "^root|hack" => realizando filtrado con multiples campos
~~~

~~~
~$ cat /etc/passwd | grep -E "^root\|^hack" => escapando del pipe con "\"
~~~

~~~
 ssh bandit18@bandit.labs.overthewire.org -p 2220 whoami => me da tiempo de realizar la ejecución del comando whoami
 ssh bandit18@bandit.labs.overthewire.org -p 2220 bash => asignando una bash en el breve tiempo que nos asignan
~~~

~~~
./bandit20-do sh => ejecutando un comando con el usuario propietario del fichero (SUID)
./bandit20-do bash -p => "-p" para que nos permita el permiso SUID
~~~

~~~
./subcontent 5757 => ejecutando la script de bandit 20
nc -nlvp 5757 => pornerme en escucha con netcat, sobre el puerto 5757
~~~

~~~
~$ echo "prueba" | md5sum => realizando hash en md5
~~~

~~~
~$ watch -n 1 ls -l
watch -n 1=> que nos muestre cada segundo (monitorizando)
ls -l => monitorizando el comando "ls -l" cada segundo
~~~

~~~
~$ for i in $(seq 1 100); do echo "el numero es $i"; done => seq de secuenciador
~~~

~~~
for i in {0001..9999}; do echo "$i : numero}; done => realizando secuenciador con "0001"
~~~

~~~
~$ cat dictionary.txt | nc localhost 30002 | grep -v -E "Wrong|Please"
~~~

~~~
~$ cat dictionary.txt | nc localhost 30002 
=> emitiendo datos al localhost sobre el puerto 30002 con netcat
grep -v -E => "-v" eliminar las lineas que tengas las coincidencias escritas, 
"-E" filtrar por multiples camps
~~~~

~~~
~$ more /etc/passwd => te carga el archivo, sin ocupar toda la pantalla
ssh -i bandit26.sshkey bandit26@localhost
presionamos "v"

escribimos
:e /etc/bandit_pass/bandit26 => podemos ver el contenido del fichero (flag bandit 26)
:set sell=/bin/bash => variable shell va valer /bin/bash
:shell => mostrar una shell
~~~

~~~
./bandit27-do whoami => ejecutando el ficheor de bandit 26 con permisos SUID
./bandit27-do bash -p => "-p" para que atienda a permisos suid
~~~

~~~
git clone ssh://bandit27-git@localhost/home/bandit27-git/repo
cat rep/README
~~~

~~~
git log --oneline => ver los commits del repository
git log --oneline -p => "-p" ver los cambios en cada commit
git log -p => mostrar en formato pagin
~~~~

~~~
git branch => ver en que rama estamos
git branch -r => listar las demas ramas del repositorio
git checkout dev => cambiando de rama a "dev" (desarrollo)
~~~

~~~
git tag => mostrar los tag del proyecto
git show secret => mostrando el contenido del tag "secret"
~~~

~~~
git push -u origin master => enviando commit al repositorio
~~~

~~~
echo "HOLA QUE TAL" | tr '[A-Z]' '[a-z]' 
=> convirteindo la cadena a lowecase
~~~

~~~
echo $0 => muestra el tipo de la terminal
~~~
