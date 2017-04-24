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
Um objeto é um iterable se define seu comportamento ao iterar, como quais valores são exibidos durante um loop do construtor `for...of`

Para ser iterable, um objeto precisa implementar o método @@iterator, o objeto (ou um dos objetos até ao longo da cadeia de protótipo) precisa ter a propriedade com a chave `Symbol.iterator`

### Iterables nativos

String, Array, TypedArray, Map e Set são todos iterables nativos, porque os objetos de protótipo de todos eles tem o método `Symbol.iterator`
```js
function runIterable (iterable) {
    for (let element of iterable) {
        console.log('Iterable element: ', element);
    }
}

runIterable(['Gabriel', 'Godoy']);
// Elemento iterable:  Gabriel
// Elemento iterable:  Godoy

runIterable('Gabriel');
// Elemento Iterable :  G
// Elemento Iterable :  a
// Elemento Iterable :  b
// Elemento Iterable :  r
// Elemento Iterable :  i
// Elemento Iterable :  e
// Elemento Iterable :  l
```

### Iterable customizado
Esse objeto literal abaixo não tem nem herdaa propriedade `Symbol.iterator`. Mas é possível tornar ele iterável adicionando a propriedade [Symbol.iterator] para ele
```js
let myIterable = {};

// Adiciona Symbol.iterator para ele
myIterable[Symbol.iterator] = function* () {
    yield 1;
    yield 2;
    yield 3;
};

// E agora se torna iterable
for(let value of myIterable){
    console.log(value);
}
// 1
// 2
// 3
```
