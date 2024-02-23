# Express

Express é um _framework_ para construção de aplicativos da web com **Node.js**, de maneira mínima e flexível e que fornece um conjunto robusto de recursos para aplicativos da web.

### Instalação

Assumindo que já tenha instalado o [Node.js](nodejs.md), crie um diretório para conter o seu aplicativo.

```
mkdir app
cd app
```

Use o comando `npm init` como mostrado em [NPM](npm.md). Por enquanto, é possível simplesmente pressionar RETURN para aceitar os padrões para a maioria deles, com as seguintes exceções:

```

entry point: (index.js)

```

Insira `app.js`, ou qualquer nome que deseje para o arquivo principal. Se desejar que seja `index.js`, pressione entrar para aceitar o nome de arquivo padrão sugerido.

Para que possamos utilizar módulos vindos de outras bibliotecas, como já vimos anteriormente, precisamos alterar o nosso arquivo `package.json` e adicionar uma linha com

```
"type": "module"
```

Agora instale o **Express** no diretório `app` e salve-o na lista de dependências. Por exemplo:

```
npm install express
```

### Estrutura básica

No diretório `app`, crie um arquivo chamado `app.js` (ou o nome que você escolheu) e inclua o seguinte código:

```javascript
import express from "express";

const port = 3000; // A porta que será usada pela sua aplicação.
const app = express();

app.get('/', (req, res) => {
  res.send('Olá, mundo');
});

app.listen(port, () => {
  console.log(`Executando em http://localhost:${port}`)
})

```

O método `get()` é uma função do objeto de aplicativo (`app`) no Express que define uma rota para uma solicitação GET específica. Ele recebe dois argumentos: o primeiro é o **caminho da rota** e o segundo é uma **função** que será executada quando essa rota for acessada.

O aplicativo inicia um servidor e escuta a porta **3000** por conexões. Neste caso, quando alguém acessar a URL `'/'`, a função anônima será executada e a resposta será enviada com o texto `'Olá, mundo!'`. Para todos os outros caminhos, ele irá responder com um **404 Não Encontrado**.

### Roteamento básico

O **Roteamento** refere-se à maneira de como um aplicativo responde a uma solicitação do cliente por um endpoint (endereço) específico, que é uma URI (ou caminho) e um método de solicitação HTTP específico (GET, POST, e assim por diante). **Cada rota pode ter uma ou mais funções de manipulação**, que são executadas quando a rota é correspondida.

A definição de rotas aceita a seguinte estrutura:

```javascript
app.metodo(CAMINHO, CALLBACK)
```

Onde:

* `app` é uma instância do `express`.
* `metodo` é um método de solicitação [HTTP](fetch-e-http.md).
* `CAMINHO` é um caminho no servidor.
* `CALLBACK` é a função executada quando a rota é correspondida.

Os seguintes exemplos ilustram a definição de rotas simples.

Responder com `Hello World!` na página inicial:

```javascript
app.get('/', function (req, res) {
  res.send('Hello World!');
});
```

Responder a uma solicitação **POST** na rota raiz (`/`) com a página inicial do aplicativo:

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

### Métodos do objeto requisição <a href="#response-methods" id="response-methods"></a>

O objeto de requisição (`req`) contém informações sobre a solicitação HTTP feita pelo cliente, como os cabeçalhos, os parâmetros da URL, os dados do corpo da requisição e muito mais. Você pode acessar essas informações usando propriedades e métodos fornecidos pelo objeto `req`.

Aqui estão alguns exemplos de uso comuns do objeto `req`:

* `req.params`: Um objeto contendo os parâmetros nomeados capturados na URL. Por exemplo, se você tiver uma rota definida como `/users/:id`, pode acessar o valor do parâmetro `id` usando `req.params.id`.
* `req.query`: Um objeto contendo os parâmetros de consulta (query string) enviados na URL. Por exemplo, para a URL `/search?term=express`, você pode acessar o valor do parâmetro `term` usando `req.query.term`.
* `req.body`: Um objeto contendo os dados enviados no corpo da requisição. Para acessar esses dados, é necessário usar um _middleware_, como o `express.json()`

### Métodos do objeto de resposta <a href="#response-methods" id="response-methods"></a>

Os métodos do objeto de resposta (`res`) na seguinte tabela podem enviar uma resposta ao cliente, e finalizar o ciclo solicitação-resposta. Se nenhum destes métodos forem chamados a partir de um manipulador de rota, a solicitação do cliente será deixada em suspenso.

* `res.send()`: Envia uma resposta ao cliente com um corpo de resposta opcional. Pode ser uma string, um objeto JSON, um arquivo etc. Por exemplo, `res.send('Olá, mundo!')` envia a string "Olá, mundo!" como resposta.
* `res.json()`: Envia uma resposta ao cliente no formato JSON. Pode ser usado para enviar objetos JavaScript como resposta. Por exemplo, `res.json({ nome: 'João', idade: 25 })` envia o objeto JSON `{ "nome": "João", "idade": 25 }` como resposta.
* `res.status()`: Define o código de status da resposta. Por padrão, o código de status é 200 (OK). Por exemplo, `res.status(404).send('Página não encontrada')` envia a resposta com o código de status 404 e o corpo "Página não encontrada".
* `res.redirect()`: Redireciona o cliente para outra URL. Por exemplo, `res.redirect('/outra-rota')` redireciona o cliente para a rota `/outra-rota`.

### Middleware

Um middleware no Express é uma função que atua como uma camada intermediária entre a requisição e a resposta em uma aplicação Node.js. Ele recebe a requisição (`req`), a resposta (`res`) e a próxima função (`next`) no ciclo de requisição-resposta.

```javascript
app.use((req, res, next) => {
  console.log('Recebida uma requisição');
  next(); // Passa o controle para a próxima função
});
```

O middleware pode realizar ações intermediárias, como processar dados, modificar objetos de requisição ou resposta, lidar com erros, fazer autenticação e muito mais. Ele é útil para modularizar e reutilizar código em diferentes rotas e pontos do ciclo de vida da requisição.

### Entregando arquivos estáticos

Para entregar arquivos estáticos como imagens, arquivos CSS, e arquivos JavaScript, use a função `express.static` integrada no Express.

Passe o nome do diretório que contém os ativos estáticos para a função para iniciar a entregar os arquivos diretamente. Por exemplo, use o código a seguir para entregar imagens, arquivos CSS, e arquivos JavaScript em um diretório chamado `public`:

```javascript
app.use(express.static("public"));
```

Ao inicializar a aplicação, deverá ser possivel acessar todos os arquivos que estavam dentro de `/public` através da URL (nos exemplos aqui, `http://localhost:3000`), seguido do nome do arquivo exatamente como está no diretório, como nos exemplos abaixo:

```
http://localhost:3000/images/kitten.jpg
http://localhost:3000/css/style.css
http://localhost:3000/js/app.js
http://localhost:3000/images/bg.png
http://localhost:3000/hello.html
```
