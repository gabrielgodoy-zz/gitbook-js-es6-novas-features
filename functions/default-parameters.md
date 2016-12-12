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
