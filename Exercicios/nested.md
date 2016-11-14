# Exercício do tema Nested

### O objetivo é otimizar o seguinte trecho de CSS com o conteúdo da aula

```scss
.form {
  overflow: auto;
}

.form .button,
.form .input {
  width: 50%;
  float: left;
}

.button {
 background-color: $colorDefault;
 color: white;
 font-size: $defaultFontSize;
 font-weight: 600;
}

.button:hover {
 opacity: .8;
}

.input {
 border: 1px solid $colorDefault;
 color: black;
 font-size: $defaultFontSize;
 font-weight: 600;
}

.input:focus {
 color: $colorDefault;
}

.input-password {
  border: red;
}

@media screen and (min-width: 600px) {
  .form .button,
  .form .input {
    width: 100%;
  }
}

```
