## Destructuring an Object into variables

Example of object destructuring:
```js
function buildUser(first, last){
  let fullName = first + " " + last;
  return { first, last, fullName };
}
// Creating variable fullName, and assigning the fullName property returned by buildUser Function Object 
let { fullName } = buildUser("Tyler", "Williams");
```

Destructuring objects. 
**Make sure to have matching keys:**
```js
let obj = {x: 1, y: 2};
let {x, y} = obj; // x = 1, y = 2
```

You could also use this mechanism to change variable names:
```js
let obj = {x: 1, y: 2};
let {x: a, y: b} = obj; // a = 1, b = 2
```

Destructuring can be used to assign default values to argument objects. 
With an object literal, you can actually simulate named parameters.
```js
function doSomething({y = 1, z = 0}) {
   console.log(y, z);
}
doSomething({y: 2});
```

More on destructuring
[Destructuring gist examples](https://gist.github.com/mikaelbr/9900818)
