## Weakmaps
O Weakmap é um tipo de Map que **soment objetos** podem ser passados como chaves.
Tipos de dados primitivos, como strings, números, booleanos, etc - não são permitidos

```js
let user = {};
let mapSettings = new WeakMap();
mapSettings.set(user, "ES2015");

console.log(mapSettings.get(user)); // Get lê a registro 'user' | 'ES2015'
console.log(mapSettings.has(user)); // Retuorna true se tem um registro para essa chave
console.log(mapSettings.delete(user)); // Remove um registro e retorna um booleano baseado se esse registro existe 
```

**WeakMaps não são iterables com for...of por exemplo**

**Weakmaps são melhores com memória**
WeakMaps são chamados weaks, porque eles armazenam referências fracas dos objetos usados como chaves.

```js
let user = {}; // Todos os objetos ocupam espaço na mémória
let userStatus = new WeakMap();
mapStatus.set(user, "logged"); // referência de objeto passado como chave ao WeakMap 
someOtherFunction(user); // Uma vez que ele retorna 'user' pode ser coletado pelo garbage collector
```

WeakMaps não impedem o coletor de lixo de coletar objetos atualmente usados como chaves, mas que não são mais referenciados em nenhum outro lugar no sistema.
