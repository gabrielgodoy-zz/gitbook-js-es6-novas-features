## Spread Operators
O operador spread `...` é uma sintaxe para expandir elementos de um array em locais específicos, como argumentos em chamadas de função.

**Diferença entre operador Rest e Spread**
 
Parâmetros Rest são usados em definições de função, e o operador Spread é usado em chamadas de função

### Em Arrays
Expande elementos de um array dentro de outro array:

```js
let values = [1, 2, 4],
	some = [...values, 8], // [1, 2, 4, 8]
	more = [...values, 8, ...values]; // [1, 2, 4, 8, 1, 2, 4]

// Old JS
let values = [1, 2, 4];
// Iterate, push, sweat, repeat...
// Iterate, push, sweat, repeat...
```

### Em chamadas de funções
A sintaxe Spread também é poderoso ao chamar funções com argumentos:

```js
let values = [1, 2, 4];

doSomething(...values); // Mesma coisa que doSomething(values[0], values[1], values[2])
```

A sintaxe é muito flexível, porque o operador Spread pode ser usado em qualquer lugar na lista de argumentos.

Isso significa que a seguinte invocação produz o mesmo resultado:

```js
let values = [2, 4];
doSomething(1, ...values);  // Mesma coisa que doSomething(1, values[0], values[1])
```

### Em iterables
Ele pode ser aplicado a todos os objetos iteráveis, como um NodeList:
```js
let form = document.querySelector('#my-form'),
	inputs = form.querySelectorAll('input'),
	selects = form.querySelectorAll('select');

let allElements = [form, ...inputs, ...selects];
// Agora, allElements é um array flat contendo o `<form>` node e seu `<input \>` e `<select>` child nodes.
```

### Em Objetos
Permite usar o operador spread `...` para copiar propriedades enumeráveis de um objeto para outro, ou substituí-las

```js
let state = {someProp: '', visibilityFilter: false};
function mergeObjects(state) {
	return { ...state, visibilityFilter: true }
}
```

### Copiando Objetos ou Array que possuem outros Objetos ou array aninhados

> É importante notar que o operador spread só faz uma cópia "rasa" do objeto ou array. Portanto se dentro desse array ou objeto tiver mais um array ou objeto aninhado, este vai permanecer com a mesma referência do objeto ou array original.

Por exemplo:

```js
const originalArray = [
    {
      "person": {
        name: "Gabriel"
      }
    }
];

const newCopy = [...originalArray];
newCopy[0].person.name = "Rodrigo";
console.log(originalArray[0].person.name) // Rodrigo
```
