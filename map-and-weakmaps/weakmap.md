## Weakmaps
The WeakMap is a type of Map where **only objects** can be passed as keys.
Primitive data types - such as strings, numbers, booleans, etc - are not allowed

```js
let user = {};
let mapSettings = new WeakMap();
mapSettings.set(user, "ES2015");

console.log(mapSettings.get(user)); // Get reads the 'user' entry | 'ES2015'
console.log(mapSettings.has(user)); // Returns true if there is an entrance for that key
console.log(mapSettings.delete(user)); // Removes an entry, and returns a boolean based on whether that entrance existed
```

**WeakMaps are not iterables with for...of for example**

**Weakmaps are better with memory**
WeakMaps are called weaks, because they hold weak references to the objects used as keys
```js
let user = {}; // All objects occupy memory space
let userStatus = new WeakMap();
mapStatus.set(user, "logged"); // Object reference passed as key to WeakMap
// ..
someOtherFunction(user); //Once it returns, 'user' can be garbage collected
```

WeakMaps don't prevent the garbage collector from collecting objects currently used as keys, but that are no longer referenced anywhere else in the system.

