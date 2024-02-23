# Funções

Uma função é um bloco de código JavaScript que é definido uma vez, mas que pode ser executado ou invocado qualquer número de vezes. As funções JavaScript são parametrizadas: uma definição de função pode incluir uma lista de **parâmetros**, que funcionam como variáveis locais para o corpo da função. A maneira mais direta de definir uma função JavaScript é com a palavra-chave **`function`**, que pode ser usada como uma **declaração** ou como uma **expressão**.

```javascript
function funcaoX(parametro1, parametro2) {
    // Definindo uma função por meio de declaração
    console.log(`Parâmetros: ${parametro1} e ${parametro2}`);
}

const funcaoY = function(parametro) {
    // Definindo uma função por meio da expressão 'function'
    return `Parâmetro: ${parametro}`;
};
```

As invocações de função fornecem valores, ou **argumentos, para os parâmetros da função**. As funções geralmente usam seus valores de argumento para calcular um valor de retorno que se torna o valor da expressão de invocação de função. Esse retorno é feito por meio da palavra-chave `return`.

```javascript
funcaoX('linguagens de scripts para web', 'segundo período');
let texto = funcaoY('linguagens de scripts para web');
```

Se uma função é atribuída a uma propriedade de um objeto, ela é conhecida como um **método desse objeto.** Quando uma função é invocada em ou por meio de um objeto, esse objeto é o contexto de invocação ou este valor para a função.

```javascript
const objeto = {
  nome: "Diogo",
  sobrenome: "Moreira",
  getNome: function () {
    return `${this.nome} ${this.sobrenome}`;
  }
};

console.log(objeto.getNome());
```

As **definições de função JavaScript podem ser aninhadas em outras funções** e têm acesso a quaisquer variáveis que estejam no escopo onde foram definidas. Isso significa que as funções JavaScript são _closures_ e habilitam técnicas de programação importantes e poderosas.

```javascript
function demonstrandoClosures(texto) {
  function imprimirTexto() {
    console.log(texto);
  }
  return imprimirTexto;
}

let primeiroClosure = demonstrandoClosures("LSWEB"); 
let segundoClosure = demonstrandoClosures("ADS-IFPB");
primeiroClosure(); // Executar essa função sempre vai imprimir "LSWEB"
segundoClosure(); // Executar essa função sempre vai imprimir "ADS-IFPB"
```

Closure é a forma de fazer com que as variáveis dentro de uma função sejam **privadas** e **persistentes**.

### Arrow Functions

Nas versões mais modernas de Javascript, você pode definir funções usando uma sintaxe particularmente compacta conhecida como "_**arrow functions**_".&#x20;

A palavra-chave `function` não é usada e, como as _arrow function_ são expressões em vez de instruções, também **não há necessidade de um nome de função**. A forma geral de uma _arrow function_ é uma lista separada por vírgulas de parâmetros entre parênteses, seguida pela seta `=>`, seguida pelo corpo da função entre chaves .

```javascript
const soma = (x,y) => { return x + y; };
```

Caso a expressão não tenha mais do que uma linha, podemos omitir as chaves e a palavra `return`.

```javascript
const soma = (x,y) => x + y;
```

Caso a _arrow function_ tenha apenas um parâmetro, os parênteses podem ser omitidos também.

```javascript
const raizQuadrada = x => Math.sqrt(x);
```

Porém, caso a _arrow function_ não tenha nenhum parâmetro, os parênteses devem se fazer presentes.

Além disso, se o corpo de sua _arrow function_ é uma **única instrução de retorno**, mas a expressão a ser retornada é um **objeto literal**, então você **tem que colocar o objeto literal entre parênteses para evitar ambigüidade sintática** entre as chaves do corpo de uma função e as chaves de um literal de objeto.

```javascript
// Retorna um objeto com a propriedade value com valor x
const f = x => { return {value: x}; };
// Retorna um objeto com a propriedade value com valor x.
// Nesse segundo caso usamos parênteses para evitar a ambigüidade sintática
const g = x => ({valor: x});

const h = x => {valor: x}; // Não retorna nada
const i = x => {v: x, w: x}; // Erro de sintaxe
```

### Parâmetros rest

Nas versões mais recentes do Javascript, temos a sintaxe de **Parâmetros Rest** (**rest parameter)**, que nos permite representar um **número indefinido de argumentos como um array**. Se o último argumento nomeado de uma função tiver prefixo com  `...`, ele irá se tornar um array em que os elemento são os argumentos passados à função.

```javascript
function funcaoZ(parametro1, parametro2, ...outrosParametros) {
    // outrosParametros é um array e pode ser acesso normalmente
}
```

### Parâmetros predefinidos

**Os parâmetros predefinidos de uma função** permitem que parâmetros regulares sejam inicializados com valores iniciais caso `undefined` ou nenhum valor seja passado.

```javascript
function multiply(a, b = 1) { // Caso b não seja passado, assume o valor de 1
  return a * b;
}

multiply(5, 2); // 10
multiply(5, 1); // 5
multiply(5);    // 5
```
