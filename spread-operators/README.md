## Spread Operators
The spread operator (...) is a syntax to expand elements of an array in specific places, such as arguments in function calls.

First, let’s see how to expand elements of an array within another array:

```js
let values = [1, 2, 4];
let some = [...values, 8]; // [1, 2, 4, 8]
let more = [...values, 8, ...values]; // [1, 2, 4, 8, 1, 2, 4]


// ES5 equivalent:
let values = [1, 2, 4];
// Iterate, push, sweat, repeat...
// Iterate, push, sweat, repeat...
```

The spread syntax is also powerful when calling functions with arguments:
```js
let values = [1, 2, 4];

doSomething(...values);

function doSomething(x, y, z) {
   // x = 1, y = 2, z = 4
}

// ES5 equivalent:
doSomething.apply(null, values);
```

As you can see, this saves us from the often-used fn.apply() workaround. The syntax is very flexible, because the spread operator can be used anywhere in the argument list. This means that the following invocation produces the same result:
```js
let values = [2, 4];
doSomething(1, ...values);
```

We’ve been applying the spread operator to arrays and arguments. In fact, it can be applied to all iterable objects, such as a NodeList:

```js
let form = document.querySelector('#my-form'),
   inputs = form.querySelectorAll('input'),
   selects = form.querySelectorAll('select');

let allTheThings = [form, ...inputs, ...selects];
```
Now, allTheThings is a flat array containing the <form> node and its <input> and <select> child nodes.
