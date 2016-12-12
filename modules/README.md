## Modules
When loaded via the module system, ES6 treats a file as a separate module. 

Each module can both import other modules or specific API members, as well export their own public API members.

There are two kinds of exports: 
**named exports* (several per module)
**default exports** (one per module).

Modules on ES6 are designed around the export and import keywords. 

ES6 modules must be defined in separate files (one per module). 
The browsers/engines have a default “module loader”, which synchronously loads a module file when it’s imported.


Let’s examine an example with two modules right away:
```js
///bar.js File
function hello(who) { 
	return `Let me introduce: ${who}`; 
}
export hello; 

//foo.js File
// import only `hello()` from the 'bar' module 
import hello from 'bar'; 
var hungry = 'hippo'; 
export function awesome() { 
	console.log(hello(hungry).toUpperCase()); 
}

// baz.js File
// import the entire 'foo' and 'bar' modules 
module foo from 'foo'; 
module bar from 'bar'; 
console.log( bar.hello( 'rhino' ) ); // Let me introduce: rhino 
foo.awesome(); // LET ME INTRODUCE: HIPPO
```

### Default Exports
**Modules that only export single values** are very popular in the Node.js community. 
But they are also common in frontend development where you often have constructors/classes for models, with one model per module. 

An ECMAScript 6 module can pick a default export, the most important exported value. 
Default exports are especially easy to import.

The following ECMAScript 6 module “is” a single function:
```js
//------ myFunc.js ------
export default function () { ... };
    
//------ main1.js ------
import myFunc from './myFunc';
myFunc();
```

An ECMAScript 6 module whose default export is a class looks as follows:
```js
//------ MyClass.js ------
export default class { ... };
    
//------ main2.js ------
import MyClass from 'MyClass';
let inst = new MyClass();
```

Note: The operand of the default export declaration is an expression, it often does not have a name. Instead, it is to be identified via its module’s name.

### Named Exports (Several per module)
A module can export multiple things by prefixing their declarations with the keyword export. These exports are distinguished by their names and are called **named exports**.

```js
//------ lib.js ------
export const sqrt = Math.sqrt;
export function square(x) {
   return x * x;
}
export function diag(x, y) {
   return sqrt(square(x) + square(y));
}
  
//------ main.js ------
import { square, diag } from 'lib';
console.log(square(11)); // 121
console.log(diag(4, 3)); // 5
```

There are other ways to specify named exports (which are explained later), but I find this one quite convenient: simply write your code as if there were no outside world, then label everything that you want to export with a keyword.

If you want to, you can also import the whole module and refer to its named exports via property notation:
```js
//------ main.js ------
import * as lib from 'lib';
console.log(lib.square(11)); // 121
console.log(lib.diag(4, 3)); // 5
```

#### Exporting multiple function at once with curly braces
You can also store something in a variable then export it. If you do that, you have to wrap the variable in a set of curly braces.

```js
function double(x) {
  return x + x;
}
function triple(x) {
  return x + x;
}
export { double, triple };

// A module can then import the double function like so:
import { double, triple } from 'filePath';
double(2); // 4
```
