title: Modelos y uso de mocks
date: 2017-02-02 20:12:39
tags:
- Angular 2
- TypeScript
categories:
- Frontend
- Angular 2
---
*El siguiente post es continuación del **[resumen de Angular 2](/2017/01/30/angular2/)***

### Modelos en angular 2

Básicamente los modelos en angular 2 son clases como por ejemplo:

```typescript
export class Carpart {
  id: number;
  name: string;
  description: string;
  inStock: number;
  price: number;
}
```


De esta forma en la clase de nuestro componente podemos crear arrays de la clase Cardpart, importando la clase.

```typescript
import { Component } from '@angular/core';
import { CarPart } from './car-part';

export class CarPartsComponent {
  carParts: CarPart[] = [{
    "id": 1,
    "name": "Super Tires",
    "description": "These tires are the very best",
    "inStock": 5,
    "price": 4.99
}, { ... }, { ... }]
...

```

### Uso de mocks en angular 2

Una de las formas posibles para comenzar a desarrollar nuestra aplicación sin disponer aún los datos que nos va a suministrar la API es mediante *Mocking* (mockear datos).
Una forma simple es creando nuestro array de datos JSON o de clases que vayamos a utilizar y asignarlo a las propiedades de los componentes que nos sea necesario.

Como por ejemplo:

```typescript
import { CarPart } from './car-part';

export const CARPARTS: CarPart[] = [{
  "id": 1,
  "name": "Super Tires",
  "description": "These tires are the very best",
  "inStock": 5,
  "price": 4.99
  }, { ... }, { ... }];
```

Y ahora en nuestro componente mediante la función `ngOnInit()` damos el valor a la propiedad correspondiente, en este ejemplo a la propiedad `cardParts` se le asigna el valor `CARDPARTS` el cual es el array de cardparts que hemos importado.

```typescript
import { Component } from '@angular/core';
import { CarPart } from './car-part';
import { CARPARTS } from './mocks';
...
})

export class CarPartsComponent {
  carParts: CarPart[] ;

  ngOnInit() {
    this.carParts = CARPARTS;
  }
...
```

De esta forma podemos comenzar a desarrollar nuestra app con datos de prueba *mocks* ;).
