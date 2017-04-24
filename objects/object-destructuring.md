## Desestruturando um objeto em variáveis

Exemplo de destructuring com objeto

```js
function buildUser(first, last){
  let fullName = first + " " + last;
  return { first, last, fullName };
}
// Criando a variável fullName e atribuindo a propriedade fullName retornada pelo objeto de função buildUser 
let { fullName } = buildUser("Tyler", "Williams");
```

Desestruturando objetos 
**Tenha certeza que as chaves dão match:**
```js
let obj = {x: 1, y: 2};
let {x, y} = obj; // x = 1, y = 2
```

Você também pode usar esse mecanismo para alterar nomes de variáveis:
```js
let obj = {x: 1, y: 2};
let {x: a, y: b} = obj; // a = 1, b = 2
```

A desestruturação pode ser usada para atribuir valores padrão a objetos de argumento.
Com um objeto literal, você pode realmente simular parâmetros nomeados.

```js
function doSomething({y = 1, z = 0}) {
   console.log(y, z);
}
doSomething({y: 2});
```

Mais em destructuring
[gist com exemplos de destructuring](https://gist.github.com/mikaelbr/9900818)
