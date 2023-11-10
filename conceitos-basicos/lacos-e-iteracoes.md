# Laços e iterações

Laços oferecem um jeito fácil e rápido de executar uma ação repetidas vezes. Em Javascript temos algumas estruturas para laços:

* `while` e `do/while`
* `for`
* `for/of`
* `for/in`

### while

Assim como a instrução `if` é a condicional básica do JavaScript, a instrução `while` é o loop básico do JavaScript. Para executar uma instrução `while`, o interpretador **primeiro avalia a expressão**. Se o valor da expressão for falso, o interpretador ignora a instrução que serve como corpo do loop e passa para a próxima instrução no programa. Se, por outro lado, a expressão for verdadeira, o interpretador executa a instrução e a repete, voltando ao início do loop e avaliando a expressão novamente. No exemplo abaixo, o laço se repete imprimindo os números de 0 a 9 e para quando a variável count chega em 10, o que faz a expressão ser avaliada como falsa.

```javascript
let count = 0;
while (count < 10) {
  console.log(count);
  count++;
}
```

Para os casos onde precisamos avaliar a expressão **após a execução**, usamos a alternativa `do/while`:

```javascript
let count = 0;
do {
  console.log(count);
  count++;
} while (count < 10);
```

### for

A instrução **`for`** fornece uma construção de loop que geralmente é mais conveniente do que a instrução `while`.

A instrução `for` simplifica os loops que seguem um padrão comum. **A maioria dos loops tem algum tipo de variável de contagem**. Essa variável é **inicializada antes do início do loop** e é **testada antes de cada iteração do loop**. Finalmente, a variável do contador é incrementada ou de outra forma atualizada no final do corpo do loop, pouco antes de a variável ser testada novamente.

No loop com `for`, as três operações estão contempladas na sintaxe:

```javascript
for (let index = 0; index < 10; index++) {
  console.log(index);
}
```

### for/of

As versões modernas de Javascript definem uma nova instrução de loop: **`for/of`**. Este novo tipo de loop usa a palavra-chave `for`, mas é um tipo de loop completamente diferente do loop for visto anteriormente. O loop `for/of` funciona com **objetos iteráveis:** arrays e strings, por exemplo, são iteráveis: eles representam uma sequência ou conjunto de elementos que você pode fazer um loop (ou **iterar**) usando um loop `for/of`.

O exemplo abaixo soma todos os elementos de um array de números

```javascript
let numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9];
let sum = 0;

// Para cada um dos elementos de 'numeros'
// associe o elemento a uma variável 'element'
for (let element of numeros) { 
  sum += element; 
}
```

### for/in

O laço **`for/in`**  interage sobre propriedades de um objeto, na ordem original de inserção. Uma vez que um objeto pode ter uma quantidade indefinida de propriedades, esse loop pode auxiliar no acesso a essas propriedades.

No exemplo abaixo,  `objeto` tem 3 propriedades (que podem ser acessadas com a sintaxe `[]`, conforme já vimos em [Expressões](expressoes.md#expressoes-de-acesso-de-propriedades). O loop `for/in` associa o **nome da propriedade** para uma variável a cada iteração.

```javascript
let objeto = {
  nome: "Diogo",
  sobrenome: "Moreira",
  idade: 32,
};

for (let prop in objeto) {
  console.log(objeto[prop]);
}
```
