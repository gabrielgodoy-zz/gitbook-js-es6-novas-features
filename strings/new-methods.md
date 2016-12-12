## String new methods

A couple of convenience methods have been added to the String prototype. Most of them basically eliminate some workarounds with the indexOf\(\) method to achieve the same:

```js
'my string'.startsWith('my'); //true
'my string'.endsWith('my'); // false
'my string'.includes('str'); // true
```

Another method has been added to create a repeating string:

```js
'my '.repeat(3); // 'my my my '
```



