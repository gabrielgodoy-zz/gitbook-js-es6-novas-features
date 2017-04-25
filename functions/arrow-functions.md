## Arrow Functions
Principais características:

- Arrow functions são sempre anônimas
- Uma Arrow function não tem seu próprio `this`. A referência do `this` de uma arrow function é o `this` do escopo de fora.
- Não se utiliza a palavra `function`. Somente a seta `=>`
- A declaração de retorno é adiciona implicitamente 

Exemplo:
```js
let books = [{title: 'X', price: 10}, {title: 'Y', price: 15}];

// Com Arrow function
let titles = books.map(item => item.title);

// Sem Arrow Function
var titles = books.map(function(item) {
   return item.title;
});
```

Com somente um argumento em uma função, é possível omitir parênteses:
```js
let functionWithOneParam = value => console.log(value)
```

Com zero ou mais de um argumento, os parênteses são obrigatórios: 
```js
// No arguments
books.map(() => 1); // [1, 1]

// Múltiplos argumentos
[1,2].map((n, index) => n * index); // [0, 2]
```

Coloque chaves `{...}` caso se tenha necessidade de inserir mais lógica na função, ou mais espaço em branco.

```js
let result = [1, 2, 3, 4, 5].map( n => {
   n = n % 3;
   return n;
});
```
