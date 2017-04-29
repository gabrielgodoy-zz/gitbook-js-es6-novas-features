## Default Parameters
Com ES6, definir valores padrão para parâmetros de uma função é possível 

A sintaxe é da seguinte maneira:
```js
function doSomething(x, y = 2) {
   return x * y;
}

doSomething(5); // 10
doSomething(5, undefined); // 10
doSomething(5, 3); // 15
```

### Rest e defaults

```js
let ajax = function({ url = "localhost", port: p = 80 }, ...data) {
    console.log("Url:", url, "Port:", p, "Rest:", data);
};

ajax({ url: "someHost" }, "additional", "data", "hello"); // Url: someHost Port: 80 Rest: [ 'additional', 'data', 'hello' ]

ajax({}, "additional", "data", "hello"); // Url: localhost Port: 80 Rest: [ 'additional', 'data', 'hello' ]

ajax({}); // Url: localhost Port: 80 Rest: []

// A tentativa abaixo não funciona porque se está tentando desestruturar undefined
ajax(); // Uncaught TypeError: Cannot match against 'undefined' or 'null'

// Para consertar isso, é preciso ter valores padrões para parâmetros da função
// Nota: Olhe o "= {}" no final, sinaliza um objeto vazio como padrão, caso o primeiro argumento seja undefined
let ajax = ({ url: url = "localhost", port: p = 80 } = {}) => {
    console.log("Url:", url, "Port:", p);
};

// Agora funciona
ajax(); // Url: localhost Port: 80

ajax({}); // Url: localhost Port: 80

ajax({ port: 8080 });
//  => Url: localhost Port: 8080

ajax({ url: "someHost", port: 8080 });
//  => Url: someHost Port: 8080
```
