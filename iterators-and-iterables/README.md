# Iterator

Um objeto é um iterator quando ele sabe como acessar items de uma coleção, um de cada vez, enquanto mantém controle da sua posição atual dentro dessa sequência.

Em JavaScript um iterator é um objeto que fornece um método `next()` que retorna o próximo item na seqüência. 

Este método retorna um objeto com duas propriedades: `done` e `value`.

```js
// Exemplo de um criador de Iterator customizado
function makeCustomIterator (array) {
    let nextIndex = 0;
    return {
        next() {
            return nextIndex < array.length ? { value: array[nextIndex++], done: false } : { done: true };
        }
    }
}

/*
 makeIteratorFunc guarda um objeto com o método next nele
 */
let makeIteratorFunc = makeCustomIterator(["Gabriel", "Godoy"]);

console.log('Custom Iterator: ', makeIteratorFunc.next()); // { value: 'Gabriel', done: false }
console.log('Custom Iterator: ', makeIteratorFunc.next()); // { value: 'Godoy', done: false }
console.log('Custom Iterator: ', makeIteratorFunc.next().done); // true
```


Iterators customizados como makeCustomIterator requerem a administração do estado interno do Iterator. Generators são "fábricas de iterators", onde a palavra-chave **yield** define o ponto no qual a função irá parar quando o próximo método next() for chamado.

O mesmo resultado da função makeCustomIterator pode ser alcançado com um generator sem ter que administrar manualmente o estado do iterator, e o que deve ser retornado.

## Iterables
An object is iterable if it defines its iteration behavior, such as what values are looped over in a for..of construct.

In order to be iterable, an object must implement the @@iterator method, the object (or one of the objects up its prototype chain) must have a property with a Symbol.iterator key

Built-in iterables

String, Array, TypedArray, Map and Set are all built-in iterables, because the prototype objects of them all have a Symbol.iterator method
```js
function runIterable (iterable) {
    for (let element of iterable) {
        console.log('Iterable element: ', element);
    }
}

runIterable(['Gabriel', 'Godoy']);
// Iterable element:  Gabriel
// Iterable element:  Godoy

runIterable('Gabriel');
// Iterable element:  G
// Iterable element:  a
// Iterable element:  b
// Iterable element:  r
// Iterable element:  i
// Iterable element:  e
// Iterable element:  l
```

### Custom Iterable

This literal object below natively neither have nor inherit Symbol.iterator property. But we can make this one Iterable by addin [Symbol.iterator] property to it.

```js
let myIterable = {};

// Add Symbol.iterator to it
myIterable[Symbol.iterator] = function* () {
    yield 1;
    yield 2;
    yield 3;
};

// And now it becomes iterable
for(let value of myIterable){
    console.log(value);
}
// 1
// 2
// 3
```

