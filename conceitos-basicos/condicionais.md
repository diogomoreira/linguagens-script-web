# Condicionais

As instruções condicionais executam ou ignoram outras instruções, dependendo do valor de uma **expressão** especificada. Se você imaginar um interpretador JavaScript seguindo um caminho através de seu código, as declarações condicionais são os lugares onde o código se ramifica em dois ou mais caminhos e o interpretador deve escolher qual caminho seguir. As subseções a seguir explicam a condição básica do JavaScript, a instrução `if/else`, e também cobrem o `switch`.

Antes de falar das instruções condicionais, é importante falar de alguns operadores que serão utilizados:

| Operador                       | Descrição                                                                               |                          Exemplos que retornam verdadeiro                          |
| ------------------------------ | --------------------------------------------------------------------------------------- | :--------------------------------------------------------------------------------: |
| Igual (`==`)                   | Retorna verdadeiro caso os operandos sejam **iguais**.                                  | <p><code>3 == var1</code></p><p><code>"3" == var1</code> <code>3 == '3'</code></p> |
| Não igual (`!=`)               | Retorna verdadeiro caso os operandos **não sejam iguais**.                              |             <p><code>var1 != 4</code><br> <code>var2 != "3"</code></p>             |
| Estritamente igual (`===`)     | Retorna verdadeiro caso os operandos sejam **iguais e do mesmo tipo**.                  |                                    `3 === var1`                                    |
| Estritamente não igual (`!==`) | Retorna verdadeiro caso os operandos **não sejam iguais e/ou não sejam do mesmo tipo**. |             <p><code>var1 !== "3"</code><br> <code>3 !== '3'</code></p>            |
| Maior que (`>`)                | Retorna verdadeiro caso o operando da esquerda seja maior que o da direita.             |              <p><code>var2 > var1</code><br> <code>"12" > 2</code></p>             |
| Maior que ou igual (`>=`)      | Retorna verdadeiro caso o operando da esquerda seja maior ou igual ao da direita.       |             <p><code>var2 >= var1</code><br> <code>var1 >= 3</code></p>            |
| Menor que (`<`)                | Retorna verdadeiro caso o operando da esquerda seja menor que o da direita.             |        <p><code>var1 &#x3C; var2</code><br> <code>"12" &#x3C; "2"</code></p>       |
| Menor que ou igual (`<=`)      | Retorna verdadeiro caso o operando da esquerda seja menor ou igual ao da direita.       |        <p><code>var1 &#x3C;= var2</code><br> <code>var2 &#x3C;= 5</code></p>       |

### Instrução if/else

A instrução `if` é a instrução de controle fundamental que permite ao JavaScript tomar decisões ou, mais precisamente, **executar instruções condicionalmente** uma vez que uma dada expressão seja avaliada como `true`. A instrução `else` é usada em conjunto para dar um fluxo alternativo, caso a instrução seja avaliada como `false`.

```javascript
if (expressao)  // Caso expressao seja avaliada como 'verdadeiro'
    // Código a ser executado em apenas uma linha

if (expressao) {  // Caso expressao seja avaliada como 'verdadeiro'
    // Código a ser executado em
    // várias linhas
}

if (expressao) // Caso expressao seja avaliada como 'verdadeiro'
    // Código a ser executado em apenas uma linha
else  // Caso expressao não seja avaliada como 'verdadeiro'
    // Código a ser executado em apenas uma linha

let n = 1;
if (n === 1)
    console.log("Você tem 1 nova mensagem");
else
    console.log(`Você tem ${n} novas mensagens.`);
```

Assim como em outras linguagens, também é permitido **aninhar vários ifs** para se alcançar condições ainda mais complexas.

Também é possível usar uma instrução `else if`.

```javascript
if (n === 1) {
    // Execute bloco #1
} else if (n === 2) {
    // Execute bloco #2
} else if (n === 3) {
    // Execute bloco #3
} else {
    // Se todo o resto falhar...
}
```

### Instrução switch

Quando **todas as ramificações dependem do valor da mesma expressão**, talvez seja um desperdício avaliar repetidamente essa expressão em várias instruções `if`. A instrução `switch` lida exatamente com essa situação. A palavra-chave `switch` é seguida por uma **expressão entre parênteses** e um bloco de código entre chaves. A seguinte instrução `switch` é equivalente às instruções `if/else` repetidas mostradas na seção anterior:

```javascript
switch (n) {
    case 1: // Execute esse bloco caso n === 1
        // Execute o bloco #1.
        break; // Pare o comando 'switch' aqui
    case 2: // Execute esse bloco caso n === 2
        // Execute o bloco #2.
        break; // Pare o comando 'switch' aqui
    case 3: // Execute esse bloco caso n === 3
        // Execute o bloco #3.
        break; // Pare o comando 'switch' aqui
    default: // Se todo o resto falhar...
        break;
}
```

Quando um switch é executado, ele calcula o valor da expressão e, em seguida, procura um **caso** (`case`) cuja expressão seja avaliada com o mesmo valor (determinada pelo operador `===`). Se encontrar um, começa a executar o bloco de código na instrução marcada pelo caso. Se não encontrar um caso com um valor correspondente, ele procura uma instrução rotulada como `default`. Se não houver, a instrução `switch` pula o bloco de código completamente.

Observe a palavra reservada `break` é usada no final de cada caso neste código. A instrução `break`, em resumo, faz com que o interpretador pule para o final da instrução `switch` e continue com a execução do código.

### Operador condicional ternário

O operador condicional (ternário) é o único operador JavaScript que possui três operandos. Este operador é frequentemente usado como um atalho para a instrução `if`.

```javascript
condicao ? expressao1 : expressao2
```

Se `condicao` é `true`, o operador retornará o valor de `expressao1`; se não, ele retorna o valor de `expressao2`. Por exemplo, para exibir uma mensagem diferente baseada no valor da variável `isMember` poderiamos usar o seguinte código:

```javascript
let valor = 10;
let mensagem = 'O valor total é de ' + (isMember ? valor * 0.75 : valor );
```
