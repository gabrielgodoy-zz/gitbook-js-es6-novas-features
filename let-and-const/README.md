## let
A new way to create scope

Using **var = variable** Its scope is trapped in the nearest surrounding function 
Using **let = variable** Its scoped is trapped in the nearest curly braces

*'let' statement does not hoist, that is why you need to put all your let statements on top of the blocks*

```js
if(true) {
   let x = 1;
}
console.log(x); // undefined
```

This can make for cleaner code, resulting in fewer variables hanging around. 

```js
function foo(bar) {
   if(bar) {
     let baz = bar;
     if(baz) {
          let bam = baz;
     }
     console.log(bam); // Error
   }
    console.log(baz) // Error
}
foo("bar");
```

let variables can be reassigned
```js
let name = "Jerry Only";
name = "Glenn Danzig";
```

but not redeclared on the same scope. This gives a typeError
```js
let name = "Jerry Only";
let name = "Glenn Danzig";
```

In different scope it can be redeclared
```js
let message = "web forum";


function printInCaps(value){
  let message = value.toUpperCase();
  return message;
}


printInCaps("profiles");
console.log( message ); // web forum

// Because message inside function is trapped with let, and console sees only the global message
```

## const
Use of Const to create immutable Variables
Constants are block-scoped, much like variables defined using the let statement. 
The value of a constant cannot change through re-assignment, and it can't be redeclared.

Constants always needs to be assigned:

```js
const MAX_USERS = 15; // Right

const MAX_USERS; // Wrong
```

There is another way to declare block-scoped variables. With const, you declare a read-only reference to a value. You must assign a variable directly. 

```js
const myVar = 2;
myVar = 3;
// 3
myVar
// 2, and will always be two
```

