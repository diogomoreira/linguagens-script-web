# Variáveis

Quando um programa precisa reter um valor para uso futuro, ele atribui o **valor** a (ou “armazena” o valor em) uma **variável**. A maneira como as variáveis funcionam é outra característica fundamental de qualquer linguagem de programação.

O termo “**variável**” implica que novos valores podem ser atribuídos: que o valor associado à variável pode variar conforme o nosso programa é executado. Se atribuirmos permanentemente um valor a um nome, chamaremos esse nome de **constante** em vez de variável.

Antes de usar uma variável ou constante em um programa JavaScript, você deve declará-la. Nas versões mais recentes do JS, isso é feito com as palavras-chave `let` e `const`, que veremos a seguir. Antes, as variáveis eram declaradas com `var`, e é bem possível que você ainda encontre vários exemplos de JS por ai usando apenas `var`, que também será discutido aqui.

### `let` e `const`

Em Javascript moderno, variáveis são definidas com `let`&#x20;

```javascript
let i;
let sum;

let a, b;
```

É uma boa prática de programação atribuir um valor inicial às suas variáveis ao declará-las, quando isso for possível.

```javascript
let mensagem = "hello";
let i = 0, j = 0, k = 0;
let x = 2, y = x*x;
```

Para declarar uma constante em vez de uma variável, use `const` em vez de `let`. **`const`** funciona exatamente como `let`, exceto que você deve inicializar a constante ao declará-la.

```javascript
const nome = "Diogo";
const sobrenome = "Moreira";
const nomeCompleto = `${nome} ${sobrenome}`;
```

### Escopos

O escopo de uma variável é a **região do código-fonte do programa na qual ela é definida**. Variáveis e constantes declaradas com `let` e `const` têm escopo de bloco. Isso significa que eles são definidos **apenas dentro do bloco de código no qual a instrução let ou const aparece**. As definições de função JavaScript são blocos, assim como os corpos de instruções `if / else`, loops `while`, loops `for` e assim por diante. De modo geral, se uma variável ou constante é declarada dentro de um conjunto de chaves, então essas chaves delimitam a região do código em que a variável ou constante é definida.

Quando uma declaração aparece no nível superior, fora de qualquer bloco de código, dizemos que é uma **variável ou constante global e tem escopo global**. No **Node.js** e nos módulos JavaScript do lado do browser, o escopo de uma variável global é o arquivo que ela é definida.

O interpretador JavaScript realiza coleta de lixo automática para gerenciamento de memória. Isso significa que um programador de JavaScript geralmente não precisa se preocupar com a destruição ou desalocação de objetos ou outros valores. Quando um valor não está mais acessível - quando um programa não tem mais como se referir a ele - o intérprete sabe que ele nunca pode ser usado novamente e automaticamente recupera a memória que estava ocupando. (Os programadores de JavaScript às vezes precisam tomar cuidado para garantir que os valores não permaneçam inadvertidamente alcançáveis - e, portanto, não recuperáveis - por mais tempo do que o necessário.)

### Declarações e tipos

Se você está acostumado com linguagens tipadas estaticamente, como **C**, você pode pensar que o objetivo principal das declarações de variáveis é especificar o tipo de valores que podem ser atribuídos a uma variável. Mas, como você viu, não há nenhum tipo associado às declarações de variáveis de JavaScript. **Uma variável de JavaScript pode conter um valor de qualquer tipo**. Por exemplo, é perfeitamente legal (mas geralmente um estilo de programação pobre) em JavaScript atribuir um número a uma variável e, posteriormente, atribuir uma string a essa variável:

```javascript
let i = 10;
i = "ten";
```

### Declaração de variáveis com `var`

Em versões de JavaScript anteriores, a única maneira de declarar uma variável é com a palavra-chave `var` e **não havia como declarar constantes**. A sintaxe de `var` é como a sintaxe de `let`. Embora `var` e `let` tenham a mesma sintaxe, existem diferenças importantes na forma como funcionam:

* Variáveis ​​declaradas com `var` não têm escopo de bloco. Em vez disso, eles têm como escopo o corpo da função que o contém, não importa o quão profundamente aninhados estejam dentro dessa função.
* Se você usar `var` fora do corpo de uma função, ele declara uma **variável global**. Mas as variáveis ​​globais declaradas com `var` diferem das globais declaradas com `let` de uma maneira importante. Globais declarados com `var` são implementados como **propriedades do objeto global**. O objeto global pode ser referenciado como `globalThis`. Portanto, se você escrever `var x = 2;` fora de uma função, é como se você escrevesse `globalThis.x = 2;`.
* Ao contrário das variáveis ​​declaradas com `let`, é legal declarar a mesma variável várias vezes com `var`. E como as variáveis ​​var têm escopo de função em vez de escopo de bloco, é comum fazer esse tipo de redeclaração. A variável `i` é freqüentemente usada para valores inteiros e, especialmente, como a variável de índice de **loops** `for`. Em uma função com vários loops for, é típico que cada um comece por (`var i = 0;`) Como `var` não faz o escopo dessas variáveis ​​para o corpo do loop, cada um desses loops é (inofensivamente) redeclarado e reinicializando a mesma variável.
* Um dos recursos mais incomuns das declarações `var` é conhecido como _**hoisting**_. Quando uma variável é declarada com `var`, a declaração é "elevada" para o topo da função envolvente. A inicialização da variável permanece onde você a escreveu, mas a definição da variável vai para o topo da função. Portanto, as variáveis ​​declaradas com `var` podem ser usadas, sem erros, em qualquer lugar na função envolvente. Se o código de inicialização ainda não foi executado, o valor da variável pode ser `undefined`, mas você não receberá um erro se usar a variável antes de ser inicializada.
