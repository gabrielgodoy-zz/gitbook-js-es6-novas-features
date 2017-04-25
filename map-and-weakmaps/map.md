## Maps
Maps são estrutura de dados compostas de uma coleção de pares **chave/valor**
 Maps são úteis para armazenar dados simples, como valores de propriedade.

O método **set\(\)** é usado para adicionar entradas, e o método **get\(\)** para ler entradas

### Problemas ao usar objetos como mapas

Quando usar Objetos como chaves, **suas chaves são sempre convertidas para strings**

```js
// Dois objetos diferentes
let user1 = {name: "Sam"},
    user2 = {name: "Tyler"};

let totalReplies = {};

// Os dois objetos abaixo são convertidos para a string '[object Object]'
totalReplies[user1] = 5;
totalReplies[user2] = 42;

console.log(totalReplies[user1]); // 42
console.log(totalReplies[user2]); // 42
console.log(Object.keys(totalReplies)); // ['[object Object]']
```
Map resolve esse problema:
Quando usamos objetos como chaves em um map, eles não são convertidos para strings

```js
let user1 = {name: "Sam"},
     user2 = {name: "Tyler"};

let totalReplies = new Map();
// Esses dois valores são propriamente atribuídos a diferentes chaves
totalReplies.set(user1, 5);
totalReplies.set(user2, 42);

// Usamos os métodos get() e set() para acessar valores em Maps
console.log(totalReplies.get(user1)); // 5
console.log(totalReplies.get(user2)); // 42
```

### Quando usar maps ou objetos para armazenar dados?
Use Maps quando chaves não são conhecidas até runtime

_Chaves desconhecidas até o runtime, então...Map!_

```js
let recentPosts = new Map();
createPost(newPost, (data) => {
  	// Não se sabe qual dados do author vai ser até que se rode o código
    recentPosts.set(data.author, data.message)
});
```
_Chaves são previamente conhecidas, então...Objetos!_

```js
const POSTS_PER_PAGE = 15;
let userSettings = {
    perPage: POSTS_PER_PAGE,
    showRead: true
}
```

### Iterando Maps com for...of

```js
let mapSettings = new Map();

mapSettings.set("user", "Sam");
mapSettings.set("topic", "ES2015");
mapSettings.set("replies", ["Mal posso esperar!", "Tão legal"]);

for(let [key, value] of mapSettings) {
    console.log(`${key} = ${value}`);
}
```
