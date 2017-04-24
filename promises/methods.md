## Métodos de uma Promise

### Promise.all (iterável)
Retorna uma promessa que resolve quando todas as promessas no argumento iterable foram resolvidas. Isso é útil para agregar resultados de múltiplas promessas juntos.

### Promise.race (iterável)
Retorna uma promessa que resolve ou rejeita assim que uma das promessas no iterável resolve ou rejeita, com o valor ou razão dessa promessa.

### Promise.reject (razão)
Retorna um objeto Promise que é rejeitado com o motivo fornecido.

### Promise.resolve (value)
Retorna um objeto Promise que é resolvido com o valor especificado. Se o valor é um `thenable` (ou seja, tem um método then()), a promessa retornada "seguirá" esse `thenable`, adotando seu eventual estado; Caso contrário a promessa devolvida será cumprida com o valor. 

Geralmente, se você quiser saber se um valor é uma promessa ou não - Dê um `Promise.resolve(value)` em vez disso e trabalhe com o valor de retorno como uma promessa.
