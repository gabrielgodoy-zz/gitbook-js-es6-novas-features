## Named Parameters
Using named parameters for optional settings makes it easier to understand how a function should be invoked.

```js
function setPageThread(name, { popular, expires, activeClass } = {}) {
   // ...
}
```
and to call. If you omit one of those object properties, they will only be undefined.

```js
setPageThread("New Version", { 
   popular: true, 
   expires: 10000, 
   activeClass: "is-page-thread" 
});
```

