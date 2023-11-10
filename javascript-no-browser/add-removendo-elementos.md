# Adicionando e removendo elementos

Até agora vimos como selecionar elementos na página HTML que já foram declaradas no documento e como criar eventos. Agora, vamos aprender como manipular os elementos que estão exibidos na tela.

### Criando elementos

Em um documento HTML, a função `document.createElement()` cria o **elemento HTML especificado**. Esse elemento apesar de já ter sido criado, posteriormente deve ser inserido em um documento HTML. O retorno dessa função é uma referência para o elemento.

```javascript
let paragrafo = document.createElement("p");
```

No exemplo acima, criamos um novo elemento `<p>`. É possível criar qualquer elemento com esse método, bastando apenas mudar o argumento.

### Adicionando elementos

Precisamos aplicar o método `appendChild()` para que o elemento seja, efetivamente, inserido ao documento HTML e fique visível ao usuário. Além disso, precisamos definir qual será o elemento pai, ou seja, o elemento HTML que receberá nosso elemento como filho.

```javascript
let paragrafo = document.createElement("p");
let body = document.querySelector('body');
body.appendChild(paragrafo);
```

Agora temos um documento HTML com um parágrafo, mas ainda sem qualquer texto. Para isso, precisamos criar um elemento de texto. Para criar o nó de texto utilizamos a função `createTextNode()` e também utilizaremos a função `appendChild()` para anexar o nó ao elemento em questão, resumidamente:

```javascript
let paragrafo = document.createElement("p");
let textoParagrafo = document.createTextNode('Texto inserido com Javascript');
paragrafo.appendChild(textoParagrafo);

let body = document.querySelector('body');
body.appendChild(paragrafo);
```

Outra forma de chegar ao mesmo resultado é utilizar a **propriedade** `textContent`. Ao invés de criar e anexarmos um nó de texto podemos alterar diretamente o textContent. O exemplo abaixo produz o mesmo documento.

```javascript
let paragrafo = document.createElement("p");
paragrafo.textContent = 'Texto inserido com Javascript';

let body = document.querySelector('body');
body.appendChild(paragrafo);
```

### Removendo elementos

Assim como usamos `appendChild()` para adicionar elementos na página, podemos utilizar `removeChild()` para removê-los. Partindo do exemplo anterior, onde já tinhamos a referência ao elemento parágrafo, podemos invocar `removeChild()` dessa forma.

```javascript
body.removeChild(paragrafo);
```

Caso você ainda não tenha a referência do elemento a ser removido, use `querySelector` ([como vimos aqui](dom-document-object-model.md#selecionando-elementos-do-document))

```javascript
// Considerando que só houvesse um parágrafo
let paragrafo = document.querySelector("p");
let body = document.querySelector("body");
body.removeChild(paragrafo);
```
