## Generators (Geradores)
Um Generator administra seu próprio estado iterativo, elas são funções `pausáveis`. 

Uma função se torna um generator se ela contém um ou mais expressões **yield** (produzir)  e se utiliza a sintaxe com asterisco `function*`

### O método `next()` de um Generator
O `next()` permite que se itere dentro de um generator

Quando se atribui uma variável que armazena sua função de generator como:

`const ajaxGenSetup = ajaxGen();`

A quantidade de `next()` disponíveis para se usar representam a mesma quantidade de yields presentes na função do generator, até que `done = true`

O método `next()` retorna um objeto com duas propriedades, **done** and **value**.

`{ value: 3, done: false }`

Cada termo `yield` é um ponto de parada para um método `next()`

Na função abaixo, quando não existem mais yields para se parar, o generator retorna a propriedade done como `true` 

```js
let myGenerator = function*() {
    yield 1;
    yield 2;
    yield 3;
};

// Armazena o generator em uma variável
let gen = myGenerator();

// O método next retorna o que é programado para ser produzido na função
console.log(gen.next()); // { value: 1, done: false } 
console.log(gen.next()); // { value: 2, done: false } 
console.log(gen.next()); // { value: 3, done: false }
console.log(gen.next()); // { value: undefined, done: true } 
```

### Enviando valores para o Generator através do método `next()`
```js
function *foo() {
    let x = 1 + (yield "foo");
    console.log(x);
}

let storeGen = foo();
storeGen.next(); // {value: "foo", done: false}
storeGen.next(50); // {value: undefined, done: true}
// Logs x = 51;
```

A expressão yield "foo" vai enviar o valor em string "foo" quando se pausar a função geradora nesse ponto.
 
E em qualquer momento que o generator é reiniciado com outra função `next()`, qualquer que seja o valor enviado, será o resultado dessa expressão yield, que então será adicionado `1`, e atribuído para a variável `x`. 

****

**É como se o termo yield estivesse pausando e meio que fazendo um request externo por um valor. Esperando pelo próximo next() com um valor embutido nele**


O valor passado no método `next()` meio que 'substitui' toda a expressão yield que foi pausada por último.


### Generators para ações Async
É possível definir uma ordem específica para requisições assíncronas para rodar com geradores

Peguei esse exemplo em um [curso muito bom de um amigo meu](http://willianjusten.teachable.com/p/js-com-tdd-na-pratica).
```js
function ajax(url) {
	fetch(url)
		.then(data => data.json())
		// Essa função chama o próximo yield dentro do ajaxGen com os dados buscados como argumento
		.then(data => ajaxGenSetup.next(data));
}

// Código assíncrono que parece que é síncrono
function* ajaxGen() {
	console.log('Buscando posts...');
	const posts = yield ajax('https://willianjusten.com.br/search.json');
	console.log(posts);
	console.log('Buscando dados do Github...');
	const github = yield ajax('https://api.github.com/users/willianjusten');
	console.log(github);
	console.log('Buscando dados do Github 2...');
	const github2 = yield ajax('https://api.github.com/users/willianjusten');
	console.log(github2);
}

// Pega o gerador e todos os métodos next() de acordo com o número de yields dentro dele
const ajaxGenSetup = ajaxGen();


// Esse primeiro next() dispara o gerador e para no primeiro yield
// tem o valor de undefined, porque não existe yield inicialmente 'aguardando' por um valor
ajaxGenSetup.next(); // {value: undefined, done: false}

// Buscando posts...
// Ajax Data
// Buscando dados do Github...
// Ajax Data
// Buscando dados do Github 2...
// Ajax Data
```

### yield*
A expressão **yield*** é usada para delegar para um outro gerador ou objeto iterável

Exemplo de delegação para outro generator

```js
function* g1() {
  yield 2;
  yield 3;
  yield 4;
}

function* g2() {
  yield 1;
  yield* g1();
  yield 5;
}

let iterator = g2();

console.log(iterator.next()); // { value: 1, done: false }
console.log(iterator.next()); // { value: 2, done: false }
console.log(iterator.next()); // { value: 3, done: false }
console.log(iterator.next()); // { value: 4, done: false }
console.log(iterator.next()); // { value: 5, done: false }
console.log(iterator.next()); // { value: undefined, done: true }
```

E com outro objeto iterável como Arrays e Strings

```js
function* g3() {
  yield* [1, 2];
  yield* "34";
  yield* Array.from(arguments);
}

let iterator = g3(5, 6);

console.log(iterator.next()); // { value: 1, done: false }
console.log(iterator.next()); // { value: 2, done: false }
console.log(iterator.next()); // { value: "3", done: false }
console.log(iterator.next()); // { value: "4", done: false }
console.log(iterator.next()); // { value: 5, done: false }
console.log(iterator.next()); // { value: 6, done: false }
console.log(iterator.next()); // { value: undefined, done: true }
```
