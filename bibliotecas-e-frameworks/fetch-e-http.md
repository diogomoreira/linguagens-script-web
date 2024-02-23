# HTTP

HTTP é um protocolo de transferência que possibilita que as pessoas que inserem a URL do seu site na Web possam ver os conteúdos e dados que nele existem. A sigla vem do inglês _Hypertext Transfer Protocol_. Esse sistema é a base da comunicação que existe em toda a Internet em que os sites e conteúdos que tragam hiperlinks possam ser encontrados mais facilmente pelo público por meio de um clique do mouse ou um toque na tela.

Qualquer servidor que você escolha para hospedar o seu site tem um **programa projetado para receber solicitações HTTP**. Portanto, o navegador que você usa é um **cliente HTTP** que envia solicitações constantemente ao algum servidor.

Assim, quando um usuário acessa ou digita a URL do seu site, o navegador cria uma solicitação HTTP na web e a envia ao endereço de IP indicado pela URL. Dessa forma, o servidor recebe essa solicitação e envia os arquivos ou dados associados.

### Códigos de status

Toda requisição HTTP retorna um código que evidencia o que aconteceu com essa requisição, deixando claro se ela foi bem-sucedida ou não. Existem **cinco categorias de códigos de status HTTP**:

* **Respostas informativas** (Códigos 100 a 199)
* **Respostas bem-sucedidas** (200 a 299)
* **Redirecionamentos** (300–399)
* **Erros do cliente** (400-499)
* **Erros do servidor** (500-599)

Você pode ver uma lista completa de códigos de status em MDN Web Docs ([https://developer.mozilla.org/en-US/docs/Web/HTTP/Status](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)). Não é necessário decorar todos os códigos, mas busque sempre o mais adequado para o seu cenário.

### Métodos

HTTP fornece vários **métodos**. No entanto, você usará principalmente apenas cinco deles. Para começar, você deseja que as operações **Criar**, **Ler**, **Atualizar** e **Excluir** estejam associadas aos métodos HTTP:

| **Operação** | **Descrição**                                                                                 |
| ------------ | --------------------------------------------------------------------------------------------- |
| `GET`        | Recupera o estado atual de um recurso em algum tipo de representação (XML/JSON, por exemplo). |
| `POST`       | Cria um novo recurso.                                                                         |
| `PUT`        | Modifica um recurso completamente                                                             |
| `DELETE`     | Exclui um recurso                                                                             |
| `PATCH`      | Modifica um recurso parcialmente                                                              |

#### **GET**

O método HTTP GET é o que você geralmente usa quando deseja associar às **operações de recursos de leitura**. As operações GET bem-sucedidas devem ser associadas ao código de status **200 OK** se a resposta contiver dados ou **204 No Content** se a resposta não contiver dados.

#### POST

O método HTTP POST é normalmente o que você deseja associar à **operações de criação de recursos**.&#x20;

Para operações de criação bem-sucedidas, você pode responder com o status **201** **CREATED**, e para operações de pesquisa ou leitura bem-sucedidas, você deve usar os códigos de status **200 OK** ou **204 NO CONTENT**, embora a chamada seja feita usando o método POST HTTP.

Para erros, as respostas REST podem ter códigos de status de erro diferentes com base no tipo de erro.

{% hint style="info" %}
Há certas exceções quando você deseja usar o **método POST para operações de leitura**. No entanto, deve ser colocado em prática após um processo bem pensado. Uma dessas exceções é a operação de pesquisa em que os critérios de filtro têm muitos parâmetros que podem ultrapassar o limite de comprimento da chamada GET. Uma string de consulta GET tem um limite de 256 caracteres. Por outro lado, o método POST não é limitado pelo tamanho do URL para enviar pares de nome e valor.

Você também pode usar o método POST com HTTPS para uma chamada de leitura se os parâmetros de entrada enviados contiverem qualquer **informação privada ou segura**
{% endhint %}

#### DELETE

O método HTTP DELETE é o que você deseja associar às **operações de exclusão de recursos**. Uma chamada de exclusão bem-sucedida deve excluir o recurso associado aos parâmetros passados. Além disso, as operações DELETE bem-sucedidas devem ser associadas ao código de status **204 No Content**.

#### PUT

O método HTTP PUT é o que você geralmente deseja associar às **operações de atualização de recursos**. Além disso, as operações de atualização bem-sucedidas devem ser associadas a um código de status **200 OK** se a resposta contiver dados ou **204 No Content** se a resposta não contiver dados.

#### PATCH

O método HTTP PATCH é o que você deseja associar às **operações de atualização parcial de recurso**. Além disso, as operações PATCH bem-sucedidas devem ser associadas a um código de status **200 OK**. PATCH é relativamente novo em comparação com outras operações HTTP.
