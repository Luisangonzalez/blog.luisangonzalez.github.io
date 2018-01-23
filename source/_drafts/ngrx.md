title: ngrx
tags:
---

https://angularfirebase.com/lessons/angular-ngrx-redux-starter-guide/

### Top Five High-Level Concepts
Here are five must-know high-level concepts about ngrx/Redux.

* All application data is one single object known as a store, representing the application’s state. I like to think of the store as a mini client-side database that holds all data being consumed by an app at any given point in time.

* A state object cannot be changed - it is immutable.

* When data changes, the existing state is duplicated, then a new object is created with the updates. In Angular this data is treated as an RxJS Observable, allowing us to subscribe to it from anywhere in the app.

* State can only be changed via an action, which is also an object. It includes a type (the action name) and an optional payload (the action data), for example { type: 'DELETE_ITEM', payload: 123 }.

* When an event is emitted, for example a button click, the action is sent to a reducer function to converts the old state into the new state.




1. install `npm install @ngrx/core @ngrx/store  --save` and Import **StoreModule** in app.module.ts


```ts
// Import store
import { StoreModule } from '@ngrx/store';
// add Reducer (contains actions to save in store)
import { simpleReducer } from './simple.reducer';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    StoreModule.forRoot({ message: simpleReducer })
  ],
  bootstrap: [AppComponent]
})
export class AppModule { }

```

2. Create simple reducer

Reducer is just a function runs a **swith** statement over possible **actions that uses old state to create new state**


Now let’s create the reducer in a new file called `src/app/simple.reducer.ts.`

The reducer is just a function that runs a switch statement over possible actions that uses the old state to create a new state. Here we have two actions SPANISH and FRENCH. If the reducer receives one of these actions, it simply converts the state string to a new value.

```ts
import { Action } from '@ngrx/store';
export function simpleReducer(state: string = 'Hello World', action: Action) {
  switch (action.type) {
		case 'SPANISH':
		  return state = 'Hola Mundo'
    case 'FRENCH':
      return state = 'Bonjour le monde'
		default:
			return state;
	}
}

```

3. In component: 

Now we need a way to present and change the state in the UI. Here are a few key points about this code.

* When using the ngrx Store class, it is necessary to give it a TypeScript interface that cooresponds the object we passed to the NgModule. In this example, our AppState interface handles this task with it’s one message property.

* A variable for message$ is set as an Observable on the component by calling this.store.select('message').

* We trigger state changes by sending actions to the reducer with this.store.dispatch('ACTION')



4. In html use function to change the state

```html
<h2>{{ message$ | async }}</h2>
<button (click)="spanishMessage()">Spanish</button>
<button (click)="frenchMessage()">French</button>
```


Por ahora en resumen:

* Archivo **reducer**: `src/app/simple.reducer.ts` función que ejecuta un swith donde se encuentran las acciones que se van a llamar cuando se realice un `dispatch` para cambiar el estado.

* El **reducer** se importa en el StoreModule importado en `app.module.ts`

* En el componente
    * En la clase Store es necesario indicar el tipo de interface que vamos a utilizar en AppState
    * En el constructor inicializamos la variable que queremos con el store mediante select ` this.message$ = this.store.select('message')`
    * Añadimos las funciones que hacen un dispatch para llamar a las acciones, en el dispath el type es el nombre de la acción que hemos añadido en el swith del `reducer`
    ```ts
    spanishMessage() {
    this.store.dispatch({type: 'SPANISH'})
    } 
    ```

To view in ReduxDevtools:

`npm install @ngrx/store-devtools --D`

And add in import on `app.module.ts`

`(ENV !== 'production') ? StoreDevtoolsModule.instrument({maxAge: 70}) : [],`