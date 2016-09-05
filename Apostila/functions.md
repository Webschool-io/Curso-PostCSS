# Mixins e Extends

Um mixin é uma função que nos permite "automatizar" a estilização de nossos elementos. Algo muito semelhante a Composição.

Para compreendermos melhor como um mixin pode se comportar, vamos pensar no seguinte exemplo:

```sass
.icon {
  @mixin icon github, black;
}

.icon {
  background-image: url(icon-github.svg);
  color: black;
}
```

Para o estudo deste conceito, iremos utilizar o plugin [mixins](https://github.com/postcss/postcss-mixins).

## Mixins

Dentro de um mixin, é possível aplicar qualquer regra/estilo que esteja disponível (Baseando-se em seus plugins do projeto). Vamos por hora focarmos na mínima dessa premissa, implementando o exemplo anterior:

```sass
@define-mixin icon $name, $color {
  background-image: url(icon-$(name).svg);
  color: $color;
}
```

O `@define-mixin` é o construtor de mixins. O primeiro parâmetro é o nome do mixin. Os parâmetros seguintes são os parâmetros aceitos pelo mixin, separados por virgula. Exatamente como fazemos no JavaScript:

```js
function icon (name, color) {}
```

Assim como no ES6, também é possível definir valores padrões para os argumentos dos nossos mixins:

```sass
@define-mixin icon $name: github, $color: black
```

A definição de um mixin não está limitada a utilizações dentro de regras. Podemos também gerar novas regras:

```sass
@define-mixin icon $name, $color {
  .icon-$(name) {
    ...
    // Podemos acessar diretamente o que foi passado para o mixin e inserir onde quisermos
    @mixin-content

    // em conjunto com o plugin nested
    &:hover {
      ...
    }
  }
}

// Para utilizar:
@mixin icon github, black {
  font-size: 1rem;
}
```

## Extends

O conceito do extends é algo muito mais simples do que um mixin. A ideia é só fornecer um estilo base para ser reutilizado. Não gerar novos estilos. Por exemplo:

```sass
@define-placeholder box {
  box-sizing: border-box;
  display: block;
  height: 200px;
  width: 200px;
}

.panel {
  @extend box;
}
```

Podemos também estender estilos de regras comuns:

```sass
.list {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

.bordered-list {
  @extend .list;
  border: 1px solid black;
}
```

Próximo tópico: [Considerações](considerations.md)
