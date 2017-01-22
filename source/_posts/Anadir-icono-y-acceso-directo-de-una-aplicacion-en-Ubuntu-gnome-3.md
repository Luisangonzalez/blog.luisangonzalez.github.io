title: Añadir icono y acceso directo de una aplicación en Ubuntu gnome 3
tags:
- Linux
- Ubuntu
categories:
- Linux
- Ubuntu
date: 2015-02-24 00:03:00
---
Buenas,

Utilizo Ubuntu 14.04 Gnome http://ubuntugnome.org/ y al instalar por ejemplo Sublime text 2 o Eclipse me ocurre que :

* No se puede ejecutar desde cualquier sitio con el términal y para ello es necesario agregar la ruta al PATH : http://luisangonzalez.es/2015/02/23/Sublime-Text-2-en-Ubuntu-14-04/

* Al buscarlo en el buscador no aparece, para este caso debemos:
  * Crear un archivo en en : `/usr/share/applications/` como por ejemplo con nano o vi :

```
$ cd /usr/share/applications/
$ sudo nano sublime-text-2.desktop
```

* Que el archivo contenga :

```
[Desktop Entry]
Name= NOMBRE DEL PROGRAMA
GenericName=DESCRIPCION DEL PROGRAMA
Comment=COMENTARIO DEL PROGRAMA
Exec=RUTA DEL PROGRAMA O EL NOMBRE SI ESTA AÑADIDO AL PATH start -i
Terminal=false
Type=Application
Icon= RUTAN DEL ICONO
Categories=CATEGORIA A LA QUE PERTENECE, QUE EXISTA COMO Network;FileTransfer;
StartupNotify=false

```

Como por ejemplo para sublime test :

```
[Desktop Entry]
Name=Sublime
GenericName=Sublime
Comment=Editor
Exec=/home/luisan/Sublime2/sublime_text
Terminal=false
Type=Application
Icon=/home/luisan/Sublime2/Icon/128x128/sublime_text.png
```


Y nada espero que os sirva ;) .

Indicar que tuve problemas porque estaba escribiendo la ruta de esta forma:

`~/Sublime2/sublime_text` en vez de `/home/luisan/Sublime2/sublime_text`
