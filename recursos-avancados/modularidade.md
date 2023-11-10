# Modularidade

O objetivo da programação modular é permitir que grandes programas sejam montados usando **módulos de código** e que todo esse código seja executado corretamente. Como uma questão prática, modularidade é principalmente sobre **encapsular** ou **ocultar detalhes de implementação** privada.

Até recentemente, o JavaScript não tinha suporte integrado para módulos, e os programadores que trabalhavam em grandes bases de código faziam o possível para usar a modularidade fraca disponível por meio de classes e objetos, por exemplo. As versões mais modernas de Javascript definem **módulos** usando palavras-chave `import` e `export`. Embora a importação e a exportação façam parte da linguagem há anos, elas só foram implementadas por navegadores da web e pelo Node há relativamente pouco tempo.

{% hint style="info" %}
O uso de módulos não funciona ao executar o código localmente. É uma longa discussão, mas pra testar essa funcionalidade, utilize a função **Live Server** do VSCode ou use o Codesandbox que tudo vai funcionar (provavelmente 😅).
{% endhint %}

A modularidade consiste num conceito muito simples: **cada arquivo é seu próprio módulo** e constantes, variáveis e funções definidas em um arquivo são **privadas para aquele módulo**, a menos que sejam **explicitamente exportadas**. Os valores exportados de um módulo estão **disponíveis para uso em módulos que os importam explicitamente**.

### Exportando

Para exportar uma constante, variável, função ou classe de um módulo, basta adicionar a palavra-chave `export` antes da declaração.

```javascript
export const PI = Math.PI;

export function somar(n1, n2) { return n1 + n2; }
```

Como alternativa a adição de `export` em todo o seu módulo, você pode definir suas constantes, variáveis e funções como faria normalmente, sem nenhuma instrução de exportação e, em seguida (normalmente no final do seu módulo), escrever uma única instrução de exportação que declara exatamente o que é exportado em um único lugar. Então, em vez de escrever duas exportações individuais no código anterior, poderíamos ter escrito de forma equivalente uma única linha no final.

```javascript
export { PI, somar };
```

Esta sintaxe se parece com a palavra-chave `export` seguida por um literal de objeto (usando a notação abreviada). Mas, **neste caso, as chaves não definem realmente um objeto literal**. Essa sintaxe de exportação simplesmente requer uma lista separada por vírgulas de identificadores entre chaves.

É comum escrever módulos que exportam apenas um valor (normalmente uma função) e, neste caso, geralmente usamos o `export default` em vez de `export`.

```javascript
function somar(n1, n2) { return n1 + n2; }
export default somar;
```

As **exportações padrão** com `export default` são ligeiramente **mais fáceis de importar** do que as exportações com `export`, então, quando há apenas um valor exportado, usar o `export default` torna as coisas mais fáceis para os módulos que usam seu valor exportado.

As exportações regulares com `export` **só podem ser feitas em declarações que tenham um nome**. Exportações com `export default` podem exportar qualquer expressão, incluindo expressões de função anônima. Isso significa que se você usar o `export default`, poderá exportar literais de objeto.&#x20;

É permitido, mas um tanto incomum, que os módulos tenham um conjunto de `export` e também uma `export default`. Se um módulo tiver uma exportação padrão, **ele só pode ter uma**. Por fim, observe que a palavra-chave export só pode aparecer no nível superior do seu código Java Script. Você não pode exportar um valor de dentro de uma função, loop ou condicional.

### Importando

Você importa valores que foram exportados por outros módulos com a palavra-chave `import`. A forma mais simples de importação é usada para módulos que definem uma **exportação padrão**:

```javascript
// Considerando que o arquivo operacoes.js exporta a função somar como default
import somar from './operacoes.js';
```

Esta é a palavra-chave `import`, seguida por um **identificador** (`soma`), seguida pela palavra-chave `from`, seguida por um literal de string que **nomeia o módulo cuja exportação padrão estamos importando**. O valor de exportação padrão do módulo especificado torna-se o valor do identificador especificado no módulo atual.

O identificador ao qual o valor importado é atribuído é uma constante, como se tivesse sido declarado com a palavra-chave **`const`**. Como as exportações, as importações só podem aparecer no nível superior de um módulo e não são permitidas em funções, loops ou condicionais. **Por convenção quase universal, as importações necessárias para um módulo são colocadas no início do módulo**.

Para importar valores de um módulo que exporta vários valores, usamos uma sintaxe ligeiramente diferente

```javascript
import { somar, subtrair, multiplicar } from './operacoes.js';
```

As exportações não padrão (`export`) de um módulo **têm nomes no módulo de exportação e, quando importamos esses valores, nos referimos a eles por esses nomes**. O módulo de exportação pode exportar qualquer número de valores nomeados. Uma instrução de importação que faz referência a esse módulo pode importar qualquer subconjunto desses valores simplesmente listando seus nomes entre chaves.

Ao importar de um módulo que define muitas exportações, no entanto, você pode facilmente importar tudo com uma instrução de importação como esta:

```javascript
import * as operacoes from './operacoes.js';
operacoes.somar(1,3);
operacoes.subtrair(5,2);
```

Os módulos geralmente definem uma **exportação padrão** (`export default`) ou **várias exportações nomeadas** (`export`). É permitido, mas um tanto incomum, que um módulo use as exportações padrões e nomeadas. Mas quando um módulo faz isso, você pode importar o valor padrão e os valores nomeados com uma instrução de importação como esta:

```javascript
// Considerando que o arquivo operacoes.js exporta a função somar como default
// E todas as outras como exportações nomeadas
import somar, { multiplicar, dividir } from './operacoes.js';
```

### Importando e exportando com renomear

Se dois módulos exportam dois valores diferentes usando o mesmo nome e você deseja importar ambos os valores, você terá que renomear um ou ambos os valores ao importá-lo. Da mesma forma, se você deseja importar um valor cujo nome já está em uso em seu módulo, você precisará renomear o valor importado. Você pode usar a palavra-chave `as` com as importações nomeadas para renomeá-las conforme você as importa:

```javascript
import { somar as operacaoSomar } from './operacoes.js';

operacaoSomar(5,2);
```

Também é possível renomear os valores à medida que você os exporta, mas apenas ao usar a variante da chave da instrução de exportação. Não é comum precisar fazer isso, mas se você escolheu nomes curtos e sucintos para uso dentro de seu módulo, você pode preferir exportar seus valores com nomes mais descritivos que são menos propensos a entrar em conflito com outros módulos. Assim como acontece com as importações, você usa a palavra-chave `as` para fazer isso:

```javascript
export { somar as operacaoSomar };
```

### Usando no ambiente do browser

Agora, apenas precisamos aplicar o conceito de módulo as nossas páginas HTML. Isso é muito semelhante ao modo como aplicamos um script regular a uma página, com algumas diferenças notáveis. Você precisa incluir `type="module"` no elemento `<script>`, para declarar esse script como um **módulo**.

```markup
<script type="module" src="index.js"></script>
```
