## Async Functions and await operator
Async function can contain await expression, that pauses the execution of the async function and waits for the passed promise's resolution, and resumes the async function's execution and returns the resolved value.

```js
// Some function that returns a Promise
function getPromise() {
    return new Promise((resolve, reject) => {
        (Math.random() > .5) ? resolve('You are lucky!') : reject('Bad Luck :(');
    });
}

/*
async function
async/await let you write asynchronous code, using synchronous code structure
*/
async function main() {
    let result;
    // await receives a Promise, if rejected goes to catch block with respective error
    try {
        result = await getPromise();
    } catch (error) {
        result = `Error: ${error}`;
    }
    console.log(result);
}

// Run async function
main();
```
