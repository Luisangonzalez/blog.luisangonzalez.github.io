title: Sublime Text 2 en Ubuntu 14.04
tags:
  - Sublime Text
categories:
  - Linux
  - Ubuntu
date: 2015-02-23 23:51:00
---

Muy buenas ;)

Los pasos para instalar Sublime Text 2 en Ubuntu 14.04:

* Descargar de su web http://www.sublimetext.com/2 en 64bit en mi caso y (Ubuntu 14.04).

* Una vez descargado descomprmir y dar permisos totales :

```
$ sudo chmod -R 777 ./Sublime2
```

* Doble click en sublime_text o ejecutarlo :

```
$ ./Sublime2
```

Una vez descargado para no tener que ir cada vez que quiera ejecutarlo a la carpeta lo añado al path de mi equipo añadiendo las siguientes lineas a .bashrc ( se encuentra en la carpeta home oculto)


```
export SUBLIME_HOME=~/Sublime2
export PATH=${PATH}:$SUBLIME_HOME
```



Indicar que yo he descargado Sublime Text 2 en mi directorio home ~/ y que he renombrado la carpeta a Sublime2 para no tener problemas con los espacios.
