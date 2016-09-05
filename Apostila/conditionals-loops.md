# Estruturas Condicionais / Loops

Uns dos pontos principais da programação que os pré-processadores trazem para o CSS são as estruturas condicionais/estruturas de loop.

Iremos utilizar o plugin [advanced-variables](https://github.com/jonathantneal/postcss-advanced-variables)

## Estruturas Condicionais

A estrutura condicional é muito simples, e pode ser aplicada diretamente no seletor:

```sass
div {
 @if 3 > 1 {
  ...
 }
 @else if 3 > 2 {
  ...
 }
 @else {
  ...
 }
}
```

Um ponto interessante é que a condição pode ser qualquer expressão válida. (Até variáveis, caso você tenha importado o plugin de variável), por exemplo:

```sass
$color: blue

.texto {
 @if $color == blue {
  color: $color;
 }
}

// gera

.texto {
 color: blue;
}
```

## Loops

A estrutura de loop nos ajuda a reduzir estilos baseados em iterações, como por exemplos cores, tamanhos e afins. Para este conceito, o plugin nos fornece dois tipos de iteração: `for` e `each`:

```sass
@for $i from 1 to 3 {
 .heading-$i { font-size: $(i)rem; }
}

// gera
.heading-1 { font-size: 1rem; }
.heading-2 { font-size: 2rem; }
.heading-3 { font-size: 3rem; }
```

```sass
@each $color in (blue, green, red) {
  .color-$color {
    color: $color;
  }
}

// gera
.color-blue { color: blue; }
.color-green { color: green; }
.color-red { color: red; }
```

Próximo tópico: [Funções, Mixins e Extends](functions.md)
