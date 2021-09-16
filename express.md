# Express

Express é um _framework_ para construção de aplicativos da web com **Node.js**, de maneira mínima e flexível e que fornece um conjunto robusto de recursos para aplicativos da web.

### Instalação

Assumindo que já tenha instalado o [Node.js](nodejs.md), crie um diretório para conter o seu aplicativo.

```text
mkdir app
cd app
```

Use o comando `npm init` como mostrado em [NPM](npm.md). Por enquanto, é possível simplesmente pressionar RETURN para aceitar os padrões para a maioria deles, com as seguintes exceções:

```text

entry point: (index.js)

```

Insira `app.js`, ou qualquer nome que deseje para o arquivo principal. Se desejar que seja `index.js`, pressione entrar para aceitar o nome de arquivo padrão sugerido.

Agora instale o **Express** no diretório `app` e salve-o na lista de dependências. Por exemplo:

```text
npm install express
```

### Estrutura básica

No diretório `app`, crie um arquivo chamado `app.js` e inclua o seguinte código:

```javascript
import express from "express";

const port = 3000;
const app = express();

app.get('/', (req, res) => {
	res.send('Hello World');
});

app.listen(port, () => {
  console.log(`Executando em http://localhost:${port}`)
})

```

O aplicativo inicia um servidor e escuta a porta **3000** por conexões. O aplicativo responde com “Hello World!” à solicitações para a URL raiz \(`/`\) ou _rota_. Para todos os outros caminhos, ele irá responder com um **404 Não Encontrado**.

### Roteamento básico

O **Roteamento** refere-se à maneira de como um aplicativo responde a uma solicitação do cliente por um endpoint \(endereço\) específico, que é uma URI \(ou caminho\) e um método de solicitação HTTP específico \(GET, POST, e assim por diante\). **Cada rota pode ter uma ou mais funções de manipulação**, que são executadas quando a rota é correspondida.

A definição de rotas aceita a seguinte estrutura:

```javascript
app.metodo(CAMINHO, CALLBACK)
```

Onde:

* `app` é uma instância do `express`.
* `metodo` é um método de solicitação [HTTP](recursos-avancados/fetch-e-http.md).
* `CAMINHO` é um caminho no servidor.
* `CALLBACK` é a função executada quando a rota é correspondida.

Os seguintes exemplos ilustram a definição de rotas simples.

Responder com `Hello World!` na página inicial:

```javascript
app.get('/', function (req, res) {
  res.send('Hello World!');
});
```

Responder a uma solicitação **POST** na rota raiz \(`/`\) com a página inicial do aplicativo:

```javascript
app.post('/', function (req, res) {
  res.send('Got a POST request');
});
```

Responder a uma solicitação PUT para a rota `/user`:

```javascript
app.put('/user', function (req, res) {
  res.send('Got a PUT request at /user');
});
```

Responder a uma solicitação DELETE para a rota `/user`:

```javascript
app.delete('/user', function (req, res) {
  res.send('Got a DELETE request at /user');
});
```

### Métodos de resposta <a id="response-methods"></a>

Os métodos do objeto de resposta \(`res`\) na seguinte tabela podem enviar uma resposta ao cliente, e finalizar o ciclo solicitação-resposta. Se nenhum destes métodos forem chamados a partir de um manipulador de rota, a solicitação do cliente será deixada em suspenso.

| Método | Descrição |
| :--- | :--- |
| [res.download\(\)](https://expressjs.com/pt-br/4x/api.html#res.download) | Solicita que seja efetuado o download de um arquivo |
| [res.end\(\)](https://expressjs.com/pt-br/4x/api.html#res.end) | Termina o processo de resposta. |
| [res.json\(\)](https://expressjs.com/pt-br/4x/api.html#res.json) | Envia uma resposta JSON. |
| [res.redirect\(\)](https://expressjs.com/pt-br/4x/api.html#res.redirect) | Redireciona uma solicitação. |
| [res.render\(\)](https://expressjs.com/pt-br/4x/api.html#res.render) | Renderiza um modelo de visualização. |
| [res.send\(\)](https://expressjs.com/pt-br/4x/api.html#res.send) | Envia uma resposta de vários tipos. |
| [res.sendFile](https://expressjs.com/pt-br/4x/api.html#res.sendFile) | Envia um arquivo como um fluxo de octeto. |
| [res.sendStatus\(\)](https://expressjs.com/pt-br/4x/api.html#res.sendStatus) | Configura o código do status de resposta e envia a sua representação em sequência de caracteres como o corpo de resposta. |



