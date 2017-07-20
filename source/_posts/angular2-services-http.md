title: HTTP angular
date: 2017-06-10 20:00:48
tags:
- Angular 2
- TypeScript
categories:
- Frontend
- Angular 2
---


*El siguiente post es continuación del **[resumen de Angular 2](/2017/01/30/angular2/)***

En lo posts anteriores:
 * [Servicios](/2017/02/08/angular2-services/)
 * [Modelo de datos y mocks](/2017/02/02/mocks/)

Cargábamos los datos localmente desde fichero.

Con el [servicio http de angular](https://angular.io/docs/ts/latest/tutorial/toh-pt6.html) obtendremos los datos a través internet.

Con HTTP podemos hacer peticiones GET, POST, PUT, DELETE las cuales las podemos hacer de dos formas distintas:

* Mediante observables, como por ejemplo el método login:

```typescript
import { Injectable } from '@angular/core';
import { Http } from '@angular/http';
import 'rxjs/add/operator/map';


@Injectable()
export class AuthService {
    private backendUrl = process.env.BACKEND_URI;


    constructor(private http: Http) { }


    login(credentials: Credentials) {
      // console.log('cre', credentials);
        this.http.post(this.backendUrl + '/login', credentials)
            .map((res) => res.json())
            .subscribe(
            // We're assuming the response will be an object
            // with the JWT on an id_token key
            (data) => localStorage.setItem('jwtToken', data.jwtToken),
            (error) => console.log(error)
            );
    }
```

Como se observa importamos la librería `@angular/http` y la instanciamos en el constructor.
Tambíen necesitamos importar `rxjs/add/operator/map` para map en el observable.


* Con Promesas

```typescript
getHeroes() {
   this.heroService.getHeroes()
                    .subscribe(
                      heroes => this.heroes = heroes,
                      error =>  this.errorMessage = <any>error);
 }
```

*Se ha de tener en cuenta que en nuestro modulo tenemos que añadir `http` como provider en ambos casos.*


Para más info [Http client angular](https://angular.io/docs/ts/latest/guide/server-communication.html)
