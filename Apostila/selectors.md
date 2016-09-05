# Seletores

Seguindo a premissa de que pré-processadores são extensões do CSS (Desconsiderando a sintaxe aplicada), inicialmente temos disponíveis todos os seletores que já fazem parte da especificação do CSS. Seja um ID, uma Classe, uma Pseudo Classe, e assim por diante.

A vantagem de utilizarmos pré-processadores é a extensibilidade dos seletores. Para este conceito, iremos utilizar o plugin [nested](https://github.com/postcss/postcss-nested) (Vale notar também o [nested-w3c](https://github.com/jonathantneal/postcss-nesting), que segue a especificação oficial):

```sass
// seletor comum
.classe
```

Quanto a utilização de um nível de [especificidade](http://tableless.com.br/pontuacao-especificidade-css/), geralmente iremos fazer isso como fazemos normalmente, sem depender do pré-processador.

```sass
.pai .filho
```

Um dos pontos em que a ferramenta vem para nos ajudar, é para reduzir o código. No caso do aninhamento de regras, podemos tratar da seguinte forma:

```sass
.pai {
  .filho {
```

Dentro de uma "regra", é possível gerar estilos diretamente relacionados a ela, utilizando o seletor `&`:

```sass
.pai {
 &:hover
}

// se torna

.pai:hover
```

```sass
.pai {
 &.avo
}

// se torna

.pai.avo
```

Vale a pena levar em consideração, que o `&` também pode ser utilizado para obter o `nome` da regra (No plugin que estamos utilizando):

```sass
.pai {
 &-avo {
}

// se torna

.pai-avo
```


Próximo tópico: [Separação de Arquivos](files.md)
