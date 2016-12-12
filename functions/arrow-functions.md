## Arrow Functions

**Arrow functions are always anonymous.**
The *this* reference of an arrow function is the 'outer' this. The arrow function don't have its own this. 

Example:
```js
let books = [{title: 'X', price: 10}, {title: 'Y', price: 15}];

// ES6 Arrow function
let titles = books.map( item => item.title );

// The above is the same as:
var titles = books.map(function(item) {
   return item.title;
});
```

If we look at the syntax of arrow functions, there is no function keyword. What remains is zero or more arguments, the “fat arrow” (=>) and the function expression. The return statement is implicitly added.

With zero or more than one argument, you must provide parentheses:
```js
// No arguments
books.map( () => 1 ); // [1, 1]

// Multiple arguments
[1,2].map( (n, index) => n * index ); // [0, 2]
```

Put the function expression in a block ({ ... }) if you need more logic or more white space:
```js
let result = [1, 2, 3, 4, 5].map( n => {
   n = n % 3;
   return n;
});
```

