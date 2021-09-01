# Async/Await

Existe uma sintaxe especial para trabalhar com Promises de uma forma mais confortável, chamada "`async` / `await`". Bem mais fácil de entender e usar. Ao invés de criar uma nova Promise dentro de uma função para fazer com que ela seja assíncrona, podemos apenas marcá-la como `async`.

```javascript
async function funcaoAssincrona() {
    // Faça alguma coisa
    return valor;
}
```

E utilizariamos essa função como já fazemos com Promises. Usando as funções `then` e `catch`.

```javascript
funcaoAssincrona().then((valor) => {
    // Faça alguma coisa com o valor retornado
});
```

Portanto, `async` garante que a função retorne uma Promise. Bastante simples, certo? Mas não só isso. Há outra palavra-chave, `await`, que **funciona apenas dentro de funções assíncronas**. Observe o código abaixo.

```javascript
async function funcaoAssincrona() {
    // Faça alguma coisa
    return valor;
}

async function segundaFuncaoAssincrona() {
    const valor = await funcaoAssincrona();
    // Faça algum processamento com o valor
    return segundoValor;
}
```

A palavra-chave `await` faz com que o JavaScript "**espere" até que a promessa seja resolvida** e retorne seu resultado. O `await` **suspende** literalmente a execução da função até que a promessa seja resolvida e, em seguida, a retoma com o resultado da promessa.

É apenas uma **sintaxe mais elegante de obter o resultado da Promise do que usando `then`**. E é mais fácil de ler e escrever. ****Aqui, busca-se simplificar a sintaxe, evitando vários `then` e `catch` quando temos várias funções assíncronas sendo chamadas umas dentro de outras.

{% hint style="info" %}
Não se pode usar o `await` em funções regulares. Se tentarmos usar o `await` em uma função não assíncrona, ocorrerá um erro de sintaxe. Podemos obter esse erro se esquecermos de colocar **`async`** antes de uma função.
{% endhint %}

