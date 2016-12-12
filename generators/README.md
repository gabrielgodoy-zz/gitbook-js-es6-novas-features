## Generators
A Generator manages its own iterative state, they are 'pausable' functions.

A function becomes a generator if it contains one or more **yield** expressions and if it uses the `function*` syntax.

### The `next()` method of a Generator
The `next()` lets you iterate your generator.

When you assign a variable that store your generator function like:

`const ajaxGenSetup = ajaxGen();`

You have as many `next()` methods to use as the number of yields present in the generator function, until `done = true`

The `next()` method returns an object with two properties, **done** and **value**.
`{ value: 3, done: false }`

Each yield keyword is a stop point for a `next()` method

On the function below, when there are no more yields left to stop, the generator returns the property done as `true`

```js
let myGenerator = function*() {
    yield 1;
    yield 2;
    yield 3;
};

// Store and setup myGenerator
let gen = myGenerator();

// The next method returns what it is programmed to be yielded on the function
console.log(gen.next()); // { value: 1, done: false } 
console.log(gen.next()); // { value: 2, done: false } 
console.log(gen.next()); // { value: 3, done: false }
console.log(gen.next()); // { value: undefined, done: true } 
```

### Sending values to the Generator via `next()` method
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

The yield "foo" expression will send the "foo" string value out when pausing the generator function at that point, and whenever the generator is restarted with another `next()` function, whatever value is sent in, will be the result of that yield expression, which will then get added to 1 and assigned to the x variable.

**It's almost as if the yield keyword is pausing and sort of making an external request for a value. Waiting for the next `next()` with a value in it**

The value passed on the `next()` method kind of 'replaces' the entire yield expression that was last paused on.

### Generators for Async actions
We can set a specific order for asynchronous request to run with generators.

Got this example in a [very good ES6 course of a friend of mine](http://willianjusten.teachable.com/p/js-com-tdd-na-pratica). The course is in portuguese.

```js
function ajax(url) {
	fetch(url)
		.then(data => data.json())
		// This function calls the next yield inside ajaxGen with the fetched data as argument
		.then(data => ajaxGenSetup.next(data));
}

// Asynchronous code that seems like it is synchronous
function* ajaxGen() {
	console.log('Searching posts...');
	const posts = yield ajax('https://willianjusten.com.br/search.json');
	console.log(posts);
	console.log('Searching data from Github...');
	const github = yield ajax('https://api.github.com/users/willianjusten');
	console.log(github);
	console.log('Searching data from Github 2...');
	const github2 = yield ajax('https://api.github.com/users/willianjusten');
	console.log(github2);
}

// Gets the generator and all next() methods according to the number of yields in it
const ajaxGenSetup = ajaxGen();

// This first next() triggers the generator and stop on the first yield 
// Has value of undefined, because there was no 'yield' initially 'waiting' for a value
ajaxGenSetup.next(); // {value: undefined, done: false}

// Searching posts...
// Ajax Data
// Searching data from Github...
// Ajax Data
// Searching data from Github 2...
// Ajax Data
```