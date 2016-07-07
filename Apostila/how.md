# Como utilizar PostCSS

O PostCSS foi construído em cima do [node](https://nodejs.org/en/), então antes de tudo você precisa ter ele e o [npm](npmjs.com) instalados para prosseguir.

O PostCSS pode ser utilizado com *qualquer extensão*. Na realidade isso não importa muito, porque só estamos passando um arquivo para ser lido, como ele se chama não importa. Por boa convenção chamamos de `.css` mesmo, mas nada impede de criar algo como `.pcss` (Apesar de não utilizado)

Na maior parte dos casos, iremos utilizar ele como plugin para nossos taskrunners, mas ele pode ser utilizado de diversas maneiras. Vamos abordar algumas:

1. Como Plugin de taskrunners (gulp, grunt, broccoli, e etc)
2. Como Loader do [webpack](https://webpack.github.io/)
3. Como CLI (Command Line Interface)
4. Como API

## Plugin de Taskrunners
Dentro desse contexto, ele é considerado apenas mais uma tarefa dentro do pipeline de execução.

`npm install gulp gulp-postcss autoprefixer`

```js
const gulp = require('gulp')
const postcss = require('gulp-postcss')
const autoprefixer = require('autoprefixer')

gulp.task('css', () => {
  return gulp.src('src/**/*.css')
    .pipe( postcss( autoprefixer ) )
    .pipe( gulp.dest('build/') );
});
```

## Loader do Webpack
Ele funciona como qualquer outro loader de arquivo:

`npm install webpack style-loader css-loader postcss-loader autoprefixer`

```js
module.exports = () => {
  module: {
    loaders: [{
      test: /\.css$/,
      loader: 'style-loader!css-loader!postcss-loader' // Os loaders comuns de css para o webpack ainda são obrigatórios.
    }]
  }
}
```

## CLI
Geralmente útil quando utilizando em conjunto com [npm scripts](https://docs.npmjs.com/misc/scripts):

`npm install postcss-cli autoprefixer`

```bash
postcss -c config.json
```

```javascript
// config.json
{
  "use": ["autoprefixer"],
  "input": "screen.css",
  "output": "bundle.css",
  "autoprefixer": {
    "browsers": "> 5%"
  }
}
```

_O arquivo de configuração serve para passar as opções gerais para o postcss. é possível utilizar a cli sem ele, mas fica bem verboso._

## Como API
O PostCSS disponibiliza alguns métodos para trabalhar com arquivos CSS [conforme dito no capítulo anterior](plugins.md), isso significa que podemos levar ele para qualquer cenário JS:

`npm install postcss autoprefixer`

```javascript
const fs = require('fs')
const postcss = require('postcss')
const autoprefixer = require('autoprefixer')
const file = fs.readFileSync('src/app.css')

postcss([ autoprefixer ])
  .process(file)
  .then(function (result) {
    fs.writeFileSync('app.css', result.css);
  });
```

## Instalando Plugins

Um ponto interessante de ser notado, é que por mais que você instale "versões" diferentes do PostCSS para cada contexto que você for utilizar. Seja um taskrunner (gulp-postcss), um loader (postcss-loader), etc. Os plugins do PostCSS sempre são os mesmos. Você não os instala baseado no contexto, eles são exclusivos do PostCSS, e funcionam em qualquer lugar onde ele funciona.

Conforme dito antes, o PostCSS só processa os arquivos pelo pipeline, não adiciona nada neles. Quem se responsabiliza por isso são os [plugins](http://postcss.parts/).


Próximo tópico: [Features básicas](basics.md)
