title: Angular router
date: 2017-06-11 21:13:42
tags:
- Angular 2
- TypeScript
categories:
- Frontend
- Angular 2
---

*El siguiente post es continuación del **[resumen de Angular 2](/2017/01/30/angular2/)***

Hay varias formas de hacer un router en angular, una de ellas es la siguiente utilizando:
 * [RouterModule](https://angular.io/docs/ts/latest/api/router/index/RouterModule-class.html) y [Routes](https://angular.io/docs/ts/latest/api/router/index/Routes-type-alias.html) de [@angular/router](https://angular.io/docs/ts/latest/api/#!?query=router)

Para el ejemplo partimos de :

* Un componente cualqiera como puede ser login situdado en `/login/login.component` el cual exportamos:
  ```typescript
  import { Component, NgZone } from '@angular/core';

  @Component({
      selector: 'my-login',
      templateUrl: 'login.component.html',
      styleUrls: ['login.component.scss'],

  })
  export class LoginComponent {
    constructor() {}
  }
  ```

* Creamos un modulo app-routing `app-routing.module.ts`, el cual importa:
  * Los componentes que vamos a routear
  * NgModule
  * Routes y RouterModule

  ```typescript
  import { NgModule } from '@angular/core';
  import { Routes, RouterModule } from '@angular/router';
  import { LoginComponent } from './login/login.component';

  ```

  En el modulo creamos un array de rutas del objeto Routes en el cual se indica el path y el componente a dicho path:
    ```typescript
    export const routes: Routes = [
      { path: 'login', component: LoginComponent },
      { path: 'register', component: RegisterComponent }
    ];
    ```

  En @NgModule se importan las rutas para el routerModule y se exportan una vez añadidas las rutas:

    ```typescript
    @NgModule({
      imports: [ RouterModule.forRoot(routes) ],
      exports: [ RouterModule ],
    })
    ```

Por último exportamos `AppRoutingModule` y además todos los componentes los cuales serán incluidos en AppModule para ser declarados, de esta forma no tenemos que importar uno a uno en AppModule, si no todos los componentes añadidos en el array de AppRoutingModule.

```typescript
export class AppRoutingModule {}
export const routedComponents = [ LoginComponent, RegisterComponent ];

```

En definitiva AppRoutingModule sería por ejemplo:

```typescript
import { NgModule } from '@angular/core';
import { Routes, RouterModule } from '@angular/router';

import { LoginComponent } from './login/login.component';

export const routes: Routes = [
  { path: 'login', component: LoginComponent },
  { path: 'register', component: RegisterComponent },
];

@NgModule({
  imports: [ RouterModule.forRoot(routes) ],
  exports: [ RouterModule ],

})

export class AppRoutingModule {}

export const routedComponents = [ LoginComponent, RegisterComponent ];
```

Y en app.module se importa `import { AppRoutingModule, routedComponents } from './app-routing.module';` para añadir a `imports` AppRoutingModule y declarar en `declarations` routedComponents.

`app.module.ts`:

```typescript
import { NgModule } from '@angular/core';
import { BrowserModule }  from '@angular/platform-browser';
import { HttpModule } from '@angular/http';

import { AppComponent } from './app.component';
import { AppRoutingModule, routedComponents } from './app-routing.module';
import { AuthModule } from './shared/auth.module';


@NgModule({
    imports: [
        BrowserModule,
        AppRoutingModule, // Important add AppRoutingModule
        HttpModule
    ],
    declarations: [
        AppComponent,
        routedComponents // All components in AppRoutingModule
    ],
    bootstrap: [AppComponent]
})

export class AppModule { }

```
