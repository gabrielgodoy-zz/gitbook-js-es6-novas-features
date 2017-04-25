## Classes
Classes em JS é um assunto muito debatido. Alguns acreditam que o conceito de classes vai contra a natureza prototipal do Javascript, enquanto outro acreditam que ter o conceito de classe facilita a adoção da linguagem por novatos e desenvolvedores de outras linguagens, e que a utilização de classes facilita a criação de aplicações escaláveis. 

```js
class Vehicle {
  	// O construtor roda toda vez que uma nova instância é criada com "new"
	constructor(name){ 
		this.name = name;
		this.kind = 'vehicle';
	}

	getName() {
		return this.name;
	}

	// Utilizar a convenção de prefixo com underline para métodos privados
	_privateMethod() { 
		//...
	}
}

// Cria uma instância
let myVehicle = new Vehicle('rocky');
```

Note que a definição de classe não é um objeto normal. Por isso, não existem vírgulas entre membros da classe.

O método construtor é um método especial para criar e inicializar um objeto com propriedades pré-definidas.

Para criar uma instância de uma classe, **é preciso usar o termo `new`**
 
 ```js
let myCar = new Car('bumpy');
```

### Criando uma subclasse
Para herdar de uma classe base, use **extends**:
```js
class Car extends Vehicle {
	constructor(name) {
  		super(name);
  		this.kind = 'car'
	}
}

let myCar = new Car('bumpy');
myCar.getName(); // 'bumpy'
myCar instanceof Car; // true
```

Através das subclasses, é possível utilizar o termo **super()** dentro do construtor ou métodos para acessar a classe pai:

Para chamar um outro membro, use, por exemplo **super.getName()**

Exemplo de subclasse:
```js
class Animal {
	constructor(voice) {
		this.voice = voice || 'grunt';
	}
	speak() {
		display(this.voice);
	}
}

class Cat extends Animal {
	constructor(name, color) {
		super('Meow');
		this.name = name;
		this.color = color;
	}
}

let fluffy = new Cat('Fluffy', 'White');
display(Object.keys(fluffly.__proto__.__proto__)); // Array
display(fluffy.__proto__.__proto__.hasOwnProperty('speak')); // true
```
