## Promises Objects

The Promise object is used for deferred (to delay, to retard) and asynchronous computations. 

A Promise represents an operation that hasn't completed yet, but is expected in the future.

Creating a new Promise automatically sets it to the **pending state**.

### Promises States
Internally, a promise can be in one of three states:
- **Pending**, when the final value is not available yet
- **Fulfilled**, when and if the final value becomes available. A fulfillment value becomes permanently associated with the promise. This may be any value, including undefined.
- **Rejected**, if an error prevented the final value from being determined. This may be any value, including undefined, though it is generally an Error object, like in exception handling.

### Creating Promises
The Promise Constructor function takes an anonymous function with 2 arguments known as handlers (resolve, reject)
```js
let randomPromise = () => new Promise((resolve, reject) => (Math.random() > .5) ? resolve('ok') : reject('fail'));
```

Now using the created Promise
The second parameter on the then function acts as a catch block when things go wrong.
```js
randomPromise().then(result => console.log(result), err => console.log(err));
```

### then() and catch()
Promise.prototype.then and Promise.prototype.catch methods return promises, they can be chained

### catch() block to treat exceptions and errors
```js
Promise.resolve('oops, this is not a json to be parsed')
  .then(data => JSON.parse(data)) // Try to parse a non-JSON data send us to catch block
  .catch(error => alert(`Error: ${error.message}`)); // Error is alerted
```

### Promise Chaining
The method then() returns a promise, so can be chained again on another then()
```js
someFunction.somePromiseReturned()
  .then(getFiles)
  .then(generateIndex)
  .then(generatePosts);
```

### Using Promises for Ajax Requests (Promisifying XMLHttpRequest)
```js
function get(url) {
  return new Promise(function(resolve, reject) {
    // Do the usual XHR stuff
    let req = new XMLHttpRequest();
    req.open('GET', url);

    req.onload = function() {
      // This is called even on 404, so check the status
      if (req.status == 200) {
        // Resolve the promise with the response text
        resolve(req.response);
      }
      else {
        // Otherwise reject with the status text
        reject(Error(req.statusText));
      }
    };

    // Handle network errors
    req.onerror = function() {
      reject(Error("Network Error"));
    };

    // Make the request
    req.send();
  });
}

// Use the promisified XHR
get('story.json').then(function(response) {
  console.log("Success!", response);
}, function(error) {
  console.error("Failed!", error);
});

```

