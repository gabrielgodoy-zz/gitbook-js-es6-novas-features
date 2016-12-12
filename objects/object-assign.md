# Object.assign (equivalent to .extend() in jQuery)
Writing flexible and reusable functions

The Object.assign method copies properties from one or more source objects to a target object specified as the very first argument.

Object.assign(target, ...sources);

What if we want to call countdownTimer with different options:
```js
// The example function countdownTimer needs to be called in many different ways
let btn = document.querySelector('.btn-undo');
// As simple as this
countdownTimer(btn, 60);

// and as complicated as this
countdownTimer(btn, 60, {
	container: '.new-post-options'
});
countdownTimer(btn, 3, {
	container: '.new-post-options',
	timeUnit: 'minutes',
	timeoutClass: '.time-is-up'
});
```

## Object.assign to the rescue
We want to merge 'options' passed by the caller of the function countdownTimer, with 'defaults'.
Upon duplicate properties, those from 'options' must override properties from 'defaults'.
Like the extend() jQuery method.
```js
function countdownTimer(target, timeLeft, options = {}){
	let defaults = {
		container: '.timer-display',
		timeUnit: 'seconds',
		cloneDataAttribute: 'cloned',
		timeoutClass: '.is-timeout',
		timeoutSoonClass: '.is-timeout-soon',
		timeoutSoonTime: 10
	};
	
	// This creates an entire new object with defaults and options merged
	let settings = Object.assign({}, defaults, options);
}
```
