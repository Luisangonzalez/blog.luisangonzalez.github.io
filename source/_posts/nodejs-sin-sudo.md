title: Instalar node + npm sin sudo
date: 2016-03-19 02:03:02
tags:
- Node.js
- Ubuntu
categories:
- Configuración de entorno
- Node.js
---

Buenas, comento los pasos a seguir para instalar node en Ubuntu 14.04 para utilizar sin sudo, es decir poder instalar los paquetes que queramos sin necesidad de privilegios, **OjO esto es peligroso**, cualquier paquete npm o js que ejecutemos con node se ejecutara sin necesidad de sudo, no es nada recomendado para entornos de producción, sin embargo para desarrollo nos facilita bastante :).


1. Para ello debemos tener instalado build essentials (g++ c++ make)
```bash
$ sudo apt-get install build-essential
```
2. Descargar la última versión de node en mi caso recomiendo LTS, para descargarla =>  [nodejs.org](https://nodejs.org/en/)

3. Crear directorio donde vamos a poner todos los archivos de node en mi caso dentro de la carpeta `~/.local` creare la carpeta node.
```bash
$ cd ~/.local
$ mkdir node
```
4. Meter todo los archivos de node (tar que nos hemos descargado en el punto 1), tener en cuenta la ruta de la descarga.
```bash
$ tar xf ~/Descargas/node-v4.4.0-linux-x64.tar.xz --strip-components=1
```
5. Añadir el enlace simbolico del PATH en .bashrc o .zshrc si utilizas [oh-my-zsh](http://ohmyz.sh/)
```bash
$ echo 'export PATH=$HOME/.local/node/bin:$PATH' >> ~/.zshrc
$ echo 'export PATH=$HOME/.local/node:$PATH' >> ~/.zshrc
$ source ~/.zshrc
```

Una vez terminado podemos comprobar que esta instalado correctamente al abrir el terminal y ejecutar donde nos devolera la versión de node que hemos instalado.
```bash
$ node -v
v4.2.3
```

Por último si queremos podemos actulizar npm :
```bash
$ npm install -g npm
```

Fuente original, traducida y modificada: http://corejs.docs.bqws.io/setup/#ubuntu
