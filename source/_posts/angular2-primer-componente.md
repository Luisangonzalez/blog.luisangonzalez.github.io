title: Primer componente Angular 2
date: 2017-01-30 23:43:59
tags:
- Angular 2
- TypeScript
categories:
- Frontend
- Angular 2
---

El siguiente post es continuación del [resumen de Angular 2](/2017/01/30/angular2/)

Para comenzar añadir en `index.html` el primer componente, llamado en este caso `<my-app></my-app>`

```html
<!DOCTYPE html>
<html>

  <head>
    <!-- All the Angular 2 libraries needed -->
  </head>

  <body>
    <my-app>Loading App ...</my-app>
  </body>

</html>
```
Para cargar Js hay varias opciones, una de ellas es utilizar la librería [SystemJS](https://www.npmjs.com/package/systemjs) que se utiliza en el curso de codeschool:

El siguiente código añade el código de `app/main.ts`:
```html
<!DOCTYPE html>
<html>

  <head>
    <!-- All the Angular 2 libraries needed -->
    <script>
    System.import('app')
      .catch(function(err){ console.error(err); });
    </script>
  </head>

  <body>
    <my-app>Loading App ...</my-app>
  </body>

</html>
```

También una buena opción es con [webpack](https://webpack.github.io/) como [explican al detalle en la web oficial de angular.io](https://angular.io/docs/ts/latest/guide/webpack.html).

En `app/main.ts` añadimos nuestro primer componente:

```js
import { NgModule, Component } from '@angular/core';
//Las siguientes dependencias son para renderizar en el navegador
import { BrowserModule } from '@angular/platform-browser';
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';

// Our component decorator code goes here:

@Component({
//la etiqueta añadida anteriormente <my-app></my-app> 	
  selector: 'my-app',

// El contendio que se carga en nuestro componente
  template: `<h1> {{title}} </h1>
	<h2>{{carPart.name}}<h2>
	<p>{{carPart.description}}<p>
	<p>{{carPart.inStock}} in Stock<p>`
})

class AppComponent {
	//Definimos las propiedades que usamos en el template con {{ }}
	title = 'Ultra Racing';
	carPart = {
		"id": 1,
		"name": "Super Tires",
		"description": "These tires are the very best",
		"inStock": 5
		};
  }


// El nuevo componente lo debemos declarar en el decorador @NgModucle
@NgModule ({
declarations: [ AppComponent ]
})

class AppModule { }

// Bootrasp app (Arrancar la aplicación)
platformBrowserDynamic()
  .bootstrapModule(AppModule);
```

Tanto @Component como @NgModule son decorators, una feauture de typescript, explicado de forma breve digamos que "extiende" la funcionalidad o comportamiento de la clase a  un objeto:
* [Wikipedía](https://en.wikipedia.org/wiki/Decorator_pattern)
* [TypeScript lang](https://www.typescriptlang.org/docs/handbook/decorators.html)
