## Array destructuring
Destructuring allows to extract data from arrays or objects into distinct variables

```js
// Old way
let users = ["Sam","Tyler","Brook"];
let a = users[0];
let b = users[1];
let c = users[2];
console.log(a,b,c);

// ES6 way
let users = ["Sam","Tyler","Brook"];
let [a, b, c] = users;
console.log(a, b, c); // Sam Tyler Brook
```

Another example
```js
let [x, y] = [1, 2]; // x = 1, y = 2

// Old way
var arr = [1, 2];
var x = arr[0];
var y = arr[1];
```

With this syntax, multiple variables can be assigned a value in one go.
```js
let x = 1,
    y = 2;

[x, y] = [y, x]; // x = 2, y = 1
```

### Destructuring arrays from return values
```js
// When returning arrays from functions, we can assign to multiple variables at once
function activeUsers() {
	return ["Sam", "Alex", "Brook"];
}
let [a, b, c] = activeUsers();
console.log(a, b, c);
```

### Ignoring some returned values
You can ignore return values that you're not interested in:
```js
function activeUsers() {
  return ["Sam", "Alex", "Brook"];
}

let [a, , b] = activeUsers();
console.log(a); // Sam
console.log(b); // Brook
```

### Combining Array destructuring with Rest parameters
```js
let users = ["Sam","Tyler","Brook"];
let [first, ...rest] = users;
console.log(first + ", " + rest); // Sam, ["Tyler", "Brook"]
```
