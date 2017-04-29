## Inicializador de objetos
Só funciona se a variável tem os mesmos nomes que as chaves do objeto que está sendo inicializado

```js
// Old JS
var name = "Brook",
	totalReplies = 249,
	avatar = "/users/avatars/brook-user-1.jpg",
	user = {name: name, totalReplies: totalReplies, avatar: avatar};

// ES6
let name = "Brook",
	totalReplies = 249,
	avatar = "/users/avatars/brook-user-1.jpg",
	user = {name, totalReplies, avatar};
```

### Forma abreviada para nomes de propriedades de um objeto (ES6) 

```js
// Old JS
var a = "foo", 
    b = 42,
    c = {},
	obj = {a: a, b: b, c: c};

// ES6
let a = "foo", 
    b = 42, 
    c = {},
	obj = {a, b, c};
```

### Nomes de propriedades computadas (ES6)
Esse recurso permite definir nomes de chaves dinâmicas de um objeto literal

```js
let prop = "foo",
	obj = {
	  [prop]: "hey",
	  ["b" + "ar"]: "there",
	};
```
