## Default Parameters
In ES6, defining default values for function parameters is possible. 

The syntax is as follows:
```js
function doSomething(x, y = 2) {
   return x * y;
}

doSomething(5); // 10
doSomething(5, undefined); // 10
doSomething(5, 3); // 15
```

### Rest and defaults

```
let ajax = function({ url = "localhost", port: p = 80 }, ...data) {
    console.log("Url:", url, "Port:", p, "Rest:", data);
};

ajax({ url: "someHost" }, "additional", "data", "hello"); // Url: someHost Port: 80 Rest: [ 'additional', 'data', 'hello' ]

ajax({}, "additional", "data", "hello"); // Url: localhost Port: 80 Rest: [ 'additional', 'data', 'hello' ]

ajax({}); // Url: localhost Port: 80 Rest: []

// Doesn't work due to trying to destructure undefined
ajax(); // Uncaught TypeError: Cannot match against 'undefined' or 'null'

// To fix this we need to have default value for parameter in function
// Note: See the `= {}` at the end, saying default empty object if the first argument is undefined.
let ajax = ({ url: url = "localhost", port: p = 80 } = {}) => {
    console.log("Url:", url, "Port:", p);
};

// Now this works.
ajax(); // Url: localhost Port: 80

ajax({}); // Url: localhost Port: 80

ajax({ port: 8080 });
//  => Url: localhost Port: 8080

ajax({ url: "someHost", port: 8080 });
//  => Url: someHost Port: 8080

```
