## for...of loops

A declaração `for...of` itera sobre valores das propriedades de um objeto, e é uma maneira melhore de fazer um loop em arrays e outros objetos iteráveis.


* `for..of` funciona somente com iteráveis.

Tentar rodar `for...of` em objetos retorna TypeError

```js
let names = ["Sam", "Alex", "Brook"];

// Utiliza o index para ler o elemento em si
for(let i in names) {
    console.log(name[i]);
}


// Lê o elemento diretamente e com menos código escrito
for(let name of names) {
    console.log(name);
}
```
