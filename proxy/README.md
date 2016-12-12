## Proxy

Define different behaviours for methods inside an object.

The base syntax is `let myProxy = new Proxy(target, handler);`

**target** is an object (can be any object, including arrays, functions or even another proxy) or a function to wrap with Proxy.

**handler** is an object whose properties are functions which define the behavior of the proxy when an operation is performed on it.

**traps** Traps are used in Proxies to override native methods from an object. Trap is analogous to the concept of traps in operating systems.

### List of Handler methods
- `handler.getPrototypeOf()` A trap for Object.getPrototypeOf
- `handler.setPrototypeOf()` A trap for Object.setPrototypeOf
- `handler.isExtensible()` A trap for Object.isExtensible
- `handler.preventExtensions()` A trap for Object.preventExtensions
- `handler.getOwnPropertyDescriptor()` A trap for Object.getOwnPropertyDescriptor
- `handler.defineProperty()` A trap for Object.defineProperty
- `handler.has()` A trap for the in operator
- `handler.get()` A trap for getting property values
- `handler.set()` A trap for setting property values
- `handler.deleteProperty()` A trap for the delete operator
- `handler.ownKeys()` A trap for Object.getOwnPropertyNames
- `handler.apply()` A trap for a function call
- `handler.construct()` A trap for the new operator

#### Basic Example
In this example a random number between 1 and 10 gets returned as the default value when the object property does not exist 

It is using the get handler inside the object propety
```js
let handler = {
    get(object, prop) {
    	return prop in object ? object[prop] : Math.round(Math.random() * 10);
    }
};

let myProxy = new Proxy({}, handler);
myProxy.a = 1;
myProxy.b = undefined;

console.log(myProxy.a, myProxy.b); // 1, undefined
console.log(myProxy.anotherProperty); // Random number between 1 and 10
```
