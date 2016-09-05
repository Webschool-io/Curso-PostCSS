# Separação de Arquivos

A estruturação/separação de arquivos é muito flexível dentro do PostCSS, por abusar dos [módulos do Node](https://nodejs.org/api/modules.html).

Para este tópico, iremos nos basear no plugin [import](https://github.com/postcss/postcss-import), mas sem nos aprofundarmos em todas as possibilidades dele (Por fugirem um pouco do escopo inicial do que é CSS).

A separação contribui bastante para uma boa manutenção do nosso código CSS, e na maior parte do tempo irá variar de acordo com a preferência/metodologia aplicada no projeto.

Para usufruirmos desse benefício, o PostCSS cuida do `@import` para nós. Vale notar que não é o `@import` nativo do CSS nesse caso. O PostCSS identifica a regra `@import`, e injeta o arquivo para nós. Por exemplo:

```sass
// base.css

html, body {
 height: 100%;
}

// main.css
@import "base" // note que não é necessário a extensão .css, O PostCSS lida com isso para nós.

.link {
 text-decoration: none;
}

// resultado
html, body {
 height: 100%;
}

.link {
 text-decoration: none;
}
```

Inicialmente, o PostCSS irá definir como base para buscar as folhas de estilo a partir do (process.cwd()), mas isso pode ser mudado nas configurações do plugin.

Por utilizarmos o conceito de módulos do Node nesse plugin, é possível navegarmos pelas pastas do projeto, ou até mesmo da `node-modules` para importarmos uma folha de estilos.

Próximo tópico: [Condicionais](conditionals.md)
