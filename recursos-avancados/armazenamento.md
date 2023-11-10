# Armazenamento

Os aplicativos da Web baseados em Javascript podem usar os recursos de um navegador para **armazenar dados localmente no computador do usuário**. Esse armazenamento do lado do cliente (_client-side_) serve para dar uma memória ao navegador da web. Os aplicativos da web podem armazenar as preferências do usuário, por exemplo, ou mesmo armazenar seu estado completo, para que possam retomar exatamente de onde você parou no final da sua última visita. O armazenamento do lado do cliente é segregado por padrão, de modo que **as páginas de um site não podem ler os dados armazenados pelas páginas de outro site**. Mas duas páginas do mesmo site podem compartilhar armazenamento e usá-lo como mecanismo de comunicação.

A entrada de dados em um formulário em uma página pode ser exibida em uma tabela em outra página, por exemplo. Os aplicativos da Web podem **escolher o tempo de vida dos dados que armazenam**: os dados podem ser armazenados temporariamente para que sejam retidos apenas até a janela fechar ou o navegador sair, ou podem ser salvos no computador do usuário e armazenados permanentemente para que sejam disponíveis meses ou até anos depois.

Existem várias formas de armazenamento do lado do cliente:

* **Web Storage** (o que veremos aqui na disciplina)
* Cookies
* IndexedDB

### **Web Storage**

A API de armazenamento da Web consiste nos objetos **`localStorage`** e **`sessionStorage`**, que são objetos essencialmente persistentes que mapeiam **chaves de string para valores de string**. O Web Storage é muito fácil de usar e adequado para armazenar grandes (mas não enormes) quantidades de dados.

As propriedades **localStorage** e **sessionStorage** do objeto global referem-se a objetos **Storage**. Um objeto **Storage** se comporta de maneira muito semelhante a um objeto JavaScript normal, exceto que:

* Os valores de propriedade dos objetos Storage devem ser strings.
* As propriedades armazenadas em um objeto Storage **persistem**. Se você definir uma propriedade do objeto `localStorage` e, em seguida, o usuário recarregar a página, **o valor que você salvou nessa propriedade ainda estará disponível para o seu programa**.

{% hint style="info" %}
Os exemplos abaixo servem tanto para `localStorage` quanto para `sessionStorage`. Usaremos só localStorage para simplificar e logo a frente teremos uma discussão sobre as diferenças dos dois.
{% endhint %}

{% hint style="warning" %}
Lembre-se que esses dados são armazenados no computador do usuário, para casos onde os dados precisam ser persistidos por sua conta, será necessário utilizar outros mecanismos.
{% endhint %}

Usamos objetos `localStorage` dessa maneira:

```javascript
let nome = localStorage.nomeUsuario; // Buscando o valor armazenado
if (!nome) {
    localStorage.nomeUsuario = "Diogo Moreira"; // Definindo o valor
}
```

Você pode usar o operador `delete` para remover propriedades de `localStorage` e pode usar um loop `for / in` para percorrer as propriedades de um objeto **Storage**.

```javascript
delete localStorage.nomeUsuario;
```

Se você deseja remover todas as propriedades de um objeto de armazenamento, chame o método `clear()`.

```javascript
localStorage.clear();
```

Os objetos Storage também definem os métodos `getItem()`, `setItem()` e `deleteItem()`, que você pode usar em vez de acesso direto à propriedade e o operador de exclusão, se desejar. Lembre-se de que as propriedades dos objetos Storage só podem armazenar strings. Se você quiser para armazenar e recuperar outros tipos de dados, você terá que **codificar** e **decodificar** você mesmo.

```javascript
// Se você armazena um número, ele automaticamente é convertido para string
// Você deve converter ao ler a propriedade do localStorage.
localStorage.x = 10;
let x = parseInt(localStorage.x);

// Convertendo uma data
localStorage.lastRead = (new Date()).toUTCString();
let lastRead = new Date(Date.parse(localStorage.lastRead));

// Usar as funções de JSON é uma maneira conveniente de codificar e decodificar
localStorage.data = JSON.stringify(data); // Codifica e armazena
let data = JSON.parse(localStorage.data); // Recupera e decodifica.
```

### Tempo de vida e escopos

A diferença entre `localStorage` e `sessionStorage` envolve o **tempo de vida e o escopo do armazenamento**. Os dados armazenados por meio de `localStorage` são **permanentes**: eles não expiram e **permanecem armazenados no dispositivo do usuário até que um aplicativo da web os exclua ou o usuário peça ao navegador (por meio de alguma UI específica do navegador) para excluí-los**.&#x20;

O `localStorage` tem como escopo a origem do documento. A **origem** de um documento é definida por seu **protocolo** (http, por exemplo), **nome do host** (o endereço do seu site) e **porta**. **Todos os documentos com a mesma origem compartilham os mesmos dados localStorage**. Eles podem ler os dados uns dos outros e podem substituir os dados uns dos outros. Mas documentos com origens diferentes nunca podem ler ou sobrescrever os dados uns dos outros.

Observe que `localStorage` também tem o escopo definido pela implementação do navegador. Se você visitar um site usando o Firefox e depois visitar novamente usando o Chrome (por exemplo), quaisquer dados armazenados durante a primeira visita **não estarão acessíveis durante a segunda visita**.

Os dados armazenados por meio de `sessionStorage` têm um tempo de vida diferente dos dados armazenados por meio de `localStorage`: eles têm o mesmo tempo de vida que a janela ou a guia do navegador na qual o script que os armazenou está sendo executado. Quando a janela ou guia é fechada, quaisquer dados armazenados por meio de `sessionStorage` são excluídos. (Observe, no entanto, que os navegadores modernos têm a capacidade de reabrir as guias fechadas recentemente e restaurar a última sessão de navegação, portanto, a vida útil dessas guias e sua sessão associada ao armazenamento pode ser maior do que parece)

Como `localStorage`, `sessionStorage` tem como escopo a **origem do documento para que documentos com origens diferentes nunca compartilhem `sessionStorage`**. Mas sessionStorage também tem o escopo definido por janela. Se um usuário tem duas guias do navegador exibindo documentos da mesma origem, essas duas guias têm dados sessionStorage separados: os scripts em execução em uma guia não podem ler ou sobrescrever os dados escritos por scripts na outra guia, mesmo se ambas as guias estiverem visitando exatamente a mesma página e estão executando exatamente os mesmos scripts.

### Eventos de armazenamento

Sempre que os dados armazenados em `localStorage` são alterados, o navegador aciona um evento de “**storage**” em qualquer outro objeto **`window`** para o qual os dados estejam visíveis (mas não na janela que fez a alteração). Por exemplo: se um navegador tiver duas guias abertas para páginas com a mesma origem e uma dessas páginas armazenar um valor em localStorage, a outra guia receberá um evento de “**storage**”. Registre um manipulador para eventos de “**storage**” configurando `window.onstorage` ou chamando `window.addEventListener()` com o tipo de evento “**storage**”.

```javascript
window.addEventListener("storage", (event) => {});
```

O objeto de evento associado a um evento de “**storage**” possui algumas propriedades importantes:

* `key`, o nome ou chave do item que foi definido ou removido. Se o método `clear()` foi chamado, esta propriedade será `null`.
* `newValue`, contém o novo valor do item, se houver. Se `removeItem()` foi chamado, esta propriedade não estará presente.
* `oldValue`, contém o valor antigo de um item existente que foi alterado ou excluído. Se uma nova propriedade (sem valor antigo) for adicionada, esta propriedade não estará presente no objeto de evento.
* `storageArea`, o objeto Storage que mudou. Geralmente é o objeto localStorage.
* `url`, a URL (como uma string) do documento cujo script fez essa alteração de armazenamento.
