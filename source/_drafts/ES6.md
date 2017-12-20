title: ES6
date: 2017-10-13 20:30:24
tags:
---

## Variable declarated with `let`

`let` variables are scoped to the nearest *block* and are *NOT hoisted*.

### Using let in for loops

Each callback function now holds a reference to their *own version of i*

```js
function loadProfiles(userNames) {
    for (let in userNames) {
        _fetchProfile('/users' + userNames[i], () => {
            console.log(`Fetched for${userNames[i]}`);
        });
    }
}

loadProfiles(['Manolo','Benito','Fermin','Gonzalo']);
```
With *var* it is not posible, the var is hoisted in top of function and callback save the last value.

### variable declarated with `const`

The *const* keyword creates ***read-only*** named constants and must be assigned an initial value.

*const* are scoped to the nearest block.

* Use `let` when variables could be reassigned new values.
* Use `const` when new variables are not expected to be reassigned new value

## Functions

### Arguments undefined 

Unexpect argumentes might cause *errors* during function *execution*, the common practice is **to check for presence** of arguments.

```js
function loadProfiles(userNames) {
    let names = typeof usernames !== 'undefined' ? userNames : [];
    let namesLength = names.length;
    console.log(namesLength);
}
```
Manual arguments check don't scale well, in ES6 **Using default parameter values** :

```js
function loadProfiles(userNames = []) {
    let namesLength = names.length;
    console.log(namesLength);
}
```
 * Does not break when invoked wiht no arguments
    
    `loadProfiles(); -> 0`

 * Nor with explicit `undefined` as argument
    
    `loadProfiles(undefined); -> 0`

### Objects in arguments

The **options object** is a widely used pattern than allows user-defined settings to be passed to a function in the form of properties on an object.

**ES5**

* THe options object it hard to know what options a function accepts

```js
setPageThread('New Version out Soon!', {
    // Options object with 3 properties
    popular: true,
    expieres: 10000,
    activeClass: 'is-page-thread'
});

    // Options objects is second parameter,
    // Unclear what options this function expect just by looking at its signature.
function setPageThread(name, options = {}) {
    // Assign from proporties to local variables
    let popular = options.popular;
    let expires = options.expires;
    let activeClass = options.activeClass;

};
```

#### **ES6**

* **Using named parameters** for optional settings makes it easier to understand how a function should be invoked.
* **Omitting certain arguments on call** It is okay to omit **some options** when invoking a function with named parameters.
* **Don't omit all named arguments on call** It is **NOT okay** to omit the options argument altogether when invoking a function with named parameters when no default value is set for them.

```js
    // Now we know which arguments are avaliable
function setPageThread(name, options = { popular, expires, activeClass }) {
    // Assign from proporties to local variables
    console.log('Name: ', name);
    // Is posible omit some arguments OjO not all!!
    // console.log('Popular: ', popular);
    console.log('Expires: ', expires);
    console.log('Active: ', activeClass);

};

setPageThread('New Version out Soon!', {
    // Options object with 3 properties
    popular: true,
    expieres: 10000,
    activeClass: 'is-page-thread'
});
```

* Setting a **default value** for the entire options argument allows this parameter to be omitted during function calls.

```js
    // Now is posible invoke this function without its second argument
function setPageThread(name, options = {}) {
    // Assign from proporties to local variables
    console.log('Name: ', name);
    // Is posible omit some arguments OjO not all!!
    // console.log('Popular: ', popular);
    console.log('Expires: ', expires);
    console.log('Active: ', activeClass);

};

setPageThread('New Version out Soon!');
```

## Rest parameter, spread operator and arrow functions

#### **ES5**

* **Issues with the arguments Object**. The *arguments* object is a built-in, Array-like object that corresponds to the arguments of a function.

Here's how we want our *displayTags* function to look.

```js

// Variadic functions can accept any number of arguments

displayTags('songs');
// or 
displayTags('songs', 'lyrics');
// or
displayTags('songs', 'lyrics', 'bands');


// Hard to tell which parameters this function expects to be called.

function() displayTags() {
    for(let i in arguments) {
        let tag = arguments[i];
        _addToTopic(tag);
    }
}
```
#### **ES6**

* The new rest parameter syntax allows us to represent an indefinity number of arguments as an **array**. 
This way, changes to function signature are **less likely to break code.**

```js

                    // These 3 dots are part of the syntax
function displayTags(...tags) {
    for(let i in tags) { // tags is an Array object
        let tag = tag[i];
        _addToTopic(tag);
    }
}

```
* **Splitting Arrays into individual arguments**. We need a way to convert **Array** into individual arguments upon a **function call**.

**Using the spread Operator**

```js

// The displayTags function is now receiving individual arguments, not an Array
displayTags(...tags);

// Same as doing

displayTags(tag, tag, tag);
```

* **Rest and Spread look the same.** Rest parameters and the spread operator look the same but not it is equal:
    * **Rest parameters** is used in **Function definitions**.
    * **Spread Operator**is used in **Function invocation**

```js
// Rest Parameters --> Function definition --> Argument as an Array
function displayTags(...tags) {
    for(let i in tags) { // tags is an Array object
        let tag = tag[i];
        _addToTopic(tag);
    }

// Spread Operator --> Function invocation --> Individual argument, not array
displayTags(...tags);
```



--> Set, create arrays without duplicate variables

new Set(['asd', 'asdf','aa']); --> ['asd','aa']

   D