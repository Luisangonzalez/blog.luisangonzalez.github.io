title: Angular 2 - Estructura de directivas, Pipes y Métodos
date: 2017-01-31 20:48:17
tags:
- Angular 2
- TypeScript
categories:
- Frontend
- Angular 2
---

### Directivas

*El siguiente post es continuación del **[resumen de Angular 2](/2017/01/30/angular2/)***

Una directiva de Angular es la forma de añadir comportamiento dinámico a HTML mediante la etiqueta o selector que creamos.

Existen tres tipos diferentes de directivas:

* Component
  * Tiene un template, es el más común, lo hemos utilizado al [crear el primer componente](/2017/01/30/angular2-primer-componente/)
* [Structural Directives](https://angular.io/docs/ts/latest/guide/structural-directives.html)
  * Por ejemplo bucles `*ngFor` o condicionales `*ngIF`
* [Attribute Directives](https://angular.io/docs/ts/latest/guide/attribute-directives.html)
  * Nos permite cambiar la apariencia o comportamiento de un componente.

Podemos verlas en el fragmento de código:

```js
...
@Component({
  // El selector y templatte sería el primer tipo de directiva
  selector: 'my-app',
  template: `<h1>{{title}}</h1>
    <ul>
      <li *ngFor="let carPart of carParts">
        <h2>{{carPart.name}}<h2>
        <p>{{carPart.description}}<p>
        <p *ngIf="carPart.inStock > 0">{{carPart.inStock}} in Stock</p>
        <p *ngIf="carPart.inStock === 0">Out of Stock</p>
      </li>
    </ul>`

  // En el propio template observamos las directivas de estructura *ngFor y *ngIf

})
class AppComponent {
...
```

### Pipes y Métodos

Un **pipe** coge un dato de entrada y lo transforma a la salida deseada, como por ejemplo:

* Poner un texto en máyusculas:
```
{{carPart.name | uppercase }}
```

* Añadir formato de moneda:
```
{{carPart.price | currency:'EUR'}}
```

* [Y muchos más que encontramos en la documentación oficial](https://angular.io/docs/ts/latest/guide/pipes.html)

*Métodos (Methods)* como podemos imaginar es añadir métodos en la clase de nuestro componente para luego ser utilizada:


```js
...
@Component({
  selector: 'my-app',
  template: `<h1>{{title}}</h1>`

  })

class AppComponent {
  exampleMethod() {
      return 10;
    }
}

```
