title: Two-way Binding
date: 2017-02-07 21:29:02
tags:
- Angular 2
- TypeScript
categories:
- Frontend
- Angular 2
---

*El siguiente post es continuación del **[resumen de Angular 2](/2017/01/30/angular2/)***

En los posts anteriores hemos visto:

 * El [Binding de propiedades:](/2017/02/02/Angular2-dataBinging/)

> JavaScript to HMTL


* Y [Event Binding:](/2017/02/05/angular2-event-binding/)

> HTML to JavaScript

Two-way Binding es la unión de ambos para tener una comunicación bidireccional, es posible hacerlo de dos formas:

* Utilizando los dos Bindings:

 En este ejemplo en el mismo input se muestra la cantidad (Binding de propiedades) y se añade la cantidad (Binding de eventos):

```HTML
<input class="number" type="text" [value]="carPart.quantity" (input)="carPart.quantity = $event.target.value">
```

* Utilizando la síntasis `[ () ]` (Banana in the box)

Para ello en la clase del componente se importa `@angular/forms`:

```js
...
import { FormsModule } from '@angular/forms';

@NgModule({
  declarations: [ AppComponent ],
  imports: [ BrowserModule , FormsModule ],
  bootstrap: [ AppComponent ],
  providers: [ RacingDataService ],
})
class AppModule { }
...
```

Y en el input se utiliza la síntasis `[ () ]`:

```HTML
<input class="number" type="text" [(ngModel)]="carPart.quantity" >
```

De esta forma es mucho más clara y precisa.
