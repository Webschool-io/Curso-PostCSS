# Como um plugin funciona

Como dito já no tópico inicial, o PostCSS trabalha com plugins JavaScript. Isso é, um monte de funcoes básicas que já conhecemos, para alterar o objeto referente a folha de estilos.

Todos os plugins precisam ser executados de maneira síncrona, para garantir a ordem de execucao dos plugins. Um exemplo prático disso, é o plugin de variáveis. Este plugin precisa de fato ser executado antes que diversos outros plugins, já que eles podem consumir variáveis também.

Pensando um pouco mais em código, podemos imaginar um plugin que faz o cálculo de `rem` para `px` da seguinte maneira:

```javascript
// Por hora vamos desconsiderar a comunicacao entre o PostCSS e o plugin, e focar em como ele modifica a folha de estilos
...
// O argumento css é o objeto referente a folha de estilos, com uma série de métodos disponibilizados pelo PostCSS para facilitar a transformacao dele

(css) => {
 // walkDecl é um método que possibilita iterar por cada declaracao encontrada no objeto.
 css.walkDecl(decl => {
   // O valor da declaracao é o valor definido na própria declaracao no arquivo css.
   decl.value = decl.value.replace(/\d+rem/, rem => 16 * parseFloat(rem) + 'px')
   
   // Vale notar que o processamento da folha de estilos é inteligente, geralmente o próprio PostCSS insere a unidade baseada no contexto dela, mas como queremos explicitamente transformar em `px`, fazemos isso manualmente.
 })
}
...
```

Na maior parte do tempo, iremos utilizar plugins prontos, mas é sempre importante entender como a ferramenta funciona, para nos trazer mais confianca em nossos projetos, caso algo precise ser modificado.

Próximo tópico: [Como utilizar](how.md)

