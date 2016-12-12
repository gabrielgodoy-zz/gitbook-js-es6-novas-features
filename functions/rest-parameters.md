## Rest Parameters
It uses the `...` syntax and allows you to store trailing arguments in an array:

**Rest parameters must always be the last parameter**

```js
function doSomething(x, ...remaining) {
   return x * remaining.length;
}

doSomething(5, 0, 0, 0); // 15
```

**Difference between Rest and Spread operator**

Rest parameters is used in function definitions, and the spread operator is used in function invocations
