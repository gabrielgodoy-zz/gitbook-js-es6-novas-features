## Template Literals
Template literals provide a clean way to create strings and perform string interpolation. 
You might already be familiar with the syntax; it’s based on the dollar sign and curly braces ${..}

Template literals are enclosed by backticks (`${}`)

Here’s a quick demonstration:
```js
let name = 'John',
   apples = 5,
   pears = 7,
   bananas = function() { return 3; };

console.log(`This is ${name}.`);
console.log(`He carries ${apples} apples, ${pears} pears, and ${bananas()} bananas.`);

// ES5 equivalent:
console.log('He carries ' + apples + ' apples, ' + pears + ' pears, and ' + bananas() +' bananas.');
```

In the form above, compared to ES5, they’re merely a convenience for string concatenation. However, template literals can also be used for multi-line strings. Keep in mind that white space is part of the string:
```js
let x = `1...
2...
3 lines long!`; // Yay

// ES5 equivalents:
var x = "1...\n" + 
"2...\n" +
"3 lines long!";

var x = "1...\n2...\n3 lines long!";
```

