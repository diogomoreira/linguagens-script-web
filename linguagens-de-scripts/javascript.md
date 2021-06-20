# Contextualização sobre Javascript

**JavaScript** é a linguagem de programação da web. A **grande maioria dos sites** na web usa JavaScript, e todos os navegadores modernos – em _desktops_, _tablets_ e _smartphones_ – incluem interpretadores JavaScript, tornando essa a **linguagem mais implantada da história**.

Na última década, ambientes como o Node.js habilitou a programação JavaScript **fora dos navegadores da web**, e o grande sucesso do Node significa que o JavaScript é agora também a linguagem mais usada entre os desenvolvedores de software.

Se você já estiver familiarizado com outras linguagens de programação, pode ajudá-lo a saber que JavaScript é uma [**linguagem dinâmica**](https://developer.mozilla.org/pt-BR/docs/Glossary/Dynamic_programming_language) e de [**alto nível**](https://blog.betrybe.com/linguagem-de-programacao/linguagem-alto-e-baixo-nivel/).

{% hint style="info" %}
Uma **linguagem de programação dinâmica** é uma linguagem de programação na qual determinadas operações podem ser feitas em tempo de execução em vez de em tempo de compilação. Por exemplo, em JavaScript é possível mudar o tipo de uma variável ou adicionar novas propriedades ou métodos a um objeto enquanto o programa está sendo executado. \([MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Glossary/Dynamic_programming_language)\)
{% endhint %}

Sua sintaxe é **vagamente baseada em Java**, mas as linguagens não são relacionadas de outra forma. O nome “JavaScript” é bastante enganador. Exceto por uma semelhança sintática superficial, JavaScript é completamente diferente da linguagem de programação Java. E o JavaScript há muito superou suas raízes de linguagem de script para se tornar uma **linguagem de propósito geral robusta e eficiente**, adequada para engenharia de software séria e projetos com enormes bases de código.

Como você já deve ter visto em outras disciplinas, para ser útil, toda linguagem deve ter uma plataforma, ou **biblioteca padrão, para realizar coisas como entrada e saída básicas**. A linguagem JavaScript básica define uma **API mínima para trabalhar com números, texto, matrizes, conjuntos, dicionários** e assim por diante, mas não inclui nenhuma funcionalidade de entrada ou saída. A entrada e a saída \(bem como recursos mais sofisticados, como rede, armazenamento e gráficos\) são de responsabilidade do "**ambiente de host**" no qual o JavaScript está incorporado \(na maioria das vezes, o browser\).

O ambiente de host original para JavaScript era um **navegador da web** e ainda é o ambiente de execução mais comum para códigos com a linguagem. O ambiente do navegador da web permite que o código JavaScript obtenha **entrada do mouse e teclado do usuário** e **faça solicitações HTTP,** além disso, permite que exiba a saída para o usuário utilizando **HTML** e **CSS**.

Desde 2010, outro ambiente de host está disponível para código JavaScript: o [**NodeJS**](https://nodejs.org/en/). Em vez de restringir o JavaScript para funcionar com as APIs fornecidas por um navegador da web, o Node dá **acesso a todo o sistema operacional, permitindo que os programas JavaScript leiam e gravem arquivos, enviem e recebam dados pela rede e façam e atendam a solicitações HTTP**. O Node é uma escolha popular para implementar servidores da web e também uma ferramenta conveniente para escrever scripts de utilitários simples como alternativa aos scripts de _shell_.

Iremos abordar um pouco sobre Node na nossa disciplina nos tópicos mais avançados. Por enquanto, nosso ambiente de host padrão será um **navegador da web**. Escolha um navegador de sua preferência.

### Referências

FLANAGAN, David; NOVAK, Gregor M. **Java-Script: The Definitive Guide**. 2020.



