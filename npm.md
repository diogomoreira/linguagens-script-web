# NPM

O **npm** é o **Gerenciador de Pacotes do Node** (_Node Package Manager_) que vem junto com a instalação do NodeJS e que é muito útil no desenvolvimento Node.

Por anos, o **NPM** tem sido amplamente usado por desenvolvedores JavaScript para compartilhar ferramentas, instalar módulos e gerenciar suas dependências. O **npm** é uma ferramenta de linha de comando que ajuda a interagir com ferramentas locais de desenvolvimento e plataformas online, como navegadores e servidores. Essa utilidade auxilia na instalação e desinstalação de pacotes, gerenciamento da versões e gerenciamento de dependências necessárias para executar um projeto.

Para garantir que o npm foi instalado corretamente junto com seu NodeJS, digite no terminal/prompt de comando: `npm -v`. Você deve ter uma resposta semelhante a da imagem abaixo

![](<.gitbook/assets/image (4).png>)

Se você já tiver o Node e o npm e deseja começar a construir seu projeto, execute o comando **`npm init`** dentro do diretório que você deseja usar para seu projeto. Com isso, você dará procedimento a inicialização do seu projeto.

Esse comando funciona como uma ferramenta para criar o arquivo **`package.json`** de um projeto, solicitando algumas informações em uma espécie de passo a passo (como na figura abaixo). Depois de executar as etapas do npm init, um arquivo **package.json** será gerado e colocado no diretório atual.

![](<.gitbook/assets/image (3).png>)

O arquivo `package.json` deve se parecer com o código abaixo ao final do procedimento. Veja que os atributos `name` e `author` por exemplo, vão mudar para cada caso.

```
{
  "name": "testes-js-npm",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "Diogo Moreira",
  "license": "ISC"
}
```

### Instalando dependências

Quando necessitamos de uma biblioteca externa em um projeto baseado em **npm**, nós precisamos adicioná-la como dependência do nosso projeto. Para aqueles que já estão acostumados com Maven, o conceito aqui é igual ao das dependências de projetos Maven.

Instalar dependências é uma das coisas mais básicas que você deve aprender a fazer quando começar a usar o `npm`. Sempre que você precisar de uma dependência, geralmente será indicado qual o nome da biblioteca a ser instalada e então você irá usar o comando `npm i` com o nome do pacote desejado. O comando `npm i lodash` a seguir instala (`i`) a dependência [`lodash`](https://www.npmjs.com/package/lodash) no projeto que iniciamos anteriormente:

![](.gitbook/assets/image.png)



Observe o seu diretório e veja que ele criou uma pasta `node_modules` que contem todos os arquivos de todas as suas dependências. **Não é necessário incluir esse diretório nos seus commits**. O `package.json` já define quais serão as dependências e outras pessoas que precisarem compartilhar o mesmo código pode simplesmente executar o comando `npm i` (sem outros parâmetros) e baixar todas novamente.
