title: Añadir dispositivo para depurar e instalar apps con Android Studio o Cordova/Phonegap
tags:
- Linux
- Ubuntu
- Android
- Cordova/Phonegap
categories:
- Android
date: 2016-02-28 17:59:23
---

Desarrollar aplicaciones móviles usando el emulador de Android no siempre es tan rápido como esperamos ni mucho menos para testear los gestos táctiles, la mejor opción es depurar e isntalar las aplicaciones que estamos desarrollando en un dispositivo físico el problema es que no siempre se añade y configura automaticamente para ser usuado con Android Studio o con cordova.

En mi caso utilizo un [bq X5](http://www.bq.com/es/aquaris-x5) y estos son los pasos que he seguido para pdoer utilizarlo en Ubuntu 14.04.

-  Intalar MTPS
```
sudo apt-get install libmtp-common mtp-tools libmtp-dev libmtp-runtime libmtp9
sudo apt-get install mtpfs
```

- Añadir el id :

Con el comando `lsusb` nos listara todos los usbs conectados, entre ellos el dispositivo móvil.


```
$lsusb
Bus 002 Device 002: ID 8087:8001 Intel Corp.
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8009 Intel Corp.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 8087:07dc Intel Corp.
Bus 003 Device 002: ID 046d:c52e Logitech, Inc.
Bus 003 Device 005: ID 2a47:7f10  #Este es id
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

- Como usuario root añadimos al archivo `/etc/udev/rules.d/51-android.rules.` la siguiente linea:
`SUBSYSTEM=="usb", ATTR{idVendor}=="0x2a47", MODE="0666", GROUP="plugdev"`

- En el archivo que se encuentra en nuestra carpeta de usuario `~/.android/adb_usb.ini` añaidmos el id del dispositivo: `0x2a47` en nuestro caso.

Siguiendo estos pasos, podremos utilizar nuestro móvil con Android Studio o cordova/phonegap.

Indicar que gran parte de la información se encuentra en
`http://developer.android.com/tools/device.html`
