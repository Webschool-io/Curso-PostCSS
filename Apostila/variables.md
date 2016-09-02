# Variáveis
O conceito de uma variável no PostCSS, segue o mesmo conceito das linguagens de programação. Alocar um determinado valor/operação para reaproveitamento de código.

Mas diferente dos pré-processadores que costumamos utilizar (E como vocês já sabem), o PostCSS funciona por plugins. Então a variável irá se comportar baseada no plugin utilizado.

Para este conceito, iremos utilizar o plugin "oficial" para o PostCSS, o [simple-vars](https://github.com/postcss/postcss-simple-vars):

```sass
// a definição de uma variável
$black: #000;
```

```sass
// a utilização de uma variável
.texto {
 color: $black;
}
```

O plugin lida automaticamente com os valores digitados. Interpretando números, strings, HEX e afins automaticamente.

Como na maior parte das linguagens de programação, este plugin possibilita a interpolação dentro dos nossos arquivos:

```sass
$side: left;
$offset: 10px;

.texto {
 margin-$(side): $offset; 
}
```
