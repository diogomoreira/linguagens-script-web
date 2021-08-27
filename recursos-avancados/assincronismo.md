# Assincronismo

Para entendermos o que é o JavaScript **assíncrono**, nós primeiro temos que ter certeza que entendemos o que é o Javascript **síncrono**. Muitas das funcionalidades que nós vimos até agora são síncronas — você executa um código, e o resultado é retornado assim que o navegador puder. Veja o exemplo abaixo:

```javascript
const btn = document.querySelector('button');
btn.addEventListener('click', () => {
  alert('Você clicou em mim!');
  console.log('Codigo executado após clique no botão ok!');
});
```

Neste bloco, as linhas são executadas uma após a outra:

1. Nós damos referência à um elemento `<button>` que já está disponível na DOM.
2. Nós adicionamos um evento de `click`, e quando ele for clicado ele fará o seguinte:
   1. Mostrar uma mensagem no `alert()`.
   2. Imprimir uma mensagem no `console`.

Enquanto cada operação é processada, **nada mais pode acontecer**. Apenas uma coisa pode acontecer por vez, e tudo é bloqueado até que a operação seja concluída. Nesse caso estamos usando um código **síncrono**.

Por essa razão, muitas funcionalidades de APIs da Web agora usam **código assíncrono na execução**, especialmente aquelas que **acessam** ou **buscam** algum tipo de recurso de um website externo, como pegar um arquivo da rede, acessar um banco de dados e retornar dados dele, acessar uma stream de uma webcam, etc.

Vamos dar uma olhada em um exemplo rápido. Quando você busca uma imagem de um servidor, você não pode retornar o resultado imediatamente. Isso significa que o código abaixo poderia não funcionar:

```javascript
let resposta = fetch('imagem.png'); // Buscando uma imagem
let blob = resposta.blob(); // Lendo os dados da imagem
// Mostra sua imagem na UI
```

Isso acontece por que **você não sabe quanto tempo a imagem levará para ser baixada**, então quando você executar a segunda linha, ela vai resultar em um erro \(provavelmente sempre\) porque a  `resposta` não estará disponível ainda. Você precisa que o seu código **espere** até que a `resposta` seja retornada antes de fazer algo com ela. Isso é o que chamamos de código **assíncrono**. A função `fetch` executa e libera o fluxo normal da aplicação, **mesmo sem ter sido concluída**.

### Programação assíncrona com _callbacks_

Em seu nível mais fundamental, a programação assíncrona em JavaScript é feita com _callback_. Um _callback_ é uma função que você escreve e depois **passa para alguma outra função**. Essa outra função então invoca \(“**chama de volta**” ou "callback"\) sua função quando alguma condição é atendida ou algum evento \(**assíncrono**\) ocorre. A invocação da função de _callback_ que você fornece notifica sobre a condição ou evento e, às vezes, a invocação inclui argumentos de função que fornecem detalhes adicionais.

Já trabalhamos com callbacks até aqui, embora talvez você não tenha percebido. Vamos a alguns exemplos:

#### Timers

Um dos tipos mais simples de assincronia é quando você deseja executar algum código após um determinado período de tempo. Você pode fazer isso com a função `setTimeout()`

```javascript
setTimeout(() => { // Utilizamos uma arrow function
  console.log("Imprimiu no console após 60000ms");
}, 60000);
```

O primeiro argumento para `setTimeout()` é uma função e o segundo é um intervalo de tempo medido em milissegundos. No código anterior, `console.log` será chamada 60.000 milissegundos \(1 minuto\) após a chamada `setTimeout()`. Isso porque ele está dentro de uma **função de callback** que seu programa pode definir e `setTimeout()` **é a função que você invoca para registrar sua função de callback** e especificar sob **quais condições assíncronas ela deve ser chamada**. 

Podemos fazer isso também usando `setInterval()` em vez de `setTimeout()`:

```javascript
setInterval(() => {
  console.log("Imprimiu no console a cada 60000ms");
}, 60000);
```

#### Eventos

Os programas JavaScript no browser são quase universalmente **orientados por eventos**: em vez de executar algum tipo de computação predeterminada, eles normalmente **esperam que o usuário faça algo e, em seguida, responda às ações do usuário**, como já vimos em [Eventos](../javascript-no-browser/eventos.md). Os programas JavaScript orientados a eventos **registram funções de callback para tipos específicos de eventos em contextos específicos**, e o navegador da web invoca essas funções sempre que os eventos especificados ocorrem. Essas funções de retorno de chamada são chamadas de manipuladores de eventos ou ouvintes de eventos e são registradas com `addEventListener()`.

#### Rede

Outra fonte comum de assincronia na programação JavaScript são as **solicitações de rede**. O JavaScript em execução no navegador pode buscar dados de um servidor da web com a API **fetch**, que vamos explorar mais na seção de [Promises](promises.md).



