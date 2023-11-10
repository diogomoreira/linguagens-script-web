# Fetch

O método `fetch()`, que vimos anteriormente, pode, opcionalmente, aceitar um segundo parâmetro, um objeto `init` que permite controlar uma série de configurações diferentes, incluindo o método HTTP a ser usado na solicitação.

```javascript
fetch(url,
{
    method: 'POST', // *GET, POST, PUT, PATCH, DELETE, etc.
    headers: {
      'Content-Type': 'application/json' // O tipo de conteúdo que estamos enviando
    },
    body: JSON.stringify(data)
});
```

