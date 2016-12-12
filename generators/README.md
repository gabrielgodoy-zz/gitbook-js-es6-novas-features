## Generators
A Generator maintain its own iterative state. Each yield keyword is a stop point for the next() method. A function becomes a generator if it contains one or more 'yield' expressions and if it uses the function* syntax.

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

### Advanced Generators
The next() method also accepts a value which can be used to modify the internal state of the generator. A value passed to next() will be treated as the result of the last yield expression that paused the generator.

```js
function* customGenerator() {
    let receiveValueFromNextMethod = yield null;
    console.log('Value from next(): ', receiveValueFromNextMethod);
}

let storeCustomGenerator = customGenerator();
// The first call did not log anything, because the generator 
// was not yielding anything initially
storeCustomGenerator.next();
storeCustomGenerator.next(10); // Value from next():  10
```
