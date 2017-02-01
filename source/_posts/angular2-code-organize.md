title: Organización de código
date: 2017-01-31 22:46:02
tags:
- Angular 2
- TypeScript
categories:
- Frontend
- Angular 2
---

*El siguiente post es continuación del **[resumen de Angular 2](/2017/01/30/angular2/)***

### Organización de los componentes en Angular 2

Como vulgarmente se dice:
>  divide o vencéras

Partiendo del siguiente ejemplo en el que tenemos AppComponent en `app/main.ts`:

```js
import { NgModule, Component } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { platformBrowserDynamic } from '@angular/platform-browser-dynamic';

@Component({
  selector: 'my-app',
  template: `<h1> {{title}} </h1>
	<h2>{{carPart.name}}<h2>
	<p>{{carPart.description}}<p>
	<p>{{carPart.inStock}} in Stock<p>`
})

class AppComponent {
	title = 'Ultra Racing';
	carPart = {
		"id": 1,
		"name": "Super Tires",
		"description": "These tires are the very best",
		"inStock": 5
		};
  }


@NgModule ({
  declarations: [ AppComponent ]
})

class AppModule { }

platformBrowserDynamic()
  .bootstrapModule(AppModule);
```

Movemos toda la parte del componente `AppComponent` a un fichero aparte como por ejemplo `app.component.ts`:

```js
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  template: `<h1>{{title}}</h1>`
})

// Importante, exportar para utilizar el componente
export class AppComponent {
  title = 'Ultra Racing';
  carParts = [...];
  totalCarParts() { ... };
}

```
**Es importante, exportar para utilizar el componente `export class..` **

**En conclusión ahora disponeos de dos archivos: **

* `main.ts` Que importa el componente:

```js
// Importante hacer el import
import { AppComponent } from './app.component';

@NgModule({
  declarations: [ AppComponent ],
  imports: [ BrowserModule ],
  bootstrap: [ AppComponent ]
})
class AppModule { }
```

*  Y el propio componente en `app.component.ts`

```js
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  template: `<h1>{{title}}</h1>`
})

export class AppComponent {
  title = 'Ultra Racing';
  carParts = [...];
  totalCarParts() { ... };
}
```

##### Mover el código HTML CSS

Ahora procedemos a separar el código del template (html) y añadir los estilos,

Como por ejemplo en el componente anterior:

```js
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  templateUrl: 'app/app.component.html',
  styleUrls:['app/car-parts.component.css']
})

export class AppComponent {
  title = 'Ultra Racing';
  carParts = [...];
  totalCarParts() { ... };
}
```

Como podemos observar el código HTML se encuentra en un archivo aparte `app.component.html` :

```html
<p>There is a example ;).</p>
<ul>...</ul>
```

y el css en otro `app.component.css` :

```css
.description {
  color: #444;
  font-size: small;
}
.price {
  font-weight: bold;
}

```

De esta forma, nuestro componente se encuentra dividido en tres partes cada  una en un archivo:

* La lógica del componente en `app.component.ts` el cual se exporta para incluirlo en @module en main.ts.
* El template con el html  en `app. component.html`
* Estilos del componente en `app.component.css`
