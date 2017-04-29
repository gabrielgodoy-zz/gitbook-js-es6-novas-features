## Sets
O objeto **Set** armazena valores únicos de qualquer tipo, seja primitivas ou referências a objetos

Problemas com arrays

Em arrays, entradas duplicadas são permitidas, como abaixo:

```js
let tags = [];


tags.push("Javascript");
tags.push("Programming");
tags.push("Web");
tags.push("Web"); // Duplicate entry


console.log("Total items: ", tags.length); // 4
```

Sets impedem entradas duplicadas
Usamos o método `add()` para adicionar elementos a um Set

```js
let tags = new Set();
tags.add("Javascript");
tags.add("Programming");
tags.add({version: "2015"}); // Valires primitivos e objetos são permitidos
tags.add("Web");
tags.add("Web"); // Entradas duplicadas são ignoradas

console.log('Total items: ', tags.size); // 4, o segundo "Web" foi ignorado
```

**Sets são iteráveis. Podemos usá-los com for...of e desestruturação**

```js
let tags = new Set();
tags.add("Javascript");
tags.add("Programming");
tags.add({version: "2015"});
tags.add("Web");

for(let tag of tags) {
	console.log(tag);
}

// Destructure assignment allowed on Sets
let [a, b, c, d] = tags;
console.log(a, b, c, d);
```
