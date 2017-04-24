## Classes
Classes em JS é um assunto muito debatido. Alguns acreditam que o conceito de classes vai contra a natureza prototipal do Javascript, enquanto outro acreditam que ter o conceito de classe facilita a adoção da linguagem por novatos e desenvolvedores de outras linguagens, e que a utilização de classes facilita a criação de aplicações escaláveis. 

Classes são construídas ao redor de classes e construtores.

```js
class Vehicle {
  // O contrutor roda toda vez que uma nova instância é criada com 'new'
   	constructor(name){ 
  		this.name = name;
  		this.kind = 'vehicle';
   	}
   	getName() {
  		return this.name;
   	},
   	// Utilizar a convenção de prefixo com underline para métodos privados
   	_privateMethod() { 
  		//...
   }
}

// Create an instance
let myVehicle = new Vehicle('rocky');
```

Note que a definição de classe não é um objeto normal. Por isso, nào existem vírgulas entre membros da classe.

O método construtor é um método especial para criar e inicializar um objeto.

Para criar uma instância de uma classe, **é preciso usar o termo new**
 
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

Através das subclasses, é possível utilizar o termo **super()** dentro do construtor ou métodos para acessar a classe base:

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
