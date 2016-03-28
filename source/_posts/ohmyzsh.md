title: Instalar Oh my zsh
date: 2016-03-28 13:37:28
tags:
- Ohmyz.sh
- Ubuntu
- Git
categories:
- Configuración de entorno
- Ohmyz.sh
---

[Oh my ZSH!](http://ohmyz.sh/) Es un términal configurable con multitud de plugins como Git que hacen más atractivo nuestro terminal ;)

El plugin de Git es mi favorito, no solo por el tema, es la funcionalidad extra que le da al terminal lo que hace que se más práctico, el poder conocer en la rama en la que nos encontramos así como cuando hemos realizado una modificación nos ayuda para saber el estado en el repo en el que nos encontramos, aquí podemos observar un pantallazo del términal con ohmyzsh y el plugin git:


![Oh my zsh imagen](img/ohmyzsh.jpg "Oh my zsh imagen")

Este es uno de los plugins, hay miles de [plugins](https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins) que podemos encontrar en su repo oficial además de [temas.](https://github.com/robbyrussell/oh-my-zsh/wiki/Themes)

Para instalarlo, se han de siguir los siguintes pasos sacados de su [repo oficial](https://github.com/robbyrussell/oh-my-zsh)

 1.Instalar via apt-get
```bash
 sudo apt-get install zsh
```

 2.Hacer zsh como shell por defecto
```bash
 chsh -s $(which zsh)
```

 3.Cerrar sesión y volver a abrir, al abrir el terminal nos pregungar si crear el archivo ~/.zshrc, el cual hará la función de bashrc.

 4.En mi caso se instala correctamente pero no carga los temas ni aparece la carpeta `~/.oh-my-zsh` en la cual se pueden instalar temas y plugins, para ello descargando e instalando el siguiente script se soluciona:
```bash
 curl -L http://install.ohmyz.sh > install.sh
 sh install.sh
```
