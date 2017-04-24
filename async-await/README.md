## Funções Async e o operador await
Funções Async podem conter expressões `await`, que pausa a execução da função async e espera pela resolução da promessa que foi passada, e conclui a execução da função async retornando o valor resolvido.

```js
// Alguma função que retorna uma Promise
function getPromise() {
    return new Promise((resolve, reject) => Math.random() > .5 ? resolve('Lucky') : reject('Bad Luck'));
}

/*
Função Async
async/await permite que se escreva código assíncrono usando uma estrutura de código síncrona
*/
async function main() {
    let result;
    // await recebe uma Promise, se rejeitada vai para o block catch com o erro correspondente
    try {
        result = await getPromise();
    } catch (error) {
        result = `Error: ${error}`;
    }
    console.log(result);
}

// Roda função async
main();
```
