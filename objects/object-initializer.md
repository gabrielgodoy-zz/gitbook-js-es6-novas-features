## Object Initializer
Only works if the variable have the same names as the keys of the object being initialized
```js
// Old JS
let name = "Brook";
let totalReplies = 249;
let avatar = "/users/avatars/brook-user-1.jpg";
let user = {name: name, totalReplies: totalReplies, avatar: avatar};

// ES6
let name = "Brook";
let totalReplies = 249;
let avatar = "/users/avatars/brook-user-1.jpg";
let user = {name, totalReplies, avatar};

// Shorthand property names (ES6)
let a = "foo", 
    b = 42, 
    c = {};

let o = { a, b, c };

// Shorthand method names (ES6)
let o = {
  property([parameters]) {},
  get property() {},
  set property(value) {},
  * generator() {}
};

// Computed property names (ES6)
let prop = "foo";
let o = {
  [prop]: "hey",
  ["b" + "ar"]: "there",
};

```
