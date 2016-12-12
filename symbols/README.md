## Symbols
Symbols are a new primitive data type, like Number and String. You can use symbols to create unique identifiers for object properties or to create unique constants.

```js
const MY_CONSTANT = Symbol();

let obj = {};
obj[MY_CONSTANT] = 1;
```

Note that key-value pairs set with symbols are not returned by Object.getOwnPropertyNames(), and they are not visible in for...in iterations, Object.keys() or JSON.stringify(). 
This is in contrast to regular string-based keys. 
You can get an array of symbols for an object with Object.getOwnPropertySymbols().
Symbols work naturally with const because of their immutable character:

```js
const CHINESE = Symbol();
const ENGLISH = Symbol();
const SPANISH = Symbol();


switch(language) {
   case CHINESE:
      // 
      break;
   case ENGLISH:
      // 
      break;
   case SPANISH:
      // 
      break;
   default:
      // 
      break;
}
```

You can give a symbol a description. You can’t use it to access the symbol itself, but it’s useful for debugging.

```js
const CONST_1 = Symbol('my symbol');
const CONST_2 = Symbol('my symbol');

typeof CONST_1 === 'symbol'; // true

CONST_1 === CONST_2; // false
```
