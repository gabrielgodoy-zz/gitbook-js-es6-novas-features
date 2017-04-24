## let
Um novo jeito de criar escopo

Utilizando **var = variável** seu escopo está preso dentro da função mais próxima que envolve ela
Utilizando **let = variável** seu escopo está preso dentro dos colchetes mais próximos que envolve ela


*declarações 'let' não causam `hoist`, por isso se torna necessário colocar todas suas declaraçòes let no topo dos blocos antes de serem usadas*

```js
if(true) {
   let x = 1;
}
console.log(x); // undefined
```
Isso torna o código mais limpo, resultando em menos variáveis soltas.

```js
function foo(bar) {
   if(bar) {
     let baz = bar;
     if(baz) {
          let bam = baz;
     }
     console.log(bam); // Error
   }
    console.log(baz); // Error
}
foo("bar");
```

Variáveis let podem ser reatribuídas
```js
let name = "Jerry Only";
name = "Glenn Danzig";
```

Mas não podem ser redeclaradas no mesmo escopo. Isso gera um TypeError

```js
let name = "Jerry Only";
let name = "Glenn Danzig";
```
Em um escopo diferente ela pode ser redeclarada
```js
let message = "web forum";

function printInCaps(value){
  return value.toUpperCase();
}

printInCaps("profiles");
console.log( message ); // web forum

```
Porque `message` dentro da função está presa naquele escopo com let, e o console enxerga somente a variável `message` global

## const
Uso do `const` para criar variáveis imutáveis

Constantes tem escopo por bloco, assim como variáveis definidas usando let

*declarações 'const' não causam `hoist`, por isso se torna necessário colocar todas suas declaraçòes const no topo dos blocos antes de serem usadas*

O valor de uma constante nã pode mudar através de reatribuíção, e não pode ser redeclarada.

Constantes sempre precisam ser declaradas, e atribuídas um valor:
```js
const MAX_USERS = 15; // Certo
const MAX_USERS; // errado
```

Existe outra maneira de declarar variáveis com escopo em bloco.

Com const você declara uma referência read-only para um valor. É preciso atribuir uma valor a variável diretamente.

```js
const myVar = 2;
myVar = 3; // 3
myVar // Ainda 2, e sempre será 2
```
