# Tipos

Programas de computador funcionam manipulando valores, como um número `3.14` ou o texto `“Hello World”`. Os **Tipos** definem quais valores que podem ser representados e manipulados em uma linguagem de programação, e uma das características mais fundamentais de uma linguagem de programação é o conjunto de tipos que ela suporta.

### Visão geral

Os tipos de JavaScript podem ser divididos em **duas categorias**:

* Tipos **primitivos**;
* Tipos de **objetos**.

Os **tipos primitivos do JavaScript** incluem [números](tipos.md#number), strings de texto e valores booleanos. Os valores especiais de JavaScript `null` e `undefined` são valores primitivos, mas não são números, strings ou booleanos. Qualquer valor JavaScript que **não seja** um número, uma string, um booleano, um símbolo, `null` ou `undefined` **é um objeto**.

Um objeto é uma **coleção de propriedades** onde cada propriedade tem um nome e um valor (um valor primitivo ou outro objeto). Existe um objeto especial em JS, o **objeto global**, que também será abordado aqui. A linguagem também define um tipo especial de objeto, conhecido como `array`, que representa uma **coleção ordenada de valores numerados**. A linguagem JavaScript inclui sintaxe especial para trabalhar com arrays, e estes tem comportamento especial que os distingue de objetos comuns.

JavaScript oferece suporte a um estilo de **programação orientado a objetos**. De maneira geral, isso significa que, **em vez de ter funções definidas globalmente para operar em valores de vários tipos, os próprios tipos definem métodos para trabalhar com valores**. Para "ordenar" os elementos de um array `a`, por exemplo, não passamos `a` para uma função `sort()`. Em vez disso, invocamos o método `sort()` do array `a`:

```javascript
a.sort(); // A versão de 'sort(a)' orientada a objetos.
```

JavaScript **converte os valores de um tipo para outro** automaticamente. Se uma função espera uma `string`, por exemplo, e você dá a ele um número, ele irá converter automaticamente o número em uma string para você. E se você usar um valor não booleano onde um booleano é esperado, o JavaScript será convertido de acordo.

### Number

JavaScript tem um único tipo para todos os números (`number`) e trata todos eles como **números de ponto flutuante** (`float` em C, por exemplo). No entanto, o ponto não será exibido se não houver dígitos após o ponto decimal. Internamente, a maioria dos mecanismos JavaScript otimiza e distingue entre números de ponto flutuante e inteiros, mas isso é algo que os programadores não veem.

Os detalhes sobre a grandeza desse tipo podem ser vistos [aqui](https://2ality.com/2012/04/number-encoding.html). Mais interessante por hora é nos focarmos em **operações** que podem ser feitas com esse tipo.

#### Aritmética em Javascript

Os programas JavaScript funcionam com números usando os operadores aritméticos que a linguagem oferece. Estes incluem `+` para adição, `-` para subtração, `*` para multiplicação, `/` para divisão e `%` para módulo (resto após a divisão). [Versões mais recentes do JavaScript incluem](https://caniuse.com/mdn-javascript\_operators\_exponentiation) `**` para exponenciação.

Além desses operadores aritméticos básicos, o JavaScript suporta operações matemáticas mais complexas por meio de um conjunto de funções e constantes definidas como propriedades do objeto **Math**.

```javascript
Math.pow(2,53); // Exponenciação
Math.round(.6); // Arredondamento para o valor inteiro mais aproximado
Math.ceil(.6); // Arrendondamento 'para cima'
Math.floor(.6); // Arrendondamento 'para baixo'
Math.max(x,y,z); // Maior valor dentro de um conjunto de numeros
Math.min(x,y,z); // Menor valor dentro de um conjunto de numeros
Math.random(); // Número aleatório
Math.sqrt(9); // Raiz quadrada
```

Uma lista completa com as funções e explicações do objeto **Math** pode ser encontrada [aqui](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript/Reference/Global\_Objects/Math).

A **divisão por zero** não é um erro em JavaScript: ela simplesmente retorna `Infinity` ou `-Infinity`. No entanto, há uma exceção: **zero dividido por zero** não tem um valor bem definido e o resultado dessa operação é o valor especial não numérico, `NaN`. `NaN` também surge se você tentar **dividir infinito por infinito**, obter a raiz quadrada de um número negativo ou usar operadores aritméticos com operandos não numéricos que não podem ser convertidos em números.

### Datas e Hora

JavaScript define um "protótipo de objeto" **Date** simples para representar e manipular os números que representam **datas e horas**. As datas de JavaScript são objetos, mas também têm uma representação numérica como um carimbo de data/hora (**Timestamp**) que especifica [o número de milissegundos decorridos desde 1º de janeiro de 1970](https://stackoverflow.com/questions/2533563/why-are-dates-calculated-from-january-1st-1970):&#x20;

```javascript
timestamp = Date.now(); // A data/hora atual como um timestamp.
now = new Date(); // A data/hora atual como um objeto de Data.
ms = now.getTime(); // Converte o objeto em timestamp.
iso = now.toISOString(); // Converte para uma 'string' padronizada.
```

### Strings

Para incluir uma string em um programa JavaScript, simplesmente coloque os caracteres da string dentro de um par correspondente de aspas simples ou duplas ou crases (`'` ou `"` ou `` ` ``). Caracteres de aspas duplas e crases podem estar contidos em strings delimitadas por aspas simples e, da mesma forma, para strings delimitadas por aspas duplas e crases. Aqui estão alguns exemplos de literais de string:

```javascript
"" // String vazia, com 0 caracteres
'testando'
"3.14"
'nome="Diogo"'
"E se usarmos 'aspas simples'?"
`Ou mesmo crases?`
`Tudo isso pode ser feito com "strings" em JS`
```

Strings delimitadas com crases são um recurso recente e permitem que expressões JavaScript sejam incorporadas (ou **interpoladas**) em uma string. Falando sobre strings com mais de uma linha, temos os seguintes cenários possíveis:

```javascript
// O \n indica a quebra de linha, então essa string tem duas linhas
'two\nlines'
// Já o exemplo abaixo trata-se de uma linha só, mas o '\' indica que a 
// string continua nas linhas seguintes
"uma\
unica\
linha"
// Com crases podemos escrever de maneira mais natural
`O caracter inserido ao apertar "enter" ao final dessa
linha é incluído na string final`
```

Um dos recursos integrados do JavaScript é a capacidade de **concatenar strings**. Se você usar o operador `+` com números, ele os adicionará. Mas se você usar esse operador em strings, ele os unirá **anexando o segundo ao primeiro**. Por exemplo:

```javascript
mensagem = "Olá, " + "Fulano";
```

As strings podem ser comparadas com os operadores padrão `===` igualdade e `!==` desigualdade: duas strings são iguais se e somente se consistirem exatamente na mesma sequência de caracteres. Para determinar quantos caracteres uma string tem, podemos usar a propriedade `length`&#x20;

```javascript
nome = "Diogo";
nome.length // Retorna 5
```

Além dessa propriedade, JS provê uma série de funções para trabalhar com Strings.

```javascript
s = "Hello, world"; // Obtaining portions of a string
s.substring(1,4) // => "ell", o 2º, 3º e 4º caracter da string.
s.slice(1,4) // => "ell", o 2º, 3º e 4º caracter da string.
s.slice(-3) // => últimos 3 caracteres da string.
s.split(", ") // => Um array com duas strings ["Hello", "world"]

```

Vale lembrar de que as strings são **imutáveis** em JavaScript. As funções aqui retornam **novas strings,** eles não modificam a string na qual são chamados. Para uma lista completa de métodos de strings, veja [esse documento](https://www.w3schools.com/js/js\_string\_methods.asp).

#### Template Literals

Nas versões mais recentes do JS, os literais de string podem ser delimitados com crases, como já falamos anteriormente. Mas isso é mais do que apenas outra sintaxe literal de string, porque esses literais **podem incluir expressões JavaScript**. O valor final de um literal de string em crases é calculado avaliando quaisquer expressões incluídas, convertendo os valores dessas expressões em strings e combinando essas strings computadas com os caracteres literais dentro dos crases.

```javascript
nome = "Diogo";
saudacao = `Olá, ${nome}.`; // saudação == "Olá, Diogo."
```

Tudo entre o `${` e o correspondente `}` é **interpretado como uma expressão JavaScript**. Tudo o que estiver fora das chaves é um texto literal de string normal. A expressão dentro das chaves é avaliada e então convertida em uma string e inserida no modelo, substituindo o cifrão, as chaves e tudo o que está entre eles. Um literal de modelo pode incluir qualquer número de expressões.

### Booleanos

Um valor booleano representa **verdadeiro** (`true`) ou **falso** (`false`), ativado ou desativado, sim ou não, etc. Existem apenas dois valores possíveis deste tipo. As palavras reservadas `true` e `false` avaliam esses dois valores.

Os valores booleanos são comumente usados em estruturas de controle JavaScript. Por exemplo, a instrução `if / else` em JavaScript executa uma ação se um valor booleano for true e outra ação se o valor for false.

```javascript
if (a === 4) {
    b = b + 1;
} else {
    a = a + 1;
}
```

Este código verifica se a é igual a 4. Em caso afirmativo, ele adiciona 1 a b; caso contrário, adiciona 1 a a.

### `null` e `undefined`

`null` é uma palavra-chave de idioma que avalia um valor especial que geralmente é usado para indicar a **ausência de um valor**. Na prática, entretanto, null é normalmente considerado o único membro de seu próprio tipo e pode ser usado para indicar “nenhum valor” para números e strings, bem como objetos.

A maioria das linguagens de programação tem um equivalente ao nulo do JavaScript: você pode estar familiarizado com ele como `NULL`, `nil` ou `None`. JavaScript também tem um segundo valor que indica ausência de valor. O valor `undefined` representa um tipo mais profundo de ausência. É o valor de variáveis ​​que não foram inicializadas e o valor que você obtém quando consulta o valor de uma propriedade de objeto ou elemento de matriz que não existe. O valor `undefined` também é o valor de retorno de **funções que não retornam explicitamente um valor** e o valor de parâmetros de função para os quais nenhum argumento é passado. `undefined` é uma [constante global](tipos.md#objeto-global) predefinida que é inicializada com o valor indefinido. Apesar dessas diferenças, `null` e `undefined` indicam ausência de valor e muitas vezes podem ser usados ​​de forma intercambiável.

### Objeto global

As seções anteriores explicaram os tipos e valores primitivos do JavaScript.  Mas há um valor de objeto muito importante que devemos abordar agora. O **objeto global** é um objeto (entenderemos mais sobre isso ao decorrer da disciplina) JavaScript regular que serve a um propósito muito importante: as propriedades desse objeto são os identificadores definidos globalmente que estão disponíveis para um programa JavaScript. Quando o interpretador JavaScript é iniciado (ou sempre que um navegador da web carrega uma nova página), ele cria um novo objeto global e fornece um **conjunto inicial de propriedades que definem**

* Constantes globais como `undefined`, `Infinity` e `NaN`
* Funções globais como `isNaN()`, `parseInt()`&#x20;
* Funções de construtor de objetos como `Date()`
* Objetos globais como **`Math`**

As propriedades iniciais do objeto global não são palavras reservadas, mas merecem ser tratadas como se fossem.

