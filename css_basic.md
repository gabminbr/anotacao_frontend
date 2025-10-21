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
## Cascata
- sistema de regras e prioridades que o navegador usa para resolver conflitos quando mais de uma regra de estilo se aplica a um mesmo elemento.
### fator 1: Origem e Importância
- os estilos de uma página podem vir de 3 lugares diferentes:
```
- User-Agent (Navegador): Todo navegador (Chrome, Firefox, etc.) tem sua própria folha de estilos padrão. É por isso que, mesmo sem CSS nenhum, os links são azuis e sublinhados e os títulos <h1> são grandes e em negrito. Esta é a "lei" de menor peso.

- Author (Desenvolvedor): Este é o CSS que nós escrevemos. Nossos arquivos .css são as "leis" que criamos para o nosso site. Em condições normais, nossos estilos sempre prevalecem sobre os estilos padrão do navegador.

- User (Usuário): Alguns usuários, muitas vezes por questões de acessibilidade (como daltonismo ou baixa visão), podem ter sua própria folha de estilos personalizada para, por exemplo, forçar todas as fontes a serem maiores ou de maior contraste.
```
- a ordem de prioridade é Author -> User -> User-Agent
### fator 2: Especificidade
- uma declaração CSS mais específica, vai ter mais precedência que uma menos específica. O estilo inline por exemplo, tem mais especificidade que os seletores.
- Um seletor do tipo ID vai ser mais específico que um do tipo Classe que por sua vez vai ser mais do que os type selectores
- Quando não há uma precedência de seletores mais específicos que outros, o que vai valer vai ser o seletor que tiver mais elementos vai ter precedencia sobre o que tem menos:
```html
<!-- index.html -->

<div class="main">
  <div class="list subsection">Red text</div>
</div>
```
```css
/* rule 1 */
.subsection {
  color: blue;
}

/* rule 2 */
.main .list {
  color: red;
}
```
- a rule 2 vai ter precedencia
- agora outro exemplo:
```html
<!-- index.html -->

<div class="main">
  <div class="list" id="subsection">Blue text</div>
</div>
```
```css
/* rule 1 */
#subsection {
  color: blue;
}

/* rule 2 */
.main .list {
  color: red;
}
```
- a rule 1 vai ter precedencia, pois tem o seletor do tipo ID

## Box Model
- tudo no css é uma box, e devemos entender o que são o *padding*, *margin* e *border*.
```
padding: é o espaço entre a borda da caixa e o conteúdo dentro da caixa
border: como o nome diz, é a 'borda' da caixa, é o espaço entre o padding e o margin
margin: é o espaço entre as borders da caixa com as borders de outras caixas
```
- o box-sizing: (border-box) basicamente, ele vai fazer com que a soma content + padding + border tenha o tamanho que colocamos como width e height.
- já o content-box é o padrão, o content vai ter o mesmo tamanho que declaramos no width e height, entretanto, vai somar com padding e border, e no fim vai ser na tela algo maior que o tamanho do content q colocamos.
- exemplo:
```css
.box1 {
  box-sizing: border-box;
  color: rgb(0,0,0);
  width: 700px;
  margin: 30px;
  border: 20px solid black;
  padding: 30px;
}
```

## Block e Inline
- basicamente, block elements são aqueles que vao se agrupar como uma pilha, um embaixo do outro, tipo o <p></p>, <h1></h2>.
- temos o div, que basicamente vai servir como um container para agruparmos varios elementos que queremos colocar scripts ou css
- Divs allow us to divide the page into different blocks and apply styling to those blocks.
- já os inline elements, não vão começar em uma nova linha, eles vão aparecer na linha que for colocado, um exemplo é o de link, o <a></a>
- o display property, vai servir para transformar em inline ou block.
- button por exemplo, é um inline block, inline pq ele fica lado a lado do elemento na linha, e block pois pode colocar as properties como width e etc.
- para inline, temos um container também, que vai ser o span.

  ## FlexBox
- exemplo de uso:
```html
<div class="flex-container">
  <div class="one"></div>
  <div class="two"></div>
  <div class="three"></div>
</div>
```
```css
.flex-container {
  display: flex; 
}

/* this selector selects all divs inside of .flex-container */
.flex-container div {
  background: peachpuff;
  border: 4px solid brown;
  height: 100px;
  flex: 1; 
}
```
- flex containers e flex items: o flex container vai ser qualquer elemento que tiver a propriedade *display: flex*, já o flex item vai ser qualquer elemento que estiver dentro do flex container
- qualquer elemento pode se tornar um flex container, um flex item também pode ser um flex container
- a declaração *flex:...*: na verdade, essa propriedade é um atalho para definir 3 propriedades ao mesmo tempo:
```
- flex-grow: é o 'fator de crescimento' daquele flex item, ao usarmos 1, estamos dizendo para que o flex item se estique e ocupe o espaço disponível, e vai ser igualmente distribuído entre todos, mas ao usar
2 em um em especifico por exemplo, a proporcao ficaria dois items com tamanhos iguais, e um com o dobro.
- flex-shrink: é parecido com o grow, mas é o 'fator de encolhimento' do flex item, vai dizer o quão 'generoso' é cada item para aceitar perder espaço, 1 sendo o padrão que diz que todos irão encolher uniformemente,
o 0 especifica que aquele flex item não vai encolher e o 2 aceita encolher o dobro.
- flex-basis: define o tamanho inicial dos flex items, ao usar o auto, ele vai usar o tamanho width que foi especificado, se usarmos o 0 ele vai meio que 'zerar' todos os flex itens em tamanho e ir moldando de acordo
com as outras propriedades flex.
```
### Alignment
- para ajustar a disposição dos itens do container ao longo do eixo X, usamos a propriedade *justify-content*, e para o eixo Y usamos o *align-items*, esses eixos se baseiam no *flex-direction* do container flex, se muda o container para column, o justify muda o eixo Y e etc.
- **Gap**: adiciona um espaço específico entre os flex items, i.e: gap: 8px;

