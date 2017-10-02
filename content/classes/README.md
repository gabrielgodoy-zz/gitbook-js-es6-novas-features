## Classes
A sintaxe de classe no JS é somente "cosmética". Por baixo dos panos, o JS continua trabalhando com prototype e não com herança de classes.

Essa sintaxe de classe facilita a adoção da linguagem por novatos e desenvolvedores que vem de outras linguagens.

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

Note que a definição de classe não é um objeto literal normal. Por isso, não existem vírgulas entre membros da classe.

O método construtor é um método especial para criar e inicializar um objeto que será uma instância dessa classe. Possuindo propriedades pré-definidas.

Para criar uma instância da classe, **é preciso usar o termo `new`**

 ```js
let myCar = new Car('bumpy');
```


### Criando uma subclasse
Para herdar de uma outra classe, use **extends**:

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

Através das subclasses, é possível utilizar o termo **super()** dentro do construtor ou de métodos para acessar a classe pai.

O termo **super()** precisa ser a primeira coisa declarada dentro do construtor da subclasse.

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

## Métodos estáticos

Métodos estáticos pertencem a classe, mas não as instâncias dessa classe.

Métodos estáticos servem como funções utilitárias de uma determinada classe, que não pertencem a suas instâncias. É um método geral.

```js
class Article {
  constructor(title, date) {
    this.title = title;
    this.date = date;
  }

  static compare(articleA, articleB) {
    return articleA.date - articleB.date;
  }
}

// usage
let articles = [
  new Article("Mind", new Date(2016, 1, 1)),
  new Article("Body", new Date(2016, 0, 1)),
  new Article("JavaScript", new Date(2016, 11, 1))
];

articles.sort(Article.compare);

alert( articles[0].title ); // Body
```