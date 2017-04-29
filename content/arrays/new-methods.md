## Métodos estáticos de Array
O objeto Array recebeu novos métodos estáticos, assim como novos métodos em seu `prototype`

### Array.from()
`Array.from` cria um Array a partir de `array-like` e objetos iteráveis. array-like são objetos parecidos com a estrutura de array mas que não são arrays.

Exemplos de objetos `array-like` incluem:
* Uma lista de nodes retornados por **document.getElementsByTagName\(\)**
* As novas estruturas de dados como `Map` e `Set`
  
No exemplo abaixo, o array `items` possui o método forEach, que não está disponível na coleção `itemElements` 
```js
let itemElements = document.querySelectorAll('.items');
let items = Array.from(itemElements);
items.forEach((element) => {
    console.log(element.nodeType)
});

// Solução alternativa utilizada no ES5:
let items = Array.prototype.slice.call(itemElements);
```

Uma feature interessante de `Array.from` é o segundo argumento `mapFunction`, que é opcional.

Ele permite que se crie um novo array mapeado em uma só chamada:
```js
let navElements = document.querySelectorAll('nav li'),
    navTitles = Array.from(navElements, el => el.textContent);
```

### Array.of()
O método Array.of() cria uma nova Array com um número variável de argumentos, independente do número ou do tipo dos argumentos.

A diferença entre o `Array.of()` e os construtores de Array é no tratamento dos argumentos inteiros: `Array.of(42)` cria um array com um único elemento, 42, enquanto Array(42) cria um array com 42 elementos, cada um com valor `undefined`:

```js
let x = new Array(3); // [undefined, undefined, undefined]
let y = Array.of(8); // [8]
let z = [1, 2, 3]; // Array literal
```

## Métodos do protótipo Array
Alguns métodos foram adicionados ao protótipo do Array.

### Array.find()
Array.find retorna o primeiro elemento na array que satisfaz uma determinada condição

```js
// Encontre um admin no array de users
let names = [{
    login: "Sam",
    isAdmin: false
}, {
    login: "Brook",
    isAdmin: true
}, {
    login: "Tyler",
    isAdmin: true
}];

// Retorna o primeiro objeto onde o usuário admin é true
let admin = users.find((user) => {
    return user.isAdmin;
});

console.log(admin); // {login: "Brook", isAdmin: true}
```

**find** retorna o primeiro elemento no qual a função avalia como `True`  

> `arr.find(callback[, thisArg])`

```js
[5, 1, 10, 8].find(n => n === 10) // 10
```

**findIndex** retorna o index do primeiro elemento no qual a funçao de avalia como `True`

> `arr.findIndex(callback[, thisArg])`

```js
[5, 1, 10, 8].findIndex(n => n === 10) // 2
```

**fill** "substitui" os elementos do array com um argumento
 
> `arr.fill(value[, start = 0[, end = this.length]])`

```js
[0, 0, 0].fill(7); // [7, 7, 7]
[0, 0, 0, 0, 0].fill(7, 1, 3); // [0, 7, 7, 7, 0]
```

### Array.copyWithin()
O método `copyWithin()` copia de maneira superficial parte de uma array para outro lugar na mesma array e retorna isso, sem modificar o tamanho dessa array. Embora copyWithin() não modifique o tamanho da Array, ela causa uma mutação nela. 

```js
["alpha", "bravo", "charlie", "delta"].copyWithin(2, 0);
// resulta em ["alpha", "bravo", "alpha", "bravo"]
```
