## Symbols
Symbols são um novo tipo de dados primitivos, como Number e String. Você pode usar symbols para criar identificadores exclusivos para propriedades de objeto ou para criar constantes exclusivas.

```js
const MY_CONSTANT = Symbol();

let obj = {};
obj[MY_CONSTANT] = 1;
```

Observe que pares de valor-chave definidos com symbols não são retornados por `Object.getOwnPropertyNames()` e eles não são visíveis em iterações `for...in`, `Object.keys()` ou `JSON.stringify()`.

Isso está em contraste com chaves baseadas em string.

Você pode obter um array de symbols para um objeto com `Object.getOwnPropertySymbols()`

Os símbolos trabalham naturalmente com `const` devido ao seu caráter imutável:

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

Você pode dar a um symbol uma descrição. Você não pode usá-lo para acessar o próprio símbolo, mas é útil para debugging.

```js
const CONST_1 = Symbol('my symbol');
const CONST_2 = Symbol('my symbol');

typeof CONST_1 === 'symbol'; // true

CONST_1 === CONST_2; // false
```
