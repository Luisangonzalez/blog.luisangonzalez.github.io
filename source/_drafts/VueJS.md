title: VueJS
date: 2017-10-25 20:25:27
tags:
---
1. Iniciación --> bootstrapping (Instancía de vue)
```js
Vue.config.productionTip = false

new Vue({
 el: '#myTasks',
 data: {
   msg: 'Hello world'
 },
 computed: {
   fullMSG: function () {
     return this.msg + ‘!’
   }
 }
})
```
// Primer componente:
Vue.component('mi-component', {
 data: function () {
   return {
     msg: 'Hello world'
   }
 },
 template: '<p>Hola!</p>',
 methods: {
 }
})
```js

2. JSX --> .vue
3. Propiedades de datos en los componentes:
  - Propiedades de datos en los componentes:
    - **Data:** Son los datos de iniciación, accesibles desde el template, *modelo de instancia*.
    - **props:** Comuncación entre los componentes, ***One-way Down Data Flow** siempre de padres a hijos, puede recibir una o varias Propiedades.
        - type :Define el tipo que debe tener la prop
        - required : Define si la prop es obligatoria o no
        - default : En caso de que la propiedad no contenga valor, se le asigna este valor por    defecto a la prop
        - validator : Si el valor de la prop es válido, asigna dicho valor a la pop
    - computed --> datos de los componentes con transformación
    - watchers --> reactivo

```js
export default {
  name: 'vu-component',
  props: {
    month: {
      type: String,
      required: true,
      default: 'September',
      validator (value) {
        return value.startsWith('S')
      }
    }
  },
  data () {
    return {
      msg: 'Hello world!'
    }
  }
}
```
4. Ciclo de vida de los componentes
  hooks


5. Componentes Asincronos , webpack con 