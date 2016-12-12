## Spread Operators
The spread operator `...` is a syntax to expand elements of an array in specific places, such as arguments in function calls.

**Difference between Rest and Spread operator**
 
Rest parameters is used in function definitions, and the spread operator is used in function invocations

### In Arrays
Expand elements of an array within another array:

```js
let values = [1, 2, 4],
	some = [...values, 8], // [1, 2, 4, 8]
	more = [...values, 8, ...values]; // [1, 2, 4, 8, 1, 2, 4]

// Old JS
let values = [1, 2, 4];
// Iterate, push, sweat, repeat...
// Iterate, push, sweat, repeat...
```

### In Function calls
The spread syntax is also powerful when calling functions with arguments:

```js
let values = [1, 2, 4];

doSomething(...values); // Same as doSomething(values[0], values[1], values[2])
```

The syntax is very flexible, because the spread operator can be used anywhere in the argument list. 

This means that the following invocation produces the same result:
```js
let values = [2, 4];
doSomething(1, ...values);  // Same as doSomething(1, values[0], values[1])
```

### In iterables 
It can be applied to all iterable objects, such as a NodeList:
```js
let form = document.querySelector('#my-form'),
	inputs = form.querySelectorAll('input'),
	selects = form.querySelectorAll('select');

let allElements = [form, ...inputs, ...selects];
// Now, allElements is a flat array containing the `<form>` node and its `<input \>` and `<select>` child nodes.
```

### In Objects
Lets you use the spread `...` operator to copy enumerable properties from one object to another or override them
```js
let state = {someProp: '', visibilityFilter: false};
function mergeObjects(state) {
	return { ...state, visibilityFilter: true }
}
```
