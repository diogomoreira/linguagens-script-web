# Classes

Classes em JavaScript foram introduzidas nas versões modernas do Javascript e são **simplificações da linguagem** para as **heranças baseadas nos protótipos**. Classes em JavaScript provêm uma maneira mais simples e clara de criar objetos.

Uma maneira de definir uma classe é usando uma declaração de classe. Para declarar uma classe, você deve usar a palavra-chave `class` seguida pelo nome da classe (aqui `Retangulo`).

```javascript
class Retangulo {
  constructor(altura, largura) {
    this.altura = altura;
    this.largura = largura;
  }
}
```

Uma **Expressão de Classe** (class expression) é outra forma para definir classes. Expressões de Classes podem possuir nomes ou não (anônimas). O nome dado para uma expressão de classe é local ao corpo da classe.

```
// sem nome
let Retangulo = class {
  constructor(altura, largura) {
    this.altura = altura;
    this.largura = largura;
  }
};

// nomeada
let Retangulo = class Retangulo {
  constructor(altura, largura) {
    this.altura = altura;
    this.largura = largura;
  }
};
```

### Métodos construtores <a href="#metodos_prototipos" id="metodos_prototipos"></a>

O construtor é um **método especial** para criar e inicializar um objeto criado a partir de uma classe. Apenas um método especial com o nome _constructor_ pode existir em uma classe. O erro `SyntaxError` será mostrado se a classe contiver mais de um método _constructor._

```javascript
class Retangulo {
  constructor(altura, largura) {
    this.altura = altura;
    this.largura = largura;
  }
}
```

### Instanciando um objeto a partir de uma classe <a href="#metodos_prototipos" id="metodos_prototipos"></a>

Um "construtor" em JavaScript é "somente" uma função que passa a ser chamada com o operador **`new`**. O **operador `new` ** cria uma instancia de uma classe definido pelo usuário ou de um dos tipos nativos (_built-in_) que possuem uma função construtora.

```javascript
class Retangulo {
  constructor(altura, largura) {
    this.altura = altura;
    this.largura = largura;
  }
}

let novoRetangulo = new Retangulo(10,20);
```

### Métodos Protótipos <a href="#metodos_prototipos" id="metodos_prototipos"></a>

Os métodos declarados dentro de uma definição de classe são **métodos protótipos,** aqueles que serão herdados pelos objetos que tomarem a classe definida como seu protótipo. No exemplo abaixo, o método `calcularArea` é herdado por todos os objetos que instanciarem (`new`) o objeto `Retangulo`.

```javascript
class Retangulo {
    constructor(altura, largura) {
      this.altura = altura; this.largura = largura;
    }

    calculaArea() {
        return this.altura * this.largura;
    }
}

const quadrado = new Retangulo(10, 10);

console.log(quadrado.area);
```

### Métodos estáticos <a href="#metodos_estaticos" id="metodos_estaticos"></a>

A palavra-chave [`static`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes/static) define um método estático de uma classe. Métodos estáticos são chamados sem a instanciação da sua classe e não podem ser chamados quando a classe é instanciada. Métodos estáticos são geralmente usados para criar funções de utilidades por uma aplicação.

Chamadas a métodos estáticos são feitas diretamente na classe e não podem ser feitas em uma instância da classe. Métodos estáticos são comumente utilizados como funções utilitárias.

```javascript
class ChamadaDoMetodoEstatico {
  static metodoEstatico() {
    return 'O método estático foi chamado';
  }
}
ChamadaDoMetodoEstatico.metodoEstatico();
// 'O método estático foi chamado'
```
