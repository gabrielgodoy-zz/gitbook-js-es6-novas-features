## Maps
Maps are a data structure composed of a collection of **key/value** pairs. 
Maps are useful to store simple data, such as property values.

The **set** method is used to add entries, and the **get** method to read entries

### Issues with using objects as maps
When using Objects as keys, **its keys are always converted to strings**

```js
// Two different objects
let user1 = {name: "Sam"},
	user2 = {name: "Tyler"};
	
let totalReplies = {};

// Both objects below are converted to the string '[object Object]'
totalReplies[user1] = 5;
totalReplies[user2] = 42;

console.log(totalReplies[user1]); // 42
console.log(totalReplies[user2]); // 42
console.log(Object.keys(totalReplies)); // ['[object Object]']
```

Map fixes that:
When we use objects as keys on a map they are not converted to strings

```js
let user1 = {name: "Sam"},
 	user2 = {name: "Tyler"};

let totalReplies = new Map();
// These two values are properly assigned to different keys
totalReplies.set(user1, 5);
totalReplies.set(user2, 42);

// We use the get() and set() methods to access values in Maps)
console.log(totalReplies.get(user1)); // 5
console.log(totalReplies.get(user2)); // 42
```

### When to use maps or objects to store data
Use Maps when keys are unknown until runtime

*Keys unknown until runtime, so...Map!*
```js
let recentPosts = new Map();
createPost(newPost, (data) => {
	// We dont know what data.author is going to be until you run this code
	recentPosts.set(data.author, data.message)
});
```

*Keys are previously defined, so...Objects!*
```js
const POSTS_PER_PAGE = 15;
let userSettings = {
	perPage: POSTS_PER_PAGE,
	showRead: true
}
```

### Iterating Maps with for...of
```js
let mapSettings = new Map();

mapSettings.set("user", "Sam");
mapSettings.set("topic", "ES2015");
mapSettings.set("replies", ["Can't wait!", "So Cool"]);

for(let [key, value] of mapSettings) {
	console.log(`${key} = ${value}`);
}
```