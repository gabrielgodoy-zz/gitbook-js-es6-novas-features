## Proxy

Definir comportamentos diferentes para métodos dentro de um objeto.

A sintaxe base é `let myProxy = new Proxy (target, handler);`

**target** é um objeto (pode ser qualquer objeto, incluindo arrays, funções ou até mesmo outro proxy) ou uma função para quebrar com Proxy.

**manipulador** é um objeto cujas propriedades são funções que definem o comportamento do proxy quando uma operação é realizada sobre ele.

**traps (armadilhas)** Armadilhas são usadas em Proxies para substituir métodos nativos de um objeto. Trap é análogo ao conceito de armadilhas em sistemas operacionais.

### Liste de métodos Handler 
- `handler.getPrototypeOf()` Uma armadilha para Object.getPrototypeOf
- `handler.setPrototypeOf()` Uma armadilha para Object.setPrototypeOf
- `handler.isExtensible()` Uma armadilha para Object.isExtensible
- `handler.preventExtensions()` Uma armadilha para Object.preventExtensions
- `handler.getOwnPropertyDescriptor()` Uma armadilha para Object.getOwnPropertyDescriptor
- `handler.defineProperty()` Uma armadilha para Object.defineProperty
- `handler.has()` Uma armadilha para the in operator
- `handler.get()` Uma armadilha para getting property values
- `handler.set()` Uma armadilha para setting property values
- `handler.deleteProperty()` Uma armadilha para the delete operator
- `handler.ownKeys()` Uma armadilha para Object.getOwnPropertyNames
- `handler.apply()` Uma armadilha para uma chamada de função
- `handler.construct()` Uma armadilha para the new operator

#### Exemplo Básico
Neste exemplo, um número aleatório entre 1 e 10 é retornado como o valor padrão quando a propriedade do objeto não existe

Ele está usando o manipulador `get` dentro da propriedade do objeto

```js
let handler = {
    get(object, prop) {
    	return prop in object ? object[prop] : Math.round(Math.random() * 10);
    }
};

let myProxy = new Proxy({}, handler);
myProxy.a = 1;
myProxy.b = undefined;

console.log(myProxy.a, myProxy.b); // 1, undefined
console.log(myProxy.anotherProperty); // Número aleatório entre 1 e 10
```
