# Objetos

Objetos são o tipo de dados mais fundamental do JavaScript, e você já os viu muitas vezes por aqui. Como os objetos são tão importantes para a linguagem JavaScript, é importante que você entenda como eles funcionam em detalhes.

Um objeto é um valor composto: ele agrega **vários valores** \(valores primitivos ou outros objetos\) e permite que você **armazene e recupere esses valores por nome**.

Um objeto é uma coleção não ordenada de propriedades, cada uma delas com um nome e um valor. Os nomes das propriedades são geralmente strings, então podemos dizer que os **objetos mapeiam strings para valores**. Além de manter seu próprio conjunto de propriedades, um objeto JavaScript também "herda" as propriedades de outro objeto, conhecido como seu “**protótipo**”. Os objetos JavaScript são **dinâmicos**, o que significa que as **propriedades podem ser adicionadas e excluídas**.

Qualquer valor em JavaScript que não seja uma `string`, um `number`, um `boolean`, `null` ou `undefined` é um objeto. E mesmo que os demais não sejam objetos, eles podem se comportar como objetos imutáveis. 

**Objetos são mutáveis e manipulados por referência ao invés de valor.** Se a variável `x` se refere a um objeto e o código `let y = x` é executado, a variável `y` contém uma referência ao mesmo objeto, **não uma cópia desse objeto**.

### Propriedades

Uma propriedade tem um **nome** e um **valor**. Um nome de propriedade pode ser qualquer string, incluindo a string vazia, mas **nenhum objeto pode ter duas propriedades com o mesmo nome**. O valor pode ser qualquer valor JavaScript ou pode ser uma **função**. O exemplo abaixo demonstra um objeto com strings, numeros, arrays e funções como suas propriedades.

```javascript
const objeto = {
  nome: "Diogo",
  sobrenome: "Moreira",
  idade: 32,
  contatos: ["diogo.moreira@ifpb.edu.br"],
  getNome: function () {
    return `${this.nome} ${this.sobrenome}`;
  }
};
```

#### Acesso a propriedades

Veja como acessar as propriedades de um objeto na nossa seção de [Expressões](expressoes.md#expressoes-de-acesso-de-propriedades).

### Criando objetos

A maneira mais fácil de criar um objeto é incluir um **literal de objeto** em seu código JavaScript. Em sua forma mais simples, um **literal de objeto** é uma lista de propriedades colocadas entre chaves, separadas por vírgulas de `nomes` e `valores` separados por dois pontos, como em `nome:valor`.

Um nome de propriedade é um identificador JavaScript ou uma string. Um valor de propriedade é qualquer expressão JavaScript; o valor da expressão \(pode ser um valor primitivo ou um valor de objeto\) torna-se o valor da propriedade. O exemplo abaixo mostra alguns desses casos

```javascript
let vazio = {};
let ponto = { x: 0, y: 0};
let livro = {
	"titulo": "Javascript com a turma de Linguagens de Scripts",
	autor: {
		nome: "Diogo",
		sobrenome: "Moreira"
	}
};
```

#### Com o operador `new()`

O novo operador cria e inicializa um novo objeto. A palavra-chave **`new`** deve ser seguida por uma **chamada de função**. Uma função usada dessa forma é chamada de **construtor** e serve para inicializar um objeto recém-criado. JavaScript inclui construtores para seus tipos integrados.

```javascript
let o = new Object();
let a = new Array();
let d = new Date();
let r = new Map();
```

#### Com o método `Object.create()`

`Object.create()` cria um novo objeto, usando seu primeiro argumento como o **protótipo desse objeto**.

```javascript
let o1 = Object.create({x: 1, y: 2});
```

Você pode passar `null` para criar um novo objeto que não tenha um protótipo, mas se você fizer isso, o objeto recém-criado não herdará nada, nem mesmo métodos básicos como `toString()`. Na prática, teremos um objeto mais "pobre" do que se usassemos um literal de objeto.

Um uso para `Object.create()` é quando você deseja se proteger contra **modificações não intencionais \(mas não maliciosas\) de um objeto por uma função** que você não tem controle \(uma vez que estamos usando referência ao invés de valor\). Em vez de passar o objeto diretamente para a função, você pode passar um objeto que herda dela. Se a função ler propriedades desse objeto, ela verá os valores herdados. Se ele definir propriedades, no entanto, essas gravações não afetarão o objeto original.

```javascript
let o = { x: "Não mude esse valor" };
codigoExterno.funcaoQualquer(Object.create(o));
```



