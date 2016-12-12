## Proxy
**TODO:** Needs more study and personal elaboration 
For now is almost copy paste from [MDN docs](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Proxy):

The Proxy object is used to define custom behavior for fundamental operations (e.g. property lookup, assignment, enumeration, function invocation, etc).

**handler**
Placeholder object which contains traps.

**traps**
The methods that provide property access. This is analogous to the concept of traps in operating systems.

**target**
Object which the proxy virtualizes. It is often used as storage backend for the proxy. Invariants (semantics that remain unchanged) regarding object non-extensibility or non-configurable properties are verified against the target.


```js
let p = new Proxy(target, handler);
```

**target**
A target object (can be any sort of objects, including a native array, a function or even another proxy) or function to wrap with Proxy.

**handler**
An object whose properties are functions which define the behavior of the proxy when an operation is performed on it.


#### Basic Example
In this simple example the number 37 gets returned as the default value when the property name is not in the object. It is using the get handler.
```js
let handler = {
    get: function(target, name){
        return name in target?
            target[name] :
            37;
    }
};

let p = new Proxy({}, handler);
p.a = 1;
p.b = undefined;

console.log(p.a, p.b); // 1, undefined
console.log('c' in p, p.c); // false, 37
```

#### No-op forwarding proxy
In this example, we are using a native JavaScript object to which our proxy will forward all operations that are applied to it.
```js
let target = {},
	p = new Proxy(target, {});

p.a = 37; // operation forwarded to the target

console.log(target.a); // 37. The operation has been properly forwarded
```

#### Validation
With a Proxy, you can easily validate the passed value for an object. This example uses the set handler.
```js
let validator = {
  set: function(obj, prop, value) {
    if (prop === 'age') {
      if (!Number.isInteger(value)) {
        throw new TypeError('The age is not an integer');
      }
      if (value > 200) {
        throw new RangeError('The age seems invalid');
      }
    }

    // The default behavior to store the value
    obj[prop] = value;

    // Indicate success
    return true;
  }
};

let person = new Proxy({}, validator);

person.age = 100;
console.log(person.age); // 100
person.age = 'young'; // Throws an exception
person.age = 300; // Throws an exceptio
```

#### Extending constructor
A function proxy could easily extend a constructor with a new constructor. This example uses the construct and apply handlers.

```js
function extend(sup,base) {
  let descriptor = Object.getOwnPropertyDescriptor(
    base.prototype,"constructor"
  );
  base.prototype = Object.create(sup.prototype);
  let handler = {
    construct: function(target, args) {
      let obj = Object.create(base.prototype);
      this.apply(target,obj,args);
      return obj;
    },
    apply: function(target, that, args) {
      sup.apply(that,args);
      base.apply(that,args);
    }
  };
  let proxy = new Proxy(base,handler);
  descriptor.value = proxy;
  Object.defineProperty(base.prototype, "constructor", descriptor);
  return proxy;
}

let Person = function(name){
  this.name = name;
};

let Boy = extend(Person, function(name, age) {
  this.age = age;
});

Boy.prototype.sex = "M";

let Peter = new Boy("Peter", 13);
console.log(Peter.sex);  // "M"
console.log(Peter.name); // "Peter"
console.log(Peter.age);  // 13
```

#### Manipulating DOM nodes
Sometimes you want to toggle the attribute or class name of two different elements. Here's how using the set handler.

```js
let view = new Proxy({
  selected: null
},
{
  set: function(obj, prop, newval) {
    let oldval = obj[prop];

    if (prop === 'selected') {
      if (oldval) {
        oldval.setAttribute('aria-selected', 'false');
      }
      if (newval) {
        newval.setAttribute('aria-selected', 'true');
      }
    }

    // The default behavior to store the value
    obj[prop] = newval;

    // Indicate success
    return true;
  }
});

let i1 = view.selected = document.getElementById('item-1');
console.log(i1.getAttribute('aria-selected')); // 'true'

let i2 = view.selected = document.getElementById('item-2');
console.log(i1.getAttribute('aria-selected')); // 'fal
```

