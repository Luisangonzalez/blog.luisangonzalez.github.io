title: Instalar Cordova Android en Ubuntu 14.04
tags:
  - Android
  - Cordova/Phonegap
  - Ubuntu
categories:
- Configuración de entorno
- Cordova/Phonegap
date: 2016-02-11 01:29:00
---

## Guia sencilla para instalar cordova

Como indican en la web de [apache cordova](https://www.npmjs.com/package/cordova) o traves del gestor de paquetes [npm](https://www.npmjs.com/package/cordova) siguiendo las instrucciones que indican:


```
sudo apt-add-repository ppa:cordova-ubuntu/ppa
sudo apt-get update
sudo apt-get install cordova-cli
npm install -g cordova

```

Y para Ubuntu instalando los paquetes:

```
sudo apt-get install cmake debhelper libx11-dev libicu-dev pkg-config qtbase5-dev qtchooser qtdeclarative5-dev qtfeedback5-dev qtlocation5-dev qtmultimedia5-dev qtpim5-dev qtsensors5-dev qtsystems5-dev

```
