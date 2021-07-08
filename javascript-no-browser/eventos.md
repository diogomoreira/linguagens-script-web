# Eventos

Os programas de JavaScript do lado do cliente usam um modelo de programação baseado em eventos. Nesse estilo de programação, o navegador da web **gera um evento sempre que algo interessante acontece ao documento ou navegador ou a algum elemento ou objeto associado a ele**. Por exemplo, o navegador da web gera um evento quando termina de carregar um documento, quando o usuário move o mouse sobre um hiperlink ou quando o usuário pressiona uma tecla do teclado.

Se um aplicativo JavaScript se preocupa com um tipo específico de evento, ele pode **registrar uma ou mais funções a serem chamadas quando eventos desse tipo ocorrerem**. Os eventos podem ocorrer em qualquer elemento dentro de um documento HTML. Começamos com algumas definições importantes que ajudam a explicar esse modelo de evento:

* **Tipo de Evento** \(_event type_\). Especifica que tipo de evento ocorreu. O tipo “_mousemove_”, por exemplo, significa que o usuário moveu o mouse. O tipo “_keydown_” significa que o usuário pressionou uma tecla no teclado, entre muitos outros.
* **Destino do Evento** \(_event target_\). Este é o objeto sobre o qual o evento ocorreu ou com o qual o evento está associado. Quando falamos de um evento, devemos especificar o tipo e o destino. Um evento de carregamento em uma janela \(objeto `window`\), por exemplo, ou um evento de clique em um elemento `<button>`.
* **Manipulador ou Ouvinte de Eventos** \(_event handler/event listener_\). Esta função trata ou responde a um evento. Os aplicativos registram suas funções de manipulador de eventos com o navegador da web, especificando um tipo de evento e um destino de evento. Quando um evento do tipo especificado ocorre no destino especificado, o navegador invoca a função do manipulador. Quando os manipuladores de eventos são chamados para um objeto, dizemos que o navegador “disparou” o evento.
* **Objeto de Evento** \(_event object_\). Este objeto está associado a um determinado evento e contém detalhes sobre esse evento. Os objetos de evento são passados ​​como um argumento para a função de manipulador de eventos. Todos os objetos de evento possuem uma propriedade `type` que especifica o tipo de evento e uma propriedade `target` que faz referência ao destino do evento.
* **Propagação de Evento** \(_event propagation_\). Este é o processo pelo qual o navegador decide em quais objetos acionar os manipuladores de eventos. Para eventos que são específicos para um único objeto - como o evento “`load`” no objeto `window` nenhuma propagação é necessária. Porém, quando certos tipos de eventos ocorrem em elementos dentro do documento HTML, eles se propagam na árvore do documento.

### Categorias de eventos

Existem eventos de muitas categorais, alguns deles são **dependentes de dispositivos** \(como cliques de mouse, toques na tela, etc\), outros são **independentes de dispositivo** \(como o fato de ativar uma caixa de texto para começar a digitar\). Não é interessante falar deles individualmente. A medida que a necessidade for surgindo, falaremos de alguns deles e os demais podem ser vistos [nesse documento do MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/Events).

### Registrando manipuladores de eventos

A maneira mais simples de registrar um **manipulador de evento** é definindo uma propriedade do **destino do evento**. Por convenção, as propriedades têm nomes que consistem na palavra “`on`” seguida pelo nome do evento: `onclick`, `onchange`, `onload`, `onmouseover` e assim por diante. Observe que esses nomes de propriedade diferenciam maiúsculas de minúsculas e são escritos em letras minúsculas, mesmo quando o tipo de evento \(como “mouse-over”\) consiste em várias palavras. O código a seguir inclui dois registros de manipulador de eventos deste tipo:

```javascript
window.onload = function () {
  let botao = document.querySelector("#botaoAlerta");
  botao.onclick = function (event) {
    alert("Botão foi clicado");
  };
};
```

[Link para o Codesandbox](https://codesandbox.io/s/manipulacao-de-eventos-25cu8?file=/index.js)

Também é possivel registrar manipuladores de eventos por meio de atributos de elementos no documento HTML. Essa técnica é geralmente desaprovada no desenvolvimento da web moderno, mas é possível e está documentada aqui porque você ainda pode vê-la em código existente.

Ao definir um manipulador de eventos como um atributo HTML, o valor do atributo deve ser uma **string de código JavaScript**. Esse código deve ser o corpo da função do tratador de evento, não uma declaração de função completa. Ou seja, o código do manipulador de eventos HTML não deve ser cercado por chaves e prefixado com a palavra-chave `function`. Por exemplo:

```javascript
<button id="botaoAlerta" onclick="alert("Botão foi clicado")">
    Disparar um alert
</button>
```

### `addEventListener()`

Qualquer objeto que pode ser um destino de evento - isso inclui os objetos `window` e `document` e todos os elementos do documento - definem um método `addEventListener()` que você pode usar para **registrar um manipulador de eventos para esse destino**. Esse método recebe dois argumentos obrigatoriamente.

O primeiro é o **tipo de evento** para o qual o manipulador está sendo registrado. O tipo \(ou nome\) do evento é uma string que não inclui o prefixo “`on`” usado ao definir as propriedades do manipulador de eventos. O segundo argumento é **a função que deve ser chamada quando ocorre o tipo de evento especificado**. O código a seguir registra dois manipuladores para o evento “`click`” em um elemento `<button>`. Observe as diferenças entre as duas técnicas usadas:

```markup
<button id="mybutton">Click me</button>
<script>
let b = document.querySelector("#botaoAlerta");
b.onclick = function () {
  console.log("Obrigado por clicar!");
};
b.addEventListener("click", function () {
  console.log("Obrigado novamente");
});
</script>
```

Chamar `addEventListener()` com “`click`” como seu primeiro argumento não afeta o valor da propriedade `onclick`. Neste código, um clique de botão registrará duas mensagens no console do desenvolvedor. E se chamarmos `addEventListener()` primeiro e, em seguida, definirmos `onclick`, ainda registraremos duas mensagens, apenas na ordem oposta. Mais importante, você pode chamar `addEventListener()` várias vezes para registrar mais de um manipulador para o mesmo tipo de evento no mesmo objeto. Quando um evento ocorre em um objeto, todos os manipuladores registrados para aquele tipo de evento são chamados na ordem em que foram registrados.

`addEventListener()` é pareado com um método `removeEventListener()` que espera os mesmos dois argumentos, mas remove uma função de manipulador de eventos de um objeto em vez de adicioná-la.

