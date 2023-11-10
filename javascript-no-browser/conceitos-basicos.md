# Conceitos básicos

A linguagem JavaScript foi criada em 1994 com o propósito expresso de possibilitar o **comportamento dinâmico nos documentos exibidos pelos navegadores da web**. A linguagem evoluiu significativamente desde então e, ao mesmo tempo, o escopo e as capacidades da plataforma web cresceram explosivamente. Hoje, os programadores de JavaScript podem pensar na web como uma plataforma completa para o desenvolvimento de aplicativos.

O NodeJS tem uma única implementação e uma única fonte para documentação. As impleementações da Web, por outro lado, são **definidas por consenso entre os principais fornecedores de navegadores da Web** (Firefox, Chrome, Opera, Safari, etc). Mesmo sem uma documentação única, uma boa fonte é o [MDN Web Docs](https://developer.mozilla.org).

{% hint style="info" %}
Daqui pra frente, toda vez que falarmos "**Javascript do lado cliente**" será uma referência a código que executa no browser e interage com elementos da página.
{% endhint %}

Nesse módulo, falaremos sobre como embutir programas Javascript em páginas HTML e realizar coisas como:

* Controlar o estilo e o conteúdo das páginas;
* Realizar trocas de dados pela internet;
* Manusear histórico e navegação do browser;
* Armazenar dados;

E muitas outras coisas que vão surgindo com a necessidade. A intenção aqui não é cobrir 100% das possibilidades de Javascript em um browser, mas sim dar um pontapé inicial para que você entenda o que pode ser feito ou não.

### A tag `<script>`

Os navegadores da Web exibem documentos HTML por padrão. Se você quiser que um navegador da web execute um código JavaScript, você deve fazer referência a esse código, e é isso que a tag `<script>` faz. O código JavaScript pode aparecer também embutido em um arquivo HTML entre as tags `<script></script>`.

O programa abaixo utiliza um código Javascript embutido para mostrar um relógio que se atualiza a cada 1 segundo (1000ms).

```markup
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>Relógio</title>
  </head>
  <body>
    <h1>Relógio digital</h1>
    <!-- Esse elemento será usado para mostrar as horas -->
    <span id="relogio"></span>

    <script>
      function mostrarHoras() {
        let clock = document.querySelector("#relogio");
        let now = new Date();
        clock.textContent = now.toLocaleTimeString();
      }
      // Mostre a hora assim que carregar o script
      mostrarHoras();
      // Chame a função mostrarHoras a cada 1000ms (1 segundo)
      setInterval(mostrarHoras, 1000);
    </script>
  </body>
</html>
```

Embora embutir o código na página HTML seja possível, é preferível que tivessemos todo o conteúdo do script em um arquivo separado com extensão `.js` (`relogio.js`, por exemplo) e fizessemos referência a ele por meio da tag `script` com o atributo `src`.

```markup
<script src="scripts/relogio.js"></script>
```

{% hint style="info" %}
Dê preferência para adicionar essa tag sempre como a última linha dentro do `<body>` para que ela não atrapalhe o carregamento do conteúdo da página.
{% endhint %}

Arquivos `.js` contem apenas código Javascript, sem tags HTML de qualquer tipo. Existem várias vantagens em usar o atributo `src`:

* Simplifica seus arquivos HTML permitindo que você remova grandes blocos de código Java-Script deles - ou seja, ajuda a **manter o conteúdo e o comportamento separados**.
* Quando várias páginas da web compartilham o mesmo código JavaScript, o uso do atributo src permite que você **mantenha apenas uma única cópia desse código**, em vez de ter que editar cada arquivo HTML quando o código for alterado.
* Se um arquivo de código JavaScript for compartilhado por mais de uma página, ele só precisa ser baixado uma vez, pela primeira página que o utiliza - as páginas subsequentes podem recuperá-lo do cache do navegador.
* Como o atributo src assume uma URL arbitrária como seu valor, um programa JavaScript ou página da web de um servidor da web pode empregar **código exportado por outros servidores da web**.

{% hint style="info" %}
Antigamente pensava-se que os navegadores poderiam algum dia implementar linguagens diferentes do JavaScript, e os programadores adicionaram atributos como `language="javascript"` e `type="application/javascript"` às suas tags. Você vai encontrar esse tipo de escrita em vários exemplos pela web durante seu aprendizado.

Saiba desde já que isso é completamente **desnecessário**. JavaScript é a linguagem padrão (e única) da web. O atributo `language` está obsoleto e existem apenas poucos motivos para usar um atributo `type`. Veremos eles no decorrer desse curso.
{% endhint %}

