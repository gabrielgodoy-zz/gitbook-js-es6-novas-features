## Módulos
Quando carregado através do sistema do módulo, o ES6 trata um arquivo como um módulo separado.

Cada módulo pode importar outros módulos ou membros específicos da API, assim como exportar seus próprios membros públicos da API.

Existem dois tipos de exportações:
- **named exports** (várias por módulo)
- **exportações default** (uma por módulo)

Os módulos no ES6 são projetados em torno das palavras-chave `export` e` import`

Os módulos ES6 devem ser definidos em arquivos separados (um por módulo).

Os navegadores/motores têm um "carregador de módulo" padrão, que carrega de forma síncrona um arquivo de módulo quando é importado.

Vamos examinar um exemplo com dois módulos:

```js
// bar.js
function hello(who) { 
	return `DEIXE-ME APRESENTAR: ${who}`; 
}
export hello; 

// foo.js 
// importa somente `hello()` do módulo 'bar'
import hello from 'bar'; 
var hungry = 'hippo'; 
export function awesome() { 
	console.log(hello(hungry).toUpperCase()); 
}

// baz.js
// Importa todos os módulos 'foo' e 'bar' 
module foo from 'foo'; 
module bar from 'bar'; 
console.log( bar.hello( 'rhino' ) ); // Deixe-me introduzir: rhino
foo.awesome(); // DEIXE-ME APRESENTAR: HIPPO
```

### Default Exports
**Módulos que exportam valores únicos** são muito populares na comunidade Node.js.

Mas eles também são comuns no desenvolvimento de frontend onde muitas vezes você tem construtores/classes para modelos, com um modelo por módulo.

Um módulo ES6 pode escolher `export default`, o valor exportado mais importante.

`Default export` são especialmente fáceis de importar.

O seguinte módulo ECMAScript 6 "é" uma única função:

```js
//------ myFunc.js ------
export default function () {...};
    
//------ main1.js ------
import myFunc from './myFunc';
myFunc();
```

Um módulo ECMAScript 6 que seu `export default` é uma classe parece da seguinte maneira:

```js
//------ MyClass.js ------
export default class { ... };
    
//------ main2.js ------
import MyClass from 'MyClass';
let inst = new MyClass();
```

Nota: O operando da declaração de `export default` é uma expressão, muitas vezes não tem um nome. Em vez disso, ele deve ser identificado **através do nome do seu módulo**.

### Named Exports (várias por módulo)
Um módulo pode exportar várias coisas, prefixando suas declarações com a palavra-chave `export`.

Essas exportações são distinguidas por seus nomes e são chamadas **named exports**.

```js
//------ lib.js ------
export const sqrt = Math.sqrt;
export function square(x) {
   return x * x;
}
export function diag(x, y) {
   return sqrt(square(x) + square(y));
}
  
//------ main.js ------
import { square, diag } from 'lib';
console.log(square(11)); // 121
console.log(diag(4, 3)); // 5
```

Também é possível importar todo o módulo e referir-se às suas exportações nomeadas através da notação de propriedade:

```js
//------ main.js ------
import * as lib from 'lib';
console.log(lib.square(11)); // 121
console.log(lib.diag(4, 3)); // 5
```

#### Exportação de múltiplas funções de uma só vez com chaves
Também é possível armazenar algo em uma variável, e em seguida, exportá-lo

```js
function double(x) {
  return x + x;
}
function triple(x) {
  return x + x;
}
export { double, triple };

// A module can then import the double function like so:
import { double, triple } from 'filePath';
double(2); // 4
```