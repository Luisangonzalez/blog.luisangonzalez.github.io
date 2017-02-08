title: Servicios
date: 2017-02-08 21:10:53
tags:
- Angular 2
- TypeScript
categories:
- Frontend
- Angular 2
---

*El siguiente post es continuación del **[resumen de Angular 2](/2017/01/30/angular2/)***

En el post anterior [Modelo de datos y mocks](/2017/02/02/mocks/) cargábamos datos mocks importando directamente el archivo, esta **no** es la mejor forma debido a:
* Necesitamos importar el archivo en cualquier archivo que necesite acceso a los datos.
* No es sencillo cambiar el flujo de trabajo entre los datos reales y los mockeados.
* La carga de datos la realizan mejor las clases de services.

##### Los servicios son utilizados para organizar y compartir código a través de toda la app, suelen organizarse:

 `example.component.ts`  (Pide datos al servicio) ->
 `example.service.ts` (accede a los datos para pasarselos al componente) -> `mocks.ts`

Como por ejemplo:

* example.service.ts
```js
import { CARPARTS } from './mocks';
  export class RacingDataService {
    getCarParts() {
      return CARPARTS;
    }
}
```
* example.component.ts
```js
import { RacingDataService } from './racing-data.service';
...
export class CarPartsComponent {
  carParts: CarPart[];

  ngOnInit() {
    let racingDataService = new RacingDataService();
    this.carParts = racingDataService.getCarParts();
    }
}
```
De esta formar tenemos los datos desacoplados, no tenemos que importar los datos cuando nos sea necesario, solo el servicio y este es el que nos devuelve los datos, de esta forma si tenemos que cambiar la fuente de datos solo lo cambiamos en un solo lugar.

##### Los servicios en Angular 2 pueden y es conveniente usar el patrón de [inyección de dependencias](https://en.wikipedia.org/wiki/Dependency_injection)

El inyector de dependencias se encarga de crear y enviar los datos que le pidamos:

> Sabe si es necesario instanciar los datos para enviarlos o enviar los ya instanciados.


 Los pasos para hacer inyectable a un servicio son los siguientes:

 1. Añadir el decorator `@inyectable` al servicio.
 2. Indicar nuestro servicio inyectable en `providers` de `@NgModule`.
 3. Inyectar la dependencía en el componente que sea necesario.
 4. Utilizar el servicio en el componente en `ngOnInit()`.

Por ejemplo:

 * 1.Añadir el decorator `@inyectable` al servicio.

```js
import { CARPARTS } from './mocks';
import { Injectable } from '@angular/core';

@Injectable()
export class RacingDataService {
  getCarParts() {
    return CARPARTS;
  }
}
```

 * 2.Indicar nuestro servicio inyectable en `providers` de `@NgModule`.

 ```js
 ...
 import { RacingDataService } from './racing-data.service';

 @NgModule({
    declarations: [ AppComponent ],
    imports: [ BrowserModule, FormsModule ]
    bootstrap: [ AppComponent ] ,
    // En providers indicamos todos nuestros servicios inyectables
    providers: [ RacingDataService ]
 })
 class AppModule { }
 ...
 ```

 * 3y4 Inyectar la dependencía en el componente que sea necesario y utilizar el servicio en el componente en `ngOnInit()`.

 ```js
 ...
 import { RacingDataService } from './racing-data.service';

 @Component({ ... })
 export class CarPartsComponent {

   carParts: CarPart[];

   // Inyectar la dependencia en el componente
   constructor(private racingDataService: RacingDataService) { }

   // Utilizarla
   ngOnInit() {
     this.carParts = this.racingDataService.getCarParts();
   }
 }
 ```

De esta forma conseguimos que nuestro servicio:

* Sea desacoplado
* Escalable porque nuestras dependencias están ligadas a las clases
* Testeable porque es sencillo mockear
