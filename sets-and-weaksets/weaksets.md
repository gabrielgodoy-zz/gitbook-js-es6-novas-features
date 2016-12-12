## Weaksets

More memory efficient type of Sets
The WeakSets is a type where only objects are allowed to be stored

**WeakSets are not iterable, and you cannot read values**

```js
let weakTags = new WeakSet();

weakTags.add("Javascript"); // Invalid, Only objects can be added to Weaksets
weakTags.add({name: "Javascript"});
let iOS = {name: "iOS"};
weakTags.add(iOS);
weakTags.has(iOS); // true
weakTags.delete(iOS); // true
```

### WeakSets use cases
We can use weakSets to create special groups from existing objects **without mutating them**. Favoring immutable objects allows for much simpler code with **no unexpected side efffetcs**.

Example of unecessary mutation on each post object without Weaksets
```js
let readPosts = new WeakSet();
postList.addEventListener('click', (event) => {
	// Mutates 'post' objets, crating a new property to indicate if it has been read
	post.isRead = true; 
});
// ... rendering posts
for(let post of postArray) {
	if(!post.isRead) { // Checks a property on each post
		_addClassToPost(post.element);
	}
}
```

Example using WeakSets without the need to mutate objects (create flag properties)
Creating group of objects and check for the presence of those objects on the weakset group
```js
let readPosts = new WeakSet();

postList.addEventListener('click', (event) => {
	readPosts.add(post); // Add objects to a group of read posts weakset
});

// ... rendering posts
for(let post of postArray) {
	if(!readPosts.has(post)) { // has() checks wether an object is present in the WeakSet
		_addClassToPost(post.element);
	}
}
```