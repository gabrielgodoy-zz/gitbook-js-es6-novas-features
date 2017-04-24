## Array destructuring
Destructuring permite extrair dados de arrays ou objetos em variáveis distintas

```js
// Maneira antiga
let users = ["Sam","Tyler","Brook"];
let a = users[0];
let b = users[1];
let c = users[2];
console.log(a,b,c);

// Com ES6
let users = ["Sam","Tyler","Brook"];
let [a, b, c] = users;
console.log(a, b, c); // Sam Tyler Brook
```

Outro exemplo
```js
let [x, y] = [1, 2]; // x = 1, y = 2

// Maneira antiga
var arr = [1, 2];
var x = arr[0];
var y = arr[1];
```

Com essa sintaxe, múltiplas variáveis podem ter valor atribuído de uma só vez
```js
let x = 1,
    y = 2;

[x, y] = [y, x]; // x = 2, y = 1
```

### Destructuring arrays de valores de retorno
```js
// Ao retornar arrays de funções, é possível atribuir valores a múltiplas variáveis de uma só vez
function activeUsers() {
	return ["Sam", "Alex", "Brook"];
}
let [a, b, c] = activeUsers();
console.log(a, b, c);
```

### Ignorando valores retornados
É possível ignorar valores de retorno que nõ seja interessante
```js
function activeUsers() {
  return ["Sam", "Alex", "Brook"];
}

let [a, , b] = activeUsers();
console.log(a); // Sam
console.log(b); // Brook
```

### Combinando destructuring de Array com parâmetros Rest
```js
let users = ["Sam","Tyler","Brook"];
let [first, ...rest] = users;
console.log(first + ", " + rest); // Sam, ["Tyler", "Brook"]
```
