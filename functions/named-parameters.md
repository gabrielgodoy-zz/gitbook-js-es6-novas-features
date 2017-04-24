## Named Parameters
Utilizando parâmetros nomeados para configurações opcionais torna mais fácil de entender como uma função deve ser invocada. 

```js
function setPageThread(name, { popular, expires, activeClass } = {}) {
   // ...
}
```

e para chamar. Se você omitir uma dessas propriedade do objeto, elas somente serão `undefined`

```js
setPageThread("New Version", { 
   popular: true, 
   expires: 10000, 
   activeClass: "is-page-thread" 
});
```
