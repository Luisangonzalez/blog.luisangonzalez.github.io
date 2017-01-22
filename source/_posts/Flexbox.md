title: Resumen Flexblox del curso "Cracking the case with Flexbox" de CodeSchool
date: 2017-01-22 00:13:38
tags:
- CCS3
- Flexbox
---
> [Cracking the case with Flexbox](https://www.codeschool.com/courses/cracking-the-case-with-flexbox)

[Flexblox](https://www.w3.org/TR/css-flexbox-1/) es un nuevo tipo de display, uno más de los ya conocidos:

* Block layout
* Table layout
* Inline layout
* Positioning layout
* Flex layout
  * Flex containers
  * Flex items
  * Flex lines
* Aquí podemos encontrar todas las propiedades de [display](http://www.w3schools.com/cssref/pr_class_display.asp).

Aparece para facilitarnos [Responsive Design o Diesño adaptable](https://developer.mozilla.org/es/docs/Desarrollo_Web/Web_adaptable) evitando el uso de Float, con Flexbox cambia la forma en la que posicionamos los elementos como veremos en este breve resumen, destacando su estructura compuesta por un contenedor padre `display: flex` y sus elementos `flex`.

> [Ejemplo de variaciones en flex](http://codepen.io/Luisangonzalez/pen/mOmNNM)

Esta claro que Flexbox está para quedarse, actualmente es soportado por todos los nuevos navegadores :
> Can i use [Flexbox](http://caniuse.com/#search=Flexbox)

#### Algunos patrones UI de Flexbox:

* Equal heights (mismas alturas)
* Vertically centered content (contenido centrado verticalmente)
* Media objects
* Sticky footers (Footer fijo)
* Column layouts (Diseño en columnas)

## Propiedades Flexbox:

###  flex-wrap: wrap;

El valor por defecto en Flexbox es `nowrap`, cuando se indica `flex-wrap: wrap` se obliga a los elementos a permanecer en la misma línea aún sin espacio, cuando no hay espacio horizontalmente coloca los elementos uno debajo de otro, verticalmente, parecido a display block.


```CSS
.setup {
  display: flex;
  flex-wrap: wrap;
}
```
#### flex-wrap: wrap-reverse;
Renderiza al reves, el primer elemento es colocado el último.

```CSS
.setup {
display: flex;
flex-wrap: wrap-reverse;
}
```

### Flex direction

Flex wrap apila los elementos en pila tipo block cuando no hay espacio, si queremos apilar los elementos aún habiendo espacio debemos utlizar la propiedad `flex-direction` con el valor `column`.

```CSS
.setup {
display: flex;
flex-direction: column;
}
```
El valor por defecto es `row`, estos son los posibles valores:
* `row`
* `row-reverse`
* `column`
* `column-reverse`

### Justification and order:

![Imagen de Mozilla Fundation con licencia CC-BY-SA 2.5. http://creativecommons.org/licenses/by-sa/2.5/ ](https://developer.mozilla.org/files/3739/flex_terms.png)

###  _main asix_

**Main axis** es determinada por *flex-direction*, es el caso por defecto `flex-direction: row;`
**main axis** es en horizonal y **cross axis** en vertical.


En el caso de `flex-direction: column;` es viceversa, **main axis** vertical y **cross axis** horizontal.

#### `justify-content`

Es usado para distribuir el contenido en el *`main axis`*

* `justify-content: flex-start` (Default value)
* `justify-content: flex-end`
* `justify-content: center`
* `justify-content: space-between`
* `justify-content: space-around`

#### `order`

Ordenar elemento, -1, 0, 1..

### `align-items` --&gt; _cross axis_

Para alinear el contenido en el _cross axis_

* `aling-items: stretch;` _Defualt_
* `aling-items: flex-start;`
* `aling-items: flex-end;`
* `aling-items: center;`
* `aling-items: baseline;`

_OjO_ No se controla si los items son `flex-wrap`, para ello `align-content`


### Size

Nuevas propieades para espacio, lo más común por defecto es usar:

`min-width: 0`

* #`flex-grow`

Nueva propiedad de espacio en flex, por defecto:

`flex-grow: 0;`

Asiganando el valor 1 ocupa el máximo espacio posible:

`flex-grow: 1;`

También es posible utilizarlo proprocinalmente, es decir en un contenedor **sin contenido** de 1000px sería:

`flex-grow: 1;` --> 250px

`flex-grow: 2;` --> 500px

`flex-grow: 1;` --> 250px

Se cálcula de manera proporcional.

*OjO* **Con contenido** se adapata dependiendo el contenido que tiene.

*OjO* Si queremos que las imagenes mantengan su tamaño original:

##### `flex-shrink: 0`

----------------------------------------------

* #### *OjO* **Para definir anchos (min-width) en flex items**

Por defecto

#### `flex-basis: auto`

Se puede definir en %, px (absolute), em (relative), rm...

Combiar `flex-basis` y `flex-shrink nos permite hacer layouts homogenos, es decir la imagen ocupa lo máximo de 'flex-basis` tanto en horizontal como en vertical.

Hay que tener en cuenta:

```CSS
/* Intrinsic sizing keywords*/
flex-basis: fill;
flex-basis: max-content;
flex-basis: min-content;
flex-basis: fit-content;

/* Automatically size based on the flex item's content */
flex-basis: content;
```
------------------------------------------------------


* #### `align-self`
** Para alinear un item flex individual del resto:**

El valor por defecto es `align-self: strech`, `align-self` sobreescribe a `align-content`


Es útil para usarlo en column, para ello ver las diapositivas 73 y 74.

* #### `align-content`
**Usado para alinear los flex item wrapped**

### Shortland

*OjO* En IE no funcionan todos.

The default *0 1 auto*:

```
.flex {
    flex: 0 1 auto;
}
```
es igual a:

```
.flex {
    flex-grow: 0;
    flex-shrink: 1;
    flex-basis: auto;
}
```

*Leer en [Gitbook](https://luisangonzalez.gitbooks.io/resumen-flexbox/content/)*

#### Fuentes y enlaces de interes:
* [Mozilla: Usando las cajas flexibles CSS](https://developer.mozilla.org/es/docs/Web/CSS/CSS_Flexible_Box_Layout/Usando_las_cajas_flexibles_CSS)
* [w3.org](https://www.w3.org/TR/css-flexbox-1/)
* [Cracking the case with Flexbox](https://www.codeschool.com/courses/cracking-the-case-with-flexbox)
