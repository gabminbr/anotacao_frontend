# CSS
## a regra CSS
- Toda regra CSS é como uma instrução que você dá ao navegador. Ela tem duas partes principais: o Seletor e o Bloco de Declaração.
```css
/* Isso é um comentário em CSS */

seletor {
  propriedade: valor;
  outra-propriedade: outro-valor;
}
```
```
Seletor: Aponta para o elemento HTML que você quer estilizar. No exemplo h1, estamos selecionando todos os elementos <h1>.
Bloco de Declaração: Fica entre chaves {} e contém uma ou mais declarações.
Declaração: Consiste em uma propriedade e um valor, separados por dois pontos (:), e terminados com um ponto e vírgula (;).
  Propriedade: É o atributo de estilo que você quer alterar (ex: color, font-size).
  Valor: É o valor que você quer atribuir àquela propriedade (ex: blue, 24px).
```
- exemplo prático:
```css
h1 {
  color: #3498db; /* Define a cor do texto para um tom de azul */
  font-size: 32px;  /* Define o tamanho da fonte para 32 pixels */
}

p {
  color: #555555; /* Define a cor do texto para um cinza escuro */
  line-height: 1.6; /* Aumenta o espaçamento entre as linhas do parágrafo */
}
```

## seletores
### seletores básicos
- **Seletor de Tipo (ou de Elemento/Tag)**: seleciona todos os elementos de um determinado tipo de tag HTML:
```css
p {
  color: #555555;
  line-height: 1.6;
}
```
- **Seletor de classe**: Seleciona todos os elementos que possuem um determinado atributo class. Este é o seletor mais versátil e útil.]
- sintaxe: .nome-da-classe
- IMPORTANTE: podemos adicionar a um elemento html mais de uma classe, basta separar por um espaço em branco (space) e digitar a classe, assim ele vai ter os atributos de ambas
- exemplo (no html e css respectivamente):
- 
```html
<title class = "titulo-da-pagina">Site teste</title>
<div class = "titulo-da-pagina">Olaaaaaa</div>
```

```css
.titulo-da-pagina{
  color: black;
  font-family;
}
```
- **Seletor de ID**: Seleciona um único elemento que possui um determinado atributo id.
- REGRA: Um id deve ser único em toda a página. Não pode haver dois elementos com o mesmo id. Use-o para elementos estruturais principais como cabeçalho, rodapé ou menu principal.
- sintaxe: #nome-do-id (note a cerquilha/hashtag no início)
- exemplo (html - css):
```html
<header id="cabecalho-principal">...</header>
```

```css
#cabecalho-principal{
  width: 100%;
  background-color: #333;
  color: white;
}
```
- class vs id: Use class para estilos que você quer reutilizar em vários elementos. Use id para um elemento único e específico.

- **Seletor de Atributo**: Seleciona elementos com base na presença ou valor de um de seus atributos.
- Sintaxe: [atributo], [atributo="valor"], e outras variações.
- exemplo (html - css):

```html
<a href="pagina_interna.html">Link Interno</a>
<a href="https://google.com" target="_blank">Google</a>
<input type="text" placeholder="Seu nome">
<input type="submit" value="Enviar">
```

```css
/* Seleciona todos os links que abrem em uma nova aba */
a[target="_blank"] {
  font-style: italic;
}

/* Seleciona apenas o input do tipo "submit" */
input[type="submit"] {
  background-color: green;
  color: white;
}
```

- **Seletor universal**: Seleciona absolutamente todos os elementos da página.
- Sintaxe: *
- exemplo:
```css
/* Zera margens e paddings de todos os elementos */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box; /* Uma propriedade muito útil que veremos em breve */
}
```

- **Grouping selector**: quando por exemplo, temos duas classes que se parecem muito e têm muitos atributos em comum, podemos meio que economizar linha dessa forma:
- antes:
```css
.read {
  color: white;
  background-color: black;
  /* several unique declarations */
}

.unread {
  color: white;
  background-color: rgb(100, 0, 0);
  /* several unique declarations */
}
```
- depois:
```css
.read,
.unread {
  color: white;
  background-color: black;
}

.read {
  /* several unique declarations */
}

.unread {
  /* several unique declarations */
}
```

## Adicionando CSS ao HTML
### CSS externo
- é o mais comum, basicamente criaremos o css num arquivo separado e linkaremos dentro do atributo <head> do HTML.
- uso:
```html
<!-- index.html -->

<head>
  <link rel="stylesheet" href="styles.css">
</head>
```
```css
/* styles.css */

div {
  color: white;
  background-color: black;
}

p {
  color: red;
}
```
### CSS interno
- basicamente, faremos o css dentro do documento html, usando o seletor <style> .. </style>
```html
<head>
  <style>
    div {
      color: white;
      background-color: black;
    }

    p {
      color: red;
    }
  </style>
</head>
<body>
  ...
</body>
```
### CSS inline
- fazer o css dentro do elemento
```html
<body>
  <div style="color: white; background-color: black;">...</div>
</body>
```
