---
title: Managing Tmux
published: true
---

Acompañe a aprender a **gestionar** una herramienta muy potente, **tmux** es un multiplexador de terminales que permite lanzar múltiples terminales.

Esta información es una recopilación de  <https://www.youtube.com/watch?v=1dDahc214co>

Personaliza tmux con el tema !Oh my tmux! <https://github.com/gpakosz/.tmux>

Manual de tmux <https://man.openbsd.org/OpenBSD-current/man1/tmux.1>

# [](#header-1)Gestión de la herramienta tmux

    tmux new-session -s "Nueva sesión" => creación de una nueva sesión

![nueva sessión](./../assets/tmux/sesion-iniciada.PNG)

    [ctrl + b] + , => renombrar el panel actual  

![renombrando panel](./../assets/tmux/renombrando-panel.PNG)

    [ctrl + b] + c => crear un panel nuevo

![creadno un nuevo panel](./../assets/tmux/nuevo-panel.PNG)

    [ctrl + b] + 3 => navegando al tercer panel

![redirigiendo al segundo panel](../assets/tmux/tercer-panel.PNG)

    [ctrl + b] + $ => renombrando sesión

![renombrando sesión](./../assets/tmux/renombrando-sesion.PNG)

    [ctrl + b] + " => split horizontal del panel actual

![split horizontal](./../assets/tmux/split-horizontal.png)

    [ctrl + b] + % => split vertical del panel actual

![split vertical](./../assets/tmux/split-vertical.png)

    [ctrl + b] + x => cerrar el panel actual

![cerrar panel](./../assets/tmux/cerrar-panel-actual.png)

    [ctrl + b] + & => cerrar la session

![cerrar sessión](./../assets/tmux/cerrar-sesion.png)

    [ctrl + b] + space => mover los paneles en la dirección de las agujas del reloj

![mover los paneles](./../assets/tmux/mover-panel-reloj.png)

    [ctrl + b] + } => alternar paneles

![alternar paneles](./../assets/tmux/alternar-panel.png)


    [ctrl + b] + m => activar el uso del mouse

![activar el uso del mouse](./../assets/tmux/modo-mouse.png)

    [ctrl + b] + [up, down, left, right] => redimensionar el panel actual con el uso de las flechas

![redimensionar el panel](./../assets/tmux/resize-panel.png)

    [ctrl + b] + [shift + 1] => mover el panel actual a uno nuevo

![mover el panel actual a uno nuevo](./../assets/tmux/move-current-panel.PNG)

    [ctrl + b] + (shift + [ ) => activar el modo copia

![modo copia](./../assets/tmux/modo-copia.png)

    [ctrl + space] => una vez ingresado en el modo copia, activas el modo selección

![modo selección](./../assets/tmux/modo-seleccion.png)

    [ctrl + s] => una vez ingresado en el modo copia, activas el modo busqueda

![modo busqueda](./../assets/tmux/modo-busqueda.png)

    [ctrl + w] => copias lo que has seleccionado ( presiona q para salir del modo copia)

![copiar la selección](./../assets/tmux/copiar-texto.png)

     tmux list-session => mostrar las sesiones activas

![mostrar sesiones](./../assets/tmux/session-list.png)

    tmux attach -t "test" => ingresar a la sesión especificada

![ingresar a la sesión](./../assets/tmux/ingresar-sesion.png)

    [ctrl + b] + s => previsualización de las sesiones activas (q para salir de esta previsualización)

![sesiones activas](./../assets/tmux/sesiones-activas.png)

    [ctrl + b] + w => previsualización de las sesiones con su jerarquía

![visualización jerarquíca](./assets/tmux/jerarquia-sesiones.png)

    [ctrl + b] + q => visualización de los números identificativos de cada panele

![vidualización de los números identificativos](./assets/tmux/numero-panel.png)

    [ctrl + b] + t => mostrar la hora en el panel actual

![mostrar hora](./../assets/tmux/hora.png)

    [ctrl + b] + (:join -s 1 -t 2) => unir el panel uno con el segundo panel

![unir panel](./../assets/tmux/unir-panel.png)

    [ctrl + b] + (:swap-window -s 2 -t 1) => alternar el segundo panel a la primera posición

![alternar el segundo panel](./../assets/tmux/swap-panel.png)

