# Iterator
An object is an iterator when it knows how to access items from a collection one at a time, while keeping track of its current position within that sequence.

In JavaScript an iterator is an object that provides a next() method which returns the next item in the sequence. 

This method returns an object with two properties: done and value.

```js
// Example of a custom Iterator Creator
function makeCustomIterator (array) {
    let nextIndex = 0;
    return {
        next() {
            return nextIndex < array.length ? { value: array[nextIndex++], done: false } : { done: true };
        }
    }
}

/*
 makeIteratorFunc holds an object with the next method in it
 */
let makeIteratorFunc = makeCustomIterator(["Gabriel", "Godoy"]);

console.log('Custom Iterator: ', makeIteratorFunc.next()); // { value: 'Gabriel', done: false }
console.log('Custom Iterator: ', makeIteratorFunc.next()); // { value: 'Godoy', done: false }
console.log('Custom Iterator: ', makeIteratorFunc.next().done); // true
```

Custom iterators like makeCustomIterator requires the management of the internal state of the iterator. Generators are "iterators factories", where the keyword yield sets the point in which the function will stop when the next next() method is called

The same result of makeCustomIterator function could be achieved with a generator without having to manually manage the state of the iterator, and what should be returned.


## Iterables
An object is iterable if it defines its iteration behavior, such as what values are looped over in a for..of construct.

In order to be iterable, an object must implement the @@iterator method, the object (or one of the objects up its prototype chain) must have a property with a Symbol.iterator key

Built-in iterables

String, Array, TypedArray, Map and Set are all built-in iterables, because the prototype objects of them all have a Symbol.iterator method
```js
function runIterable (iterable) {
    for (let element of iterable) {
        console.log('Iterable element: ', element);
    }
}

runIterable(['Gabriel', 'Godoy']);
// Iterable element:  Gabriel
// Iterable element:  Godoy

runIterable('Gabriel');
// Iterable element:  G
// Iterable element:  a
// Iterable element:  b
// Iterable element:  r
// Iterable element:  i
// Iterable element:  e
// Iterable element:  l
```

### Custom Iterable

This literal object below natively neither have nor inherit Symbol.iterator property. But we can make this one Iterable by addin [Symbol.iterator] property to it.

```js
let myIterable = {};

// Add Symbol.iterator to it
myIterable[Symbol.iterator] = function* () {
    yield 1;
    yield 2;
    yield 3;
};

// And now it becomes iterable
for(let value of myIterable){
    console.log(value);
}
// 1
// 2
// 3
```

