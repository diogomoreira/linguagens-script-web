# DOM - Document Object Model

Um dos objetos mais importantes na programação JavaScript do lado do cliente (_browsers_) é o objeto `Document` - que **representa o documento HTML que é exibido em uma janela ou guia do navegador**. A API para trabalhar com documentos HTML é conhecida como **Document Object Model**, ou **DOM**.

Os documentos HTML contêm elementos HTML aninhados uns nos outros, formando uma **árvore**. Considere o seguinte documento HTML simples:

```markup
<html>
  <head>
    <title>Sample Document</title>
  </head>
  <body>
    <h1>An HTML Document</h1>
    <p>This is a <i>simple</i> document.</p>
  </body>
</html>
```

A tag `<html>` contém as tags `<head>` e `<body>`. A tag `<head>` contém uma tag `<title>`. E a tag `<body>` contém as tags `<h1>` e `<p>`. As tags `<title>` e `<h1>` contêm strings de texto, e a tag `<p>` contém duas strings de texto com uma tag `<i>` entre elas.

O DOM **espelha a estrutura em árvore de um documento HTML**. Para cada tag HTML no documento, há um objeto `Element` correspondente e, para cada texto no documento, há um objeto `Text` correspondente. As classes `Element` e `Text`, bem como a própria classe `Document`, são todas subclasses da classe `Node` (essa palavra referencia um "nó", não confundir com NodeJS), e os objetos Node são organizados em uma estrutura de árvore que o JavaScript pode consultar e percorrer usando a **API DOM**. Uma representação do DOM pode ser vista abaixo.

![Fonte: FLANAGAN, David; NOVAK, Gregor M. Java-Script: The Definitive Guide. 2020.](<../.gitbook/assets/Screen Shot 2021-07-06 at 22.51.22.png>)

A API DOM inclui métodos para criar novos nós `Element` e `Text` e para inseri-los no documento como filhos de outros objetos `Element`. Existem também métodos para mover elementos dentro do documento e removê-los totalmente.

### Objeto global em navegadores web

Em navegadores da web, o [objeto global](../conceitos-basicos/tipos.md#objeto-global) tem **dupla função**: além de definir tipos e funções incorporados (como já vimos antes), ele também representa a janela do navegador da web atual e define propriedades como `history`, que representam o histórico de navegação da janela, e `innerWidth`, que mantém a largura da janela em pixels. Uma das propriedades desse objeto global é chamada de `window` e seu valor é o **próprio objeto global**. Isso significa que você pode simplesmente digitar `window` para se referir ao objeto global em seu código no _browser_.

Cada objeto `window` possui uma propriedade `document` que representa o conteúdo da janela. O objeto Document não é independente, entretanto. É o objeto central no [DOM](dom-document-object-model.md) para representar e manipular o conteúdo do documento.

### Selecionando elementos do `document`

Os programas JavaScript do lado do cliente geralmente precisam manipular um ou mais elementos dentro do documento. Um programa que deseja manipular um elemento embutido no documento deve de alguma forma **obter ou selecionar os objetos** Element que se referem a esses elementos do documento.

#### Selecionando elementos por meio de seletores CSS

Os métodos DOM `querySelector()` e `querySelectorAll()` nos permitem encontrar o elemento ou elementos dentro de um documento que correspondem a um **seletor CSS especificado**. O método `querySelector()` recebe uma string de seletor CSS como seu argumento e r**etorna o primeiro elemento correspondente no documento que encontrar**, ou retorna `null` se nenhum corresponder.

```javascript
let botao = document.querySelector("#botao");
let primeiroBotaoComClasse = document.querySelector(".botao-menu");
```

`querySelectorAll()` é semelhante, mas **retorna todos os elementos correspondentes** no documento em uma "espécie de array" ao invés de apenas retornar o primeiro.

```javascript
let titles = document.querySelectorAll("h1, h2, h3");
```

#### Selecionando por outros métodos

Além dos métodos mostrados anteriormente, o DOM também define vários métodos de seleção de elemento mais antigos que estão mais ou menos obsoletos agora. Você ainda pode ver alguns desses métodos em uso em exemplos na internet e não há problemas em usá-los, porém, prefira a sintaxe com CSS que já é sua conhecida de outros semestres.

```javascript
let sect1 = document.getElementById("sect1");
let titulosH2 = document.getElementsByTagName("h2");
let tooltips = document.getElementsByClassName("tooltip");
```
