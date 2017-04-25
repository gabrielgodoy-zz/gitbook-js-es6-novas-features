## Weaksets

É um tipo de Set que utiliza memória de maneira mais eficiente

O WeakSets é um tipo onde somente objetos podem ser armazenados

** WeakSets não são iteráveis, e você não pode ler valores **

```js
let weakTags = new WeakSet();

weakTags.add("Javascript"); // Inválido, somente objetos podem ser adicionados a Weaksets
weakTags.add({name: "Javascript"});
let iOS = {name: "iOS"};
weakTags.add(iOS);
weakTags.has(iOS); // true
weakTags.delete(iOS); // true
```

### Casos de uso de WeakSets
Podemos usar weakSets para criar grupos especiais a partir de objetos existentes **sem mutações**. Favorecer objetos imutáveis permite um código mais simples com **nenhum efeito colateral inesperado**.

Exemplo de mutação não necessária em cada objeto post sem Weaksets

```js
let readPosts = new WeakSet();
postList.addEventListener('click', (event) => {
	// Muta objetos 'post', criando uma nova propriedade para indicar se ela foi lida
	post.isRead = true; 
});
// ... renderizando posts
for(let post of postArray) {
	if(!post.isRead) { // Verifica uma propriedade em cada post
		_addClassToPost(post.element);
	}
}
```

Exemplo usando WeakSets sem a necessidade de mutação de objetos (criar propriedades flag)
Criando grupo de objetos e verificando a presença desses objetos no grupo de weakset

```js
let readPosts = new WeakSet();

postList.addEventListener('click', () => {
	readPosts.add(post); // Adicionar objetos a um grupo de posts de leitura weakset
});

// ... renderizando posts
for(let post of postArray) {
	if(!readPosts.has(post)) { // has() verifica se um objeto está presente no WeakSet
		_addClassToPost(post.element);
	}
}
```
