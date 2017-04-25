## Novos métodos de String

Um par de métodos convenientes foram adicionados ao protótipo String.

A maioria deles basicamente eliminam algumas soluções alternativas com o método `indexOf\(\)` para obter o mesmo:

```js
'my string'.startsWith('my'); //true
'my string'.endsWith('my'); // false
'my string'.includes('str'); // true
```

Outro método foi adicionado para criar uma seqüência de repetição:

```js
'my '.repeat(3); // 'my my my '
```
