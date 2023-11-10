# "Hello, World" em Javascript

Para aprender uma nova linguagem de programação, a prática é a parte mais importante do processo. Então, vamos começar com uma pequena prática de Javascript para apresentar o ambiente que iremos trabalhar durante esse semestre.

Para fazer isso, você precisa de um interpretador de JavaScript. A maneira mais fácil de experimentar algumas linhas de JavaScript é abrir as ferramentas de desenvolvimento da web em seu navegador (com `F12`, `Ctrl-Shift-I` ou `⌘-⌥-I` no Mac) e selecione a guia **Console**. Uma janela semelhante a imagem abaixo deve surgir.

![Tela de "Ferramentas de Desenvolvedor" no navegador Firefox.](<../.gitbook/assets/Screen Shot 2021-06-07 at 19.09.18.png>)

Você pode digitar o código no prompt e ver os resultados à medida que digita. As ferramentas de desenvolvedor do navegador geralmente aparecem como painéis na parte inferior ou direita da janela do navegador, mas geralmente você pode separá-las como janelas separadas (conforme ilustrado na figura acima), o que geralmente é bastante conveniente.

O primeiro código para testar nosso ambiente será

```javascript
console.log("Olá, mundo Javascript");
```

O código acima deve imprimir a mensagem no console do browser logo após o comando. Mais um comando que pode ser testado agora é

```javascript
window.alert("Oi")
```

Veja que esse segundo comando só é possível ao usar o ambiente de host **navegador da web**. Ao usar um ambiente como **Node**, a referência de `window` não existe.
