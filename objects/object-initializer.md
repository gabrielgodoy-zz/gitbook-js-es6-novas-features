## Object Initializer
Only works if the variable have the same names as the keys of the object being initialized

```js
// Old JS
var name = "Brook",
	totalReplies = 249,
	avatar = "/users/avatars/brook-user-1.jpg",
	user = {name: name, totalReplies: totalReplies, avatar: avatar};

// ES6
let name = "Brook",
	totalReplies = 249,
	avatar = "/users/avatars/brook-user-1.jpg",
	user = {name, totalReplies, avatar};
```

### Shorthand Object property names (ES6)
```js
// Old JS
var a = "foo", 
    b = 42,
    c = {},
	obj = {a: a, b: b, c: c};

// ES6
let a = "foo", 
    b = 42, 
    c = {},
	obj = {a, b, c};
```

### Computed property names (ES6)
This feature lets you set dynamic key names of a literal object

```js
let prop = "foo",
	obj = {
	  [prop]: "hey",
	  ["b" + "ar"]: "there",
	};
```
