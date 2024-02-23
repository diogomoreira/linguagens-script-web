# NodeJS

Diferentemente do que muitos pensam, **Node.js não é um framework javascript**, e muito menos uma **linguagem.** Ele é um **ambiente que executa códigos Javascript além do browser**, como por exemplo em servidores ou **no seu terminal/prompt de comando**. Ao utilizar NodeJS, você programa utilizando a [linguagem JavaScript](https://www.luiztools.com.br/post/por-que-stanford-trocou-java-por-javascript/), a mesma usada há décadas no browser.

Para instalar esse ambiente, vá até o [site do NodeJS](https://nodejs.org/en/) e clique na opção **Current** (versão `20.9.0` na data desse material). Siga a instalação para o seu ambiente, seja Windows, Linux ou Mac. Ao final da instalação, ao executar o terminal/prompt de comando você deve ser capaz de executar o comando `node -v`.

```
node -v
v20.9.0
```

Assim como no browser precisamos invocar um script por meio da tag `<script>` aqui será necessário invocar um comando `node <arquivo.js>` passando como parâmetro o arquivo de script que deseja executar. O primeiro código para testar nosso ambiente será

```
console.log("Olá, mundo Javascript");
```

O código acima deve imprimir a mensagem no terminal logo após o comando.

Para entender a diferença entre o ambiente NodeJS e o browser, execute o comando abaixo em um console de browser e depois execute o mesmo arquivo com NodeJS:

```
window.alert("Oi");
```

Veja que esse segundo comando só é possível ao usar o ambiente de host **navegador da web**. Ao usar um ambiente como **Node**, a referência de `window` não existe.

Assim como window não existe no ambiente node, outras referências também não vão existir, como [localStorage](../recursos-avancados/armazenamento.md), [adição e remoção de elementos](../javascript-no-browser/add-removendo-elementos.md), etc.
