# O que é PostCSS
[PostCSS](https://github.com/postcss/postcss) é uma ferramenta para transformar folhas de estilo (arquivos css) com a ajuda de plugins escritos em JavaScript.

O PostCSS difere de qualquer preprocessador existente, pelo simples fato de não ser um preprocessador. A premissa de um preprocessador é a utilizacão de uma template engine (Geralmente vemos isso em arquivos `.scss, .styl, .less`), e a partir dela converter o arquivo em um arquivo `.css`. O arquivo convertido passa por uma série de transformacoes já pré determinadas (Por exemplo, uma diretiva de `mixin` no sass, sempre será a mesma diretiva), o que impede (ou dificulta) a implementacao de novas features para os preprocessadores.

Todo e qualquer plugin utilizado dentro do pipeline do PostCSS, é criado separado da ferramenta em si. Ou seja, qualquer um pode criar seu plugin para utilizar da maneira que julgar melhor. Um fluxo de transformacao pode ser descrito da seguinte maneira:

1. A ferramenta recebe o arquivo (ou arquivos) para processar
2. Um objeto contendo todo o css em formato de árvore de nós é retornado pela operacao de processamento
3. Os plugins sao processados de maneira síncrona, para garantir a ordem deles de acordo com a chamada
4. A ferramenta recebe o objeto transformado, e processa para um arquivo css novamente

Na maior parte do tempo, iremos utilizar o PostCSS de uma maneira muito semelhante ao que usamos nossos preprocessadores, com a diferenca da flexibilidade para modificar nossos plugins da maneira que melhor nos atende, e com uma performance muito maior.

Próximo tópico: [Como um plugin funciona](plugins.md)



