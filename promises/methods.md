## Promise methods
### Promise.all(iterable)
Returns a promise that resolves when all of the promises in the iterable argument have resolved. This is useful for aggregating results of multiple promises together.

### Promise.race(iterable)
Returns a promise that resolves or rejects as soon as one of the promises in the iterable resolves or rejects, with the value or reason from that promise.

### Promise.reject(reason)
Returns a Promise object that is rejected with the given reason.

### Promise.resolve(value)
Returns a Promise object that is resolved with the given value. If the value is a thenable (i.e. has a then method), the returned promise will "follow" that thenable, adopting its eventual state; otherwise the returned promise will be fulfilled with the value. Generally, if you want to know if a value is a promise or not - Promise.resolve(value) it instead and work with the return value as a promise.

