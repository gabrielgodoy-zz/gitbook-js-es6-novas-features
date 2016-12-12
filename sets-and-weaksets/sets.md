## Sets
The **Set** Object stores unique values of any type, wheter primitives or object references

Problems with arrays
In arrays, duplicate entries are allowed, like below:

```js
let tags = [];


tags.push("Javascript");
tags.push("Programming");
tags.push("Web");
tags.push("Web"); // Duplicate entry


console.log("Total items: ", tags.length); // 4
```

Sets prevent duplicate entries
We use the add() method to add elements to a Set

```js
let tags = new Set();
tags.add("Javascript");
tags.add("Programming");
tags.add({version: "2015"}); // Primitive values and objects are allowed
tags.add("Web");
tags.add("Web"); // Duplicate entries are ignored

console.log('Total items: ', tags.size); // 4, the second "Web" was ignored
```

**Set objects are iterable. We can use them with for...of and destructuring**

```js
let tags = new Set();
tags.add("Javascript");
tags.add("Programming");
tags.add({version: "2015"});
tags.add("Web");

for(let tag of tags) {
	console.log(tag);
}

// Destructure assignment allowed on Sets
let [a, b, c, d] = tags;
console.log(a, b, c, d);
```
