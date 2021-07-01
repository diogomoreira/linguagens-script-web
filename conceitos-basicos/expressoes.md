# Expressões

Uma **expressão** é uma **frase/linha de JavaScript que pode ser avaliada para produzir um valor**.

Uma constante em seu programa é um tipo de expressão muito simples. Um nome de variável também é uma expressão simples que avalia qualquer valor atribuído a essa variável. Expressões complexas são construídas a partir de expressões mais simples.

As expressões mais simples, conhecidas como **expressões primárias**, são aquelas independentes - elas não incluem nenhuma expressão mais simples. Expressões primárias em JavaScript são valores **constantes** ou **literais**, certas **palavras-chave** de linguagem e **referências de variáveis**.

### Expressões de inicializadores

Os inicializadores de **objeto** e **array** são expressões cujo valor avaliado é um objeto ou array recém-criado. Os inicializadores de array têm uma sintaxe um pouco mais simples e vamos começar com eles. 

#### Array

Um **inicializador de array é uma lista separada por vírgulas de expressões contidas entre colchetes**. Os elementos deste array são inicializados com os valores das expressões separadas por vírgulas:

```javascript
[] // Um array vazio
[1,2,3,2+2] // Um array com os elementos: 1,2,3,4
```

As expressões de elemento em um inicializador de array podem ser outros inicializadores de array, o que significa que essas expressões podem criar matrizes:

```javascript
let matriz = [[1,2,3], [4,5,6], [7,8,9]];
```

#### Object

Expressões de **inicializador de objeto** são como expressões de inicializador de array, mas os colchetes são substituídos por chaves, e cada subexpressão é prefixada com um **nome de propriedade** e **dois** **pontos**, seguido da expressão que dá valor a propriedade.

```javascript
let p = { x: 2.3, y: -1.2 }; // Objeto p com propriedades x e y
let q = {}; // Objeto q sem propriedades
q.x = 2.3; q.y = -1.2; // Agora q tem as mesmas propriedades de p
```

É possível definir as propriedades como novos objetos dentro do primeiro, assim como fizemos para construir matrizes anteriormente.

### Expressões de definição de funções

Uma expressão de definição de função define uma **função JavaScript**, e o valor avaliado de tal expressão é a função recém-definida. Uma expressão de definição de função normalmente consiste na palavra-chave `function` seguida por uma **lista separada por vírgulas de zero ou mais identificadores \(os nomes dos parâmetros\) entre parênteses** e um **bloco de código JavaScript \(o corpo da função\) entre chaves**. Por exemplo:

```javascript
// Uma função sendo atribuida a uma variável
let soma = function(numero1, numero2) {
    // Corpo da função
}

function subtracao(numero1, numero2) {
    // Corpo da função
}
```

### Expressões de acesso de propriedades

Uma expressão de acesso de propriedade **avalia o valor de uma propriedade de objeto ou um elemento de um array**. JavaScript define **duas sintaxes** para acesso à propriedade

```javascript
expressao.identificador;
expressao[expressao];
```

O primeiro estilo de acesso à propriedade é uma expressão seguida por um ponto e um identificador. A expressão especifica o objeto e o identificador especifica o nome da propriedade desejada.

O segundo estilo de acesso à propriedade segue a primeira expressão \(o objeto ou array\) com outra expressão entre colchetes. Esta segunda expressão especifica o nome da propriedade desejada ou o índice do elemento desejado do array.

```javascript
let o = {x: 1, y: {z: 3}}; // Um objeto
let a = [o, 4, [5,6]]; // Um array que contem um objeto
o.x // => 1: Propriedade x do objeto o
o.y.z // => 3: Propriedade z da expressão o.y
o["x"] // => 1: property x of object o
a[1] // => 4: elemento no índice 1 da expressão a
a[2]["1"] // => 6: elemento no índice 1 da expressão a[2]
a[0].x // => 1: propriedade x da expressão a[0]
```

#### Acesso de propriedades condicional

As versões mais recentes do Javascript adicionam dois novos tipos de acesso a propriedades:

```javascript
expressao?.identificador;
expressao?.[expressao];
```

Em JavaScript, os valores `null` e `undefined` são os únicos dois valores que **não possuem propriedades**. Em uma expressão de acesso à propriedade usando `.` ou `[]`, você obtém um **`TypeError`** se a expressão à esquerda for avaliada como `null` ou `undefined`. Você pode usar `?.` e `?.[]` para se proteger contra erros desse tipo.

```javascript
let a = { b: null };
a?.b // Só tenta acessar b caso a não seja null ou undefined
a.b.c // TypeError porque tentamos acessar uma propriedade a partir de um null

let array = [1,2,3]; // Índices: 0, 1, 2
let valor = array?.[0]; // Acessamos o valor do indice 0 porque array não é null
```

### Expressões de invocação

Uma expressão de invocação é a sintaxe do JavaScript para **executar uma função ou método**. Ele começa com uma expressão de função que identifica a função a ser chamada. A expressão da função é seguida por um parêntese aberto, uma lista separada por vírgulas de zero ou mais expressões de argumento e um parêntese fechado.

```javascript
soma(1,2); // soma é a função; 1 e 2 os argumentos
Math.max(x,y,z); // Math.max é a função; x, y, e z os argumentos.
a.sort() // a.sort é uma função; nesse caso não há elementos (mas poderiamos).
```

