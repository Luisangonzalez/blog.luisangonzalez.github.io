title: Event Binding - Binding de eventos (One-Way Binding)
date: 2017-02-05 22:52:14
tags:
- Angular 2
- TypeScript
categories:
- Frontend
- Angular 2
---

*El siguiente post es continuación del **[resumen de Angular 2](/2017/01/30/angular2/)***

En el [post anterior se explicaba el (Binding de propiedades)](/2017/02/02/Angular2-dataBinging/) el cual consistía en la comunicación de las propiedades de las clases de los componentes (TypeScript o JavaScript) al DOM, es decir:

> JavaScript to HMTL

En el caso de Event Binding, es lo contrario:

> HTML to JavaScript

Por ejemplo añadimos una función en nuestro componente:

```typescript
export class CarPartsComponent {
  ...
  upQuantity() {
    alert("You Called upQuantity");
  }
  ...
```

Y este es llamado desde HTML, por ejemplo al hacer click:

```html
  <button (click)="upQuantity( carPart )" >Click to alert</button>
```

Además del click tenemos los siguientes eventos:


```html
<div (mouseover)="call()">

<input (blur)="call()">

<input (focus)="call()">

<input type="text" (keydown)="call()">

<form (submit)="call()">
```

Como es de esperar es posible coger información desde el elemento HTML para luego utilizarla en nuestra clase JS, por ejemplo vamos a mostrar un alert de cada letra que el usuario introduce en un input:

* Código HTML:

```html
<input type="text" (keydown)="showKey($event)">
```

* TypeScript o JavaScript

```typescript
export class CarPartsComponent {
  ...
  showKey(event) {
    alert(event.keyCode);
  }

  ...
```  

En el siguiente post tratara de Two-way Binging, es decir comuncación bidireccional entre el DOM y Js.
