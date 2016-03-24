title: Conectar placa arduino (bq zum) por Bluetooth en Android
date: 2016-03-13 18:05:08
tags:
- Android
- Cordova/Phonegap
- Arduino
categories:
  - Cordova/Phonegap
---

Con Cordova o Phonegap tenemos la gran ventaja de desarrollar una sola vez y que esta sea compatible para multiple plataformas móviles en las que se encuentran Android y IOS.

Cuando vamos a desarrollar una aplicación que hace uso de elementos nativos de la plataforma, es decir no solo es una capa de presentación web si no que utilizamos elementos físicos como el giroscopio, wifi o bluetooth en la mayoría de los casos nos vemos obligados de utilizar [plugins de cordova/phonegap](https://cordova.apache.org/plugins/).

En este caso vamos a utilizar [cordova-plugin-bluetooth-serial](https://www.npmjs.com/package/cordova-plugin-bluetooth-serial).

La aplicación de ejemplo consiste en conectar nuestro móvil con una placa Arduino que dispone de modulo de Bluetooth, en este caso [bq zum](http://www.bq.com/es/placa-zum-core) pero se puede utilizar cualquier otra añadiendo el modulo de Bluetooth.

Para ello:

* En la placa Arduino conectaremos un LED en el pin 13.
* Cargamos el [programa](https://github.com/Luisangonzalez/cordova-bluetooth-serial/blob/master/Arduino/Comunicacion_serie_Bluetooth_Z.ino) en la placa.
* El código de la App lo tenemos dispone en el repo de [github](https://github.com/Luisangonzalez/cordova-bluetooth-serial).

* Nos descagamos el código o hacemos git clone:
 `git clone git@github.com:Luisangonzalez/cordova-bluetooth-serial.git `
* Accedemos al directorio: `cd cordova-bluetooth-serial`
* Asumiendo que tenemos [instalado el SDK de Android](http://developer.android.com/sdk/installing/index.html).
* Con [cordova instalado y configurado](http://luisangonzalez.es/2016/02/11/instalar-cordova-android-en-ubuntu/) compilamos la APP:
 * Añadimos la plataforma android: `$ cordova platform add android`
 * Instalamos el plugin bluetooth: `$ cordova plugin add cordova-plugin-bluetooth-serial`
 * compilamos la app: `$ cordova run`



Si observamos el [código Arduino](https://github.com/Luisangonzalez/cordova-bluetooth-serial/blob/master/Arduino/Comunicacion_serie_Bluetooth_Z.ino) que hemos subido a la placa consiste en estar leyendo constantemente y en el caso de leer "b" encender el led y en caso "c" apagar el led.
```C
if (bluetooth_0.available() > 0) {
        bluetooth_0.println("Avaliable");
        read = bluetooth_0.readString();
        if (read == "b" || ledon) {
            bluetooth_0.print("ON");
            digitalWrite(led_0, HIGH);
            ledon = true;
        } else if (read == "c" || !ledon) {
            bluetooth_0.print("OFF");
            digitalWrite(led_0, LOW);
            ledon = false;
        }
    }
```

En el caso del código de cordova observamos en [www/js/index.js](https://github.com/Luisangonzalez/cordova-bluetooth-serial/blob/master/www/js/index.js) :
* Al comienzo del archivo en comentarios incluimos las funciones globales como LED13ON y LED13OFF que posterimente indicamos:
```javascript
/*
global cordova, console, $, bluetoothSerial,refreshButton, deviceList, disconnectButton, connectionScreen, messageDiv, led13ButtonON,led13ButtonOFF
*/
```
* A parte de las funciones para conectar y emparejar las propias que hemos realizado para enviar "b" para encender el LED:
```javascript
LED13ON: function() {
  bluetoothSerial.write("b");
}
```

y "c para apagarlo":

```javascript
LED13OFF: function() {
  bluetoothSerial.write("c");
}
```

En el caso de [www/index.html](https://github.com/Luisangonzalez/cordova-bluetooth-serial/blob/master/www/index.html):
para hacer uso de las funciones de index.js simplemente añadimos al id de los botones el nombre de las funciones:
```html
<p>
    <a class="topcoat-button--large" id="led13ButtonON">LED 13 ON</a>
    <a class="topcoat-button--large" id="led13ButtonOFF">LED 13 OFF</a>
</p>
```

Para cualquier enviar comentarios para que os pueda ayudar si me es posible, espero que os haya gustado ;).
