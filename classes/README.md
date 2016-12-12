## Classes
Classes are a well-debated feature of ES6. Some believe that they go against the prototypal nature of JavaScript, while others think they lower the barrier to entry for beginners and people coming from other languages and that they help people writing large-scale applications. In any case, they are part of ES6. Here’s a very quick introduction.
 
Classes are built around the class and constructor keywords
```js
class Vehicle {
       // constructor runs everytime a new instance is create with 'new'
   	constructor(name){ 
  		this.name = name;
  		this.kind = 'vehicle';
   	}
   	getName() {
  		return this.name;
   	},
   	// Prefixing with underscore. Convention for private
   	_privateMethod() { 
  		//...
   }
}

// Create an instance
let myVehicle = new Vehicle('rocky');
```

Note that the class definition is not a regular object. Hence, there are no commas between class members.


The constructor method is a special method for creating and intializing an object

To create an instance of a class, **you must use the new keyword**.
 
 ```js
let myCar = new Car('bumpy');
```

### Creating a subclass
To inherit from a base class, use **extends**:

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

From the derived class, you can use super from any constructor or method to access its base class:

To call the parent constructor, use **super()**

To call another member, use, for example, **super.getName()**

Example of subclass:
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
