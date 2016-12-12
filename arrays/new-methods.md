## New Array Methods

The Array object now has some new static class methods, as well as new methods on the Array prototype.

### Array.find

Array.find returns the first element in the array that satisfies a provided testing function

```js
// Find an admin in this array of users
let names = [{
    login: "Sam",
    admin: false
}, {
    login: "Brook",
    admin: true
}, {
    login: "Tyler",
    admin: true
}];

// Returns first object for which user.admin is true
let admin = users.find((user) => {
    return user.admin;
});

console.log(admin); //{login: "Brook", admin: true}
```

### Array.from

First, Array.from creates Array instances from array-like and iterable objects.   
Examples of array-like objects include:

* a nodeList returned by document.getElementsByTagName\(\);
* the new Map and Set data structures.

The items array has the forEach method, which isn’t available in the itemElements collection.

```js
let itemElements = document.querySelectorAll('.items');
let items = Array.from(itemElements);
items.forEach(function(element) {
    console.log(element.nodeType)
});

// A workaround often used in ES5:
let items = Array.prototype.slice.call(itemElements);
```

An interesting feature of Array.from is the second optional mapFunction argument. This allows you to create a new mapped array in a single invocation:

```js
let navElements = document.querySelectorAll('nav li'),
    navTitles = Array.from(navElements, el => el.textContent);
```

### Array.of

Array.of behaves much like the Array constructor. It fixes the special case when passing it a single number argument. This results in Array.of being preferable to new Array\(\). However, in most cases, you’ll want to use array literals.

```js
let x = new Array(3); // [undefined, undefined, undefined]
let y = Array.of(8); // [8]
let z = [1, 2, 3]; // Array literal
```

Last but not least, a couple of methods have been added to the Array prototype.  
I think the find methods will be very welcome to most JavaScript developers.

**find** returns the first element for which the callback returns true.  
**findIndex** returns the index of the first element for which the callback returns true.  
**fill** “overwrites” the elements of an array with the given argument.

```js
[5, 1, 10, 8].find(n => n === 10) // 10

[5, 1, 10, 8].findIndex(n => n === 10) // 2

[0, 0, 0].fill(7) // [7, 7, 7]
[0, 0, 0, 0, 0].fill(7, 1, 3) // [0, 7, 7, 7, 0]
```



