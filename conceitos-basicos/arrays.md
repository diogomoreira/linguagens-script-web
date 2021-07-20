# Arrays

Um array é uma **coleção ordenada de valores**. Cada valor é chamado de elemento e cada elemento possui uma posição numérica na matriz, conhecida como **índice**. Os arrays JavaScript não têm tipo: um elemento do array pode ser de qualquer tipo, e diferentes elementos do mesmo array podem ser de tipos diferentes. Os elementos de um array podem até ser objetos ou outros arrays, o que permite criar estruturas de dados complexas.

### Criando arrays

Existem várias maneiras de criar arrays em Javascript:

* Literais de array
* Array com operador spread \(...\)
* `Array.of()` e `Array.from()`
* Construtor `Array()` 

#### Literais

De longe, a maneira mais simples de criar um array é com um literal de array, que é simplesmente uma lista separada por vírgulas de elementos entre colchetes.

```javascript
let arrayVazio = [];
let arrayDeNumeros = [1,2,3];
let arrayStrings = ['Etc', 'Qualquer'];
let arrayComVariosTipos = ['string', 1, 1.2, { nome: 'Diogo' }];
```

#### Operador spread \(...\)

Nas versões mais recentes de Javascript, você pode usar o "**operador spread**" \(...\), para incluir os elementos de um array dentro de um literal de array.

```javascript
let a = [1,2,3]; // a == [ 1, 2, 3 ]
let b = [0, ...a, 4]; // b == [ 0, 1, 2, 3, 4 ]
```

Os três pontos “espalham” o array `a` de modo que seus elementos se tornem elementos dentro do literal do array que está sendo criado \(`b`\). O operador spread é uma ótima maneira de criar "cópias" de um array, por exemplo.

```javascript
let original = [1,2,3];
let copia = [...original];
original[0] = 0; // Mudamos o primeiro elemento para o valor 0
copia[0] // O elemento 0 da cópia ainda é 1
```

#### Array.of e Array.from

O método **`Array.of()`** cria um novo array com um número variável de argumentos, independentemente do número ou do tipo dos argumentos.

```javascript
Array.of(7);       // [7]
Array.of(1, 2, 3); // [1, 2, 3]
```

O método **`Array.from()`** cria uma nova instância de um Array quando for passado um array ou um objeto que possa **iterável** como argumento.

```javascript
Array.from([1,2,3,4,5]) // [ 1, 2, 3, 4, 5 ]
Array.from("Diogo Moreira"); // [ "D", "i", "o", "g", "o" ]
```

#### Construtor Array\(\)

Quando a função de construtor `Array()` é chamada com um argumento numérico, ela usa esse argumento como um comprimento de array. Embora esse array tenha uma quantidade pré-determinada de elementos, todos eles são `undefined` no momento da inicialização.

```javascript
a = Array(5)
a[0] // undefined
```

### Lendo e escrevendo em arrays

Você acessa um elemento de um array usando o operador `[]`. Uma referência ao array deve aparecer à esquerda dos colchetes. Uma expressão arbitrária com um valor inteiro não negativo deve estar entre colchetes. Você pode usar essa sintaxe para ler e gravar o valor de um elemento. Exemplos:

```javascript
let a = ["world"]; // Inicializando um array com 1 elemento
let value = a[0]; // Acessando esse elemento
a[1] = 3.14; // Adicionando o elemento na segunda posição (índice 1)
let i = 2;
a[i] = 3; // Adicionando o elemento na terceira posição (indice 2)
a[i + 1] = "hello"; // Adicionando o elemento na quarta posição (indice 3)
```

Para saber o tamanho de um array, utilizamos sua propriedade `length`

```javascript
let a = [1,2,3];
a.length // Retorna 3
```

### Adicionando e removendo elementos

Já vimos a maneira mais simples de adicionar elementos a um array: apenas atribuir valores a novos índices. Você também pode usar o método `push()` para adicionar um ou mais valores ao final de um array.

```javascript
let a = [];
a.push(1);
a.push(2, 3);
a.length // Retorna 3
```

Um dos métodos mais comuns para remover elementos de um array é usando o método `splice`. Ele recebe dois argumentos: o primeiro informa o **índice** \(que começa em 0\) do início da remoção, e o segundo informa **quantos elementos** devem ser removidos.

```javascript
let a = [1,2,3,4];
a.splice(0,1); // Remova 1 elemento a partir do índice 0
a.length; // Retorna 3 => [2, 3, 4]
```

Existem vários métodos de remoção dependendo do cenário que você se encontra, alguns deles são baseados em estruturas de dados \(como pilhas, por exemplo\). O próprio método `splice` é ambiguo e pode inclusive **adicionar** elementos em um array. Esses argumentos do método `splice` podem ser seguidos por qualquer número de argumentos adicionais que especifiquem **elementos a serem inseridos no array**, começando na posição especificada pelo primeiro argumento.

```javascript
let array = [1,2,3,4,5];
array.splice(0,1); // Remova 1 elemento a partir do índice 0
array.splice(0,0,1);
```

Na linha 3 do código acima, os argumentos indicam que `splice` deve: A partir da posição 0, modificando 0 elementos \(nenhum\), adicionar o elemento 1. Utilize um terminal de browser para explorar um pouco mais sobre esse método até que ele fique mais claro.

[Veja nesse site outros métodos para remover elementos de um array.](https://love2dev.com/blog/javascript-remove-from-array/)

### Iterando arrays

Nas versões mais modernas de Javascript, a maneira mais fácil de percorrer cada um dos elementos de um array \(ou qualquer objeto iterável\) é com o loop `for/of`. Outra boa maneira é com `forEach()`. Você passa uma função para o método `forEach()` de uma matriz e `forEach()` invoca sua função uma vez em cada elemento da matriz.

```javascript
let letras = Array.from("Hello World");
letras.forEach(letras => { // Arrow Function
    console.log(letras);
});
```

### Usando `map`, `filter` e `reduce`

Existem alguns métodos de array que facilitam os laços de repetição e podem ser usados em vários cenários. Vamos tomar como exemplo o seguinte array:

```javascript
let pessoas = [
	{
	  nome: "Fulano",
	  idade: 32,
	  salario: 1000,
	  cargo: 'Engenheiro de Software'
	},
	{
	  nome: "Beltrano",
	  idade: 25,
	  salario: 1000,
	  cargo: 'Programador'
	},
	{
	  nome: "Sicrano",
	  idade: 27,
	  salario: 1200,
	  cargo: 'Designer'
	},
];
```

O método **`map()`** passa cada elemento do array no qual é invocado para a função que você especifica e retorna um array contendo os valores retornados por sua função. No exemplo abaixo, vamos **dobrar o salário de todas as pessoas**:

```javascript
pessoas.map((pessoa) => { // Para cada 'pessoa' no array 'pessoas'
    pessoa.salario = pessoa.salario * 2; // Mude o salario para o dobro
    return pessoa; // Retorne a pessoa com os valores atualizados
});
```

Já o método **`filter()`** retorna **um novo array** contendo um **subconjunto dos elementos do array** no qual ele é chamado. A função que você passa para ele deve ser o que chamamos de **predicado**: uma **função que retorna verdadeiro ou falso**. No exemplo abaixo, vamos criar um novo array apenas com pessoas que tem o cargo de **Designer**.

```javascript
let designers = pessoas.filter((pessoa) => { // Para cada 'pessoa'
    return pessoa.cargo === 'Designer'; // Filtre os que tem o cargo designer
});
```

Os método `reduce()` combina os elementos de um array, usando a função que você especificar, para produzir **um único valor**. O `reduce` recebe dois parâmetros:

1. Função que tem dois parâmetros: o **acumulador** \(`sum` no exemplo abaixo\) e o elemento atual da iteração do array \(`pessoa` no exemplo abaixo\);
2. O valor inicial do acumulador \(`0` no exemplo abaixo\).

No exemplo, vamos somar todos os salários das pessoas do array:

```javascript
let salarioTotal = pessoas.reduce((sum, pessoa) => {
  return sum + pessoa.salario;
}, 0);
```



