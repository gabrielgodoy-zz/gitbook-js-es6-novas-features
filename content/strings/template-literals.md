## Template Literals
Template Literals fornecem uma maneira limpa para criar strings e executar interpolação strings.
Você já deve estar familiarizado com a sintaxe; 

É baseado no sinal do dólar e chaves $ {..}

Template Literals são incluídos com sinais de crase (`$ {}`)

Aqui está uma demonstração rápida:

```js
let name = 'John',
   apples = 5,
   pears = 7,
   bananas = function() { return 3; };

console.log(`This is ${name}.`);
console.log(`He carries ${apples} apples, ${pears} pears, and ${bananas()} bananas.`);

// Equivalente em ES5:
console.log('He carries ' + apples + ' apples, ' + pears + ' pears, and ' + bananas() +' bananas.');
```


No formulário acima, em comparação com o ES5, eles são apenas uma conveniência para concatenação strings. No entanto, template literals também podem ser usados para strings com várias linhas. Tenha em mente que o espaço em branco é parte da string:

```js
let x = `1...
2...
3 lines long!`; // Yay

// Equivalente em ES5:
var x = "1...\n" + 
"2...\n" +
"3 lines long!";

var x = "1...\n2...\n3 lines long!";
```
