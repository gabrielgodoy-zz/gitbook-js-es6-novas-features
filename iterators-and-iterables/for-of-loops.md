## for...of loops

A declaração `for...of` itera sobre valores das propriedades de um objeto, 



The for...of statement iterates over property values, and it's better way to loop over arrays and other iterable objects.

* for..of only works with iterables. 
  Try to run for...of on objects return TypeError

```js
let names = ["Sam", "Alex", "Brook"];

// Uses index to read actual element
for(let i in names) {
    console.log(name[i]);
}

// Reads element directly and with less code involved
for(let name of names) {
    console.log(name);
}
```



