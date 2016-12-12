## Generators
A Generator maintain its own iterative state. Each yield keyword is a stop point for the next() method. 

A function becomes a generator if it contains one or more 'yield' expressions and if it uses the `function*` syntax.

On the function below, when the array passed to the function finishes its iteration, there are no more yields left, so the generator return the property done as 'true'

```js
function* generatorForCustomIterator (array) {
    let nextIndex = 0;
    while (nextIndex < array.length) {
        yield array[nextIndex++];
    }
}

let myGenerator = generatorForCustomIterator(["Gabriel", "Godoy"]);

console.log('Generator: ', myGenerator.next()); // { value: 'Gabriel', done: false } 
console.log('Generator: ', myGenerator.next()); // { value: 'Godoy', done: false } 
console.log('Generator: ', myGenerator.next().done); // true
```

### Generators for Async actions
We can set a specific order for asynchronous request to run with generators.

Got this example in a [very good ES6 course of a friend of mine](http://willianjusten.teachable.com/p/js-com-tdd-na-pratica). The course is in portuguese.

```js
function ajax(url) {
	fetch(url)
		.then(data => data.json())
		.then(data => dados.next(data));
}

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
const dados = ajaxGen();
dados.next();
```

### Advanced Generators
The next() method also accepts a value which can be used to modify the internal state of the generator. 

A value passed to next() will be treated as the result of the last yield expression that paused the generator.

```js
function* customGenerator() {
    let receiveValueFromNextMethod = yield "batata";
    console.log('Value from next(): ', receiveValueFromNextMethod);
}

let storeCustomGenerator = customGenerator();
// The first call did not log anything, because the generator 
// was not yielding anything initially

storeCustomGenerator.next(); // First next stops on the first yield
storeCustomGenerator.next(10); // Value from next():  10
```
