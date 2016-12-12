## Arrow Functions
Arrow functions main characteristics:

- Arrow functions are always anonymous
- The arrow function don't have its own this. The *this* reference of an arrow function is the 'outer' this. 
- There is no function keyword. Just the `=>` 
- The return statement is implicitly added

Example:
```js
let books = [{title: 'X', price: 10}, {title: 'Y', price: 15}];

// With Arrow function
let titles = books.map(item => item.title);

// Without Arrow Function
var titles = books.map(function(item) {
   return item.title;
});
```

With just one argument on a function, you can ommit parentheses:
```js
let functionWithOneParam = value => console.log(value)
```

With zero or more than one argument, you must provide parentheses:
```js
// No arguments
books.map(() => 1); // [1, 1]

// Multiple arguments
[1,2].map((n, index) => n * index); // [0, 2]
```

Put the function expression in a braces block `{...}` if you need more logic or more white space:
```js
let result = [1, 2, 3, 4, 5].map( n => {
   n = n % 3;
   return n;
});
```
