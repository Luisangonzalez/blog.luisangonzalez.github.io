title: Property Binding - Binding de propiedades y clases CSS (One-way binding)
date: 2017-02-02 21:25:08
tags:
- Angular 2
- TypeScript
categories:
- Frontend
- Angular 2
---

*El siguiente post es continuación del **[resumen de Angular 2](/2017/01/30/angular2/)***

El *Binding* de propiedades significa mostrar las propiedades de nuesto componente en el DOM de la web y que cambie dinamícamente según cambía la propiedad, *One-way binding* es debido a que la comunicación es desde los modelos de los componentes de nuestra app al DOM no del DOM a la aplicación.

Con `[ ]` decimos a Angular 2 que esa propiedad del DOM va unida a una propiedad de nuestro modelo como por ejemplo:


* `<img [ src ] =" carPart.image ">`
* `<div [ hidden ] ="!user.isAdmin" >secret</div>`
* `<button [ disabled ] ="isDisabled" >Purchase</button>`
* `<img [ alt ] ="image.description">`


### Binding Class (CSS)

También es posible hacer binding de una clase CSS dependiendo del modelo.

Por ejemplo la clase CSS
```css
.featured {
  background: #57595D;
}
```

Es posible añadirla dependiendo del modelo, en este caso de ejemplo `cardPart.featured` devuelve `true` o `false` y si es true se añade la clase `.featured` al elemento, está es la única síntasis posible:

> `<div [class.featured]="carPart.featured" >`

Hay que tener en cuenta, que de esta forma cada elemento tiene su scope, el código generado sería el siguiente:

`<div _ngcontent-opf-2 >`

```css
.featured[_ngcontent-opf-2] {
  background: #57595D;
}
```
En definitiva:

* El binding de propiedades permite hacer binding entre las propiedades del componente y el DOM.
* Cualquier actualización del valor de la propiedad actualizara el DOM, pero no viceversa, una actualización del DOM no actualiza el modelo (One-way binding).
* El binding de clases CSS nos permite especificar estilos a un elemento del DOM si la propiedad del componente es `true`, tienen su propio scope del estilo que es dado.
