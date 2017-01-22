title: Instalar entorno para desarrollo en Android
date: 2016-03-24 12:09:03
tags:
- Android
- Ubuntu
categories:
- Configuración de entorno
- Android
---
Pasos a seguir para configurar el entorno para desarrollar en Android con Android Studio en Ubuntu 14.04


1. Descargar [Android Studio](http://developer.android.com/intl/es/sdk/index.html)
2. Descomprimir donde queramos, en mi caso en ~/.local/android
3. [Añadir icono y acceso directo](http://luisangonzalez.es/2015/02/24/Anadir-icono-y-acceso-directo-de-una-aplicacion-en-Ubuntu-gnome-3/)
4. Para evitar el error de ["Unable to install Android Studio in Ubuntu"](http://stackoverflow.com/questions/28847151/unable-to-install-android-studio-in-ubuntu)
```bash
$ sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0 lib32stdc++6
```
5. Añado las variables de entorno a .zshrc en mi caso, si no se tiene instalado sería en .bashrc
```bash
$ echo 'export PATH=$HOME/.local/android/sdk:$PATH' >> ~/.zshrc
$ echo 'export PATH=$HOME/.local/android/sdk/tools:$PATH' >> ~/.zshrc
$ echo 'export PATH=$HOME/.local/android/sdk/platform-tools:$PATH' >> ~/.zshrc
$ source ~/.zshrc
```
6. Instalar [adb](http://developer.android.com/intl/es/tools/help/adb.html)
```bash
$ sudo apt-get install android-tools-adb android-tools-fastboot
```
7. [Añadir dispositivo para depurar e instalar apps con Android Studio o cordova/phonegap](http://luisangonzalez.es/2016/02/28/add-device-android/)
