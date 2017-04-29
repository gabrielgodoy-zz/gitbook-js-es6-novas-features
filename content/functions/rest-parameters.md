## Parâmetros Rest
Ele usa a sintaxe `...` e permite que se armazene múltiplos argumentos em um array:

**Parâmetros Rest precisam sempre ser o último parâmetro**

```js
function doSomething(x, ...remaining) {
   return x * remaining.length;
}

doSomething(5, 0, 0, 0); // 15
```

**Diferença entre operadores Rest e Spread**

Parâmetro Rest é usado quando a função é definida, e o operador spread é usado quando a função é invocada.
