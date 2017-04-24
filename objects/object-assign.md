# Object.assign (equivalent to .extend() in jQuery)
Escrever funções flexíveis e reutilizáveis

O método `Object.assign` copia as propriedades de um ou mais objetos de origem para um objeto de destino especificado como o primeiro argumento.

Object.assign (target, ... sources);

E se quisermos chamar countdownTimer com opções diferentes:

```js
// A função de exemplo countdownTimer precisa ser chamada de muitas maneiras diferentes
let btn = document.querySelector('.btn-undo');
// Simples assim
countdownTimer(btn, 60);

// e complicado como isso
countdownTimer(btn, 60, {
	container: '.new-post-options'
});
countdownTimer(btn, 3, {
	container: '.new-post-options',
	timeUnit: 'minutes',
	timeoutClass: '.time-is-up'
});
```

## Object.assign para o resgate
Queremos mergear 'options' passadas pela função que chamou a função countdownTimer, com 'defaults'.
Em propriedades duplicadas, as de 'options' devem substituir propriedades de 'defaults'.
Funciona como o método extend() jQuery.

```js
function countdownTimer(target, timeLeft, options = {}){
	let defaults = {
		container: '.timer-display',
		timeUnit: 'seconds',
		cloneDataAttribute: 'cloned',
		timeoutClass: '.is-timeout',
		timeoutSoonClass: '.is-timeout-soon',
		timeoutSoonTime: 10
	};
	
	// Isso cria um novo objeto inteiro com defaults e options mergeadas
	let settings = Object.assign({}, defaults, options);
}
```
