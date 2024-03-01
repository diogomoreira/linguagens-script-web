# Objetos

Objetos são o tipo de dados mais fundamental do JavaScript, e você já os viu muitas vezes por aqui. Como os objetos são tão importantes para a linguagem JavaScript, é importante que você entenda como eles funcionam em detalhes.

Um objeto é um valor composto: ele agrega **vários valores** (valores primitivos ou outros objetos) e permite que você **armazene e recupere esses valores por nome**.

Um objeto é uma coleção não ordenada de propriedades, cada uma delas com um nome e um valor. Os nomes das propriedades são geralmente strings, então podemos dizer que os **objetos mapeiam strings para valores**. Além de manter seu próprio conjunto de propriedades, um objeto JavaScript também "herda" as propriedades de outro objeto, conhecido como seu “**protótipo**”. Os objetos JavaScript são **dinâmicos**, o que significa que as **propriedades podem ser adicionadas e excluídas**.

Qualquer valor em JavaScript que não seja uma `string`, um `number`, um `boolean`, `null` ou `undefined` é um objeto. E mesmo que os demais não sejam objetos, eles podem se comportar como objetos imutáveis.&#x20;

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

Veja como acessar as propriedades de um objeto na nossa seção de [Expressões](../expressoes.md#expressoes-de-acesso-de-propriedades).

### Criando objetos

A maneira mais fácil de criar um objeto é incluir um **literal de objeto** em seu código JavaScript. Em sua forma mais simples, um **literal de objeto** é uma lista de propriedades colocadas entre chaves, separadas por vírgulas de `nomes` e `valores` separados por dois pontos, como em `nome:valor`.

Um nome de propriedade é um identificador JavaScript ou uma string. Um valor de propriedade é qualquer expressão JavaScript; o valor da expressão (pode ser um valor primitivo ou um valor de objeto) torna-se o valor da propriedade. O exemplo abaixo mostra alguns desses casos

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

Um uso para `Object.create()` é quando você deseja se proteger contra **modificações não intencionais (mas não maliciosas) de um objeto por uma função** que você não tem controle (uma vez que estamos usando referência ao invés de valor). Em vez de passar o objeto diretamente para a função, você pode passar um objeto que herda dela. Se a função ler propriedades desse objeto, ela verá os valores herdados. Se ele definir propriedades, no entanto, essas gravações não afetarão o objeto original.

```javascript
let o = { x: "Não mude esse valor" };
codigoExterno.funcaoQualquer(Object.create(o));
```

### Testando propriedades

Uma vez que os objetos JavaScript podem ser considerados conjuntos de propriedades e geralmente é útil poder testar a associação de uma propriedade ao conjunto - **para verificar se um objeto tem uma propriedade com um determinado nome**. Você pode fazer isso com o operador `in`, com os métodos `hasOwnProperty()` e `propertyIsEnumerable ()` ou simplesmente consultando a propriedade. Todos os exemplos mostrados aqui usam strings como nomes de propriedade.

```javascript
let o = { x:1 };
"x" in o // => true
"y" in o // => false
"toString" in o // => true, pois herda a função toString
```

O método `hasOwnProperty()` de um objeto testa se esse objeto tem uma propriedade própria com o nome fornecido. Ele retorna `false` para propriedades herdadas:

```javascript
let o = { x:1 };
o.hasOwnProperty("x") // => true
o.hasOwnProperty("y") // => false
o.hasOwnProperty("toString") // => false
```

### Métodos de objetos

Nas versões mais modernas de Javascript, a sintaxe literal do objeto foi estendida para permitir um atalho onde a **palavra-chave da função e os dois pontos são omitidos**, resultando em um código como este:

```javascript
let quadrado = {
  area() {
	return this.lado * this.lado;
  },
  lado: 10,
};
quadrado.area();
```

### Gets e Sets de propriedades

Todas as propriedades do objeto que discutimos até agora foram propriedades de dados com um nome e um valor comum. JavaScript também suporta **propriedades de acesso**, que não têm um único valor, mas em vez disso, têm um ou dois métodos de acesso: um **`getter`** e / ou um **`setter`**.

Quando um programa consulta o valor de uma propriedade do acessador, o JavaScript invoca o método **`getter`** (sem passar argumentos). O valor de retorno desse método se torna o valor da expressão de acesso à propriedade. Quando um programa define o valor de uma propriedade do acessador, o JavaScript invoca o método **`setter`**, passando o valor do lado direito da atribuição. Este método é responsável por “definir”, em certo sentido, o valor da propriedade. O valor de retorno do método setter é ignorado.

Se uma propriedade tem um método `getter` e um método `setter`, é uma propriedade de **leitura/gravação**. Se tiver apenas um método getter, será uma propriedade somente leitura. E se tiver apenas um método setter, é uma propriedade somente de gravação, e as tentativas de leitura sempre avaliam como indefinido.

Propriedades de acesso podem ser descritas em um literal de objeto:

```javascript
let objeto = {
  n: '',
  
  get nome() {
    return this.n;
  },
  set nome(novoNome) {
    this.n = novoNome;
  }
}

objeto.nome = 'Diogo' // Por baixo, invocamos o método set
objeto.nome // Acessamos como propriedade, mas por baixo, invocamos o método get
```

