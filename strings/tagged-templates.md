## Tagged templates literal
Allows to modify the output of template literals using a function.
```js
let a = 5,
	b = 10;

/*
The first argument contains an array of string 
literals ("Hello " , " world", and "" in this case below)
The second, and each argument after the first one, 
are the values of the processed 
(or sometimes called cooked) substitution expressions ("15" and "50" here).
*/
function someFunction(strings, ...values) {
  console.log(strings[0]); // "Hello "
  console.log(strings[1]); // " world "
  console.log(strings[2]); // ""
  console.log(values[0]);  // 15
  console.log(values[1]);  // 50

  return "Bazinga!";
}

someFunction`Hello ${ a + b } world ${ a * b }`;
//In the end, your function returns your manipulated string.
// "Bazinga!"
```

Tag functions don't need to return a string, as shown in the following example.
```js
function template(strings, ...keys) {
  return (function(...values) {
    let dict = values[values.length - 1] || {},
    	result = [strings[0]];
    keys.forEach(function(key, i) {
      let value = Number.isInteger(key) ? values[key] : dict[key];
      result.push(value, strings[i + 1]);
    });
    return result.join('');
  });
}

let t1Closure = template`${0}${1}${0}!`;
t1Closure('Y', 'A');  // "YAY!" 
let t2Closure = template`${0} ${'foo'}!`;
t2Closure('Hello', {foo: 'World'});  // "Hello World!"
```

### Raw Strings
The special raw property, available on the first function argument of tagged template literals, allows you to access the raw strings as they were entered.
```js
function tag(strings, ...values) {
  console.log(strings.raw[0]); 
  // "string text line 1 \n string text line 2"
}

tag`string text line 1 \n string text line 2`;
```

In addition, the String.raw() method exists to create raw strings just like the default template function and string concatenation would create.
```js
String.raw`Hi\n${2+3}!`;
// "Hi\n5!"
```
