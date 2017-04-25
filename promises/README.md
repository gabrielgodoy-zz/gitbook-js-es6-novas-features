## Objetos Promessas
O objeto `Promise` é usado para cálculos que são adiados (demorados, retardados) e assíncronos.

Uma Promessa representa uma operação que ainda não foi concluída, mas que está prevista para o futuro.

A criação de uma nova Promessa define-a automaticamente como **estado pendente**.

### Estados de uma Promise
Internamente, uma promessa pode estar em um de três estados:

- **Pendente**, quando o valor final ainda não está disponível
- **Cumprida**, quando e se o valor final se torna disponível. Um valor de cumprimento se torna permanentemente associado à promessa. Isso pode ser qualquer valor, incluindo undefined.
- **Rejeitado**, se um erro impediu que o valor final fosse determinado. Isso pode ser qualquer valor, incluindo undefined, embora geralmente seja um objeto de Erro, como no tratamento de exceções.

### Criando Promessas
A função construtora da Promise assume uma função anônima com 2 argumentos conhecidos como manipuladores (resolver, rejeitar)
```js
let randomPromise = () => new Promise((resolve, reject) => (Math.random() > .5) ? resolve('ok') : reject('fail'));
```

Agora usando a promessa criada
O segundo parâmetro na função then() age como um bloco catch quando as coisas dão errado.
```js
randomPromise().then(result => console.log(result), err => console.log(err));
```

### then() e catch()
Os métodos `Promise.prototype.then` e `Promise.prototype.catch` retornam promessas, eles podem ser encadeados

### O bloco catch() trata exceções e erros
```js
Promise.resolve('oops, esse não é o json para ser parseado')
  .then(data => JSON.parse(data)) // Tentativa de parsear um arquivo que não é JSON nos leva pa o bloco catch
  .catch(error => alert(`Error: ${error.message}`)); // Erro é alertado
```

### Encadeamento de Promises
O método `then()` retorna uma promessa, então pode ser encadeado novamente em outro `then()`

```js
someFunction.somePromiseReturned()
  .then(getFiles)
  .then(generateIndex)
  .then(generatePosts);
```

### Usando Promessas para requisições Ajax (Promisifying XMLHttpRequest)

```js
function get(url) {
  return new Promise(function(resolve, reject) {
    let req = new XMLHttpRequest();
    req.open('GET', url);

    req.onload = function() {
      // Isso é chamado mesmo com 404, então verifique o status
      if (req.status == 200) {
        // Resolve a promise com o texto de resposta
        resolve(req.response);
      }
      else {
        // Caso contrário rejeitar com o texto de status
        reject(Error(req.statusText));
      }
    };

    // Lida com errors de rede
    req.onerror = function() {
      reject(Error("Network Error"));
    };

    // Faz o request
    req.send();
  });
}

// Usando o XHR "promissificado"
get('story.json').then(function(response) {
  console.log("Success!", response);
}, function(error) {
  console.error("Failed!", error);
});
```
