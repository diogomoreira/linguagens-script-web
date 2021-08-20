# Armazenamento

Os aplicativos da Web baseados em Javascript podem usar os recursos de um navegador para **armazenar dados localmente no computador do usuário**. Esse armazenamento do lado do cliente \(_client-side_\) serve para dar uma memória ao navegador da web. Os aplicativos da web podem armazenar as preferências do usuário, por exemplo, ou mesmo armazenar seu estado completo, para que possam retomar exatamente de onde você parou no final da sua última visita. O armazenamento do lado do cliente é segregado por padrão, de modo que **as páginas de um site não podem ler os dados armazenados pelas páginas de outro site**. Mas duas páginas do mesmo site podem compartilhar armazenamento e usá-lo como mecanismo de comunicação.

A entrada de dados em um formulário em uma página pode ser exibida em uma tabela em outra página, por exemplo. Os aplicativos da Web podem **escolher o tempo de vida dos dados que armazenam**: os dados podem ser armazenados temporariamente para que sejam retidos apenas até a janela fechar ou o navegador sair, ou podem ser salvos no computador do usuário e armazenados permanentemente para que sejam disponíveis meses ou até anos depois.

Existem várias formas de armazenamento do lado do cliente:

* **Web Storage** \(o que veremos aqui na disciplina\)
* Cookies
* IndexedDB

### **Web Storage**

A API de armazenamento da Web consiste nos objetos `localStorage` e `sessionStorage`, que são objetos essencialmente persistentes que mapeiam chaves de string para valores de string. O Web Storage é muito fácil de usar e adequado para armazenar grandes \(mas não enormes\) quantidades de dados.

