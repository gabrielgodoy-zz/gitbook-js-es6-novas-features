## Tagged templates literal
Permite modificar a saída de template literals usando uma função.

```js
let a = 5,
	b = 10;

/*
O primeiro argumento contém um array de string
literals ("Olá", "mundo" e "" neste caso abaixo)
O segundo, e cada argumento após o primeiro, são os valores das
(Ou às vezes chamado cooked) expressões de substituição ("15" e "50" aqui) processadas
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
// No final, sua função retorna sua string manipulada.
// "Bazinga!"
```

As funções Tag não precisam retornar uma string, como mostrado no exemplo a seguir:
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
A propriedade especial raw, disponível no primeiro argumento de função de tagged temoplates literals, permite que você acesse as raw strings conforme elas foram inseridas.
```js
function tag(strings, ...values) {
  console.log(strings.raw[0]); 
  // "string text line 1 \n string text line 2"
}

tag`string text line 1 \n string text line 2`;
```

Além disso, o método `String.raw()` existe para criar strings raw exatamente como uma `default template function` e uma concatenação de string iria criar.

```js
String.raw`Hi\n${2+3}!`;
// "Hi\n5!"
```
