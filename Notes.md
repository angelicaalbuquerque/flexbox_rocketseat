## Layouts CSS

Layout tem a ver com a maneira que os elementos estão distribuídos na tala.

### Normal flow

O Flow Layout é a meneira que os elementos `block` e `inline` ficam na págna.

```HTML
<p> Texto block com <strong>inline</strong> dentro.</p>
```

### Table

Maneira de tabelas onde a tag `table` recebe um display `table`, fazendo com que os elementos internos, como `td` e `tr`, possam ser usados para montar uma tabela.

```HTML
<table>
  <tr>
    <td>Hora</td>
    <td>20h</td>
  </tr>
  <tr>
    <td>Hora</td>
    <td>20h34</td>
  </tr>
</table>
```

### Tableless

É a ideia de não usar só tabela para posicionar os elementos.

Surgiu com a evolução do layout, trazendo o uso das propriedade `float` e `clear` para que os elementos possam mudar de posição na tela.

A `div`, por padrão, tem display block e fica disposta como linhas de uma tabela. Utilizando "tabless", eu removo que fiquem uma abaixo da outra. Para continuar com o flow normal, tenho que aplicar `clear: both`.

```HTML
<div style="float: left">esquerda</div>
<div style="float: right">direita</div>
<div style="clear: both">normal flow</div>
```

### Flexbox

Aplicando o display flex, a caixa se torna flex e faz com que os elementos internos possam receber melhor alinhamento, ordenação e tamanhos flexíveis.

```HTML
<div class="flexbox">
  <div class="item">A</div>
  <div class="item">B</div>
  <div class="item">C</div>
</div>
```

```CSS
.flexbox {
  display: flex;
}
```

## Terminologia

### Flex container, Flex item e Nesting

Container significa "algo que contém", ou seja, uma caixa com elementos dentro.

No caso abaixo, temos o flex container na classe "container" (quando aplicado display flex) e os flex items, na classe "item".

```html
<div class="container">
  <div class="item">A</div>
  <div class="item">B</div>
  <div class="item">C</div>
</div>
```

O conceito de **nesting** é de que elementos vivem dentro de outro elemento.

### Eixo principal e cruzado

Flexbox também tem eixos (axis), que são chamados de main (principal) e cross (cruzado), sendo start o começo e end o final.

Isso significa que ao utilizar um elemento com `display: flex;`, eu posso mudar o comportamento do eixo principal com o cruzado, utilizando, por exemplo, `flex-direction: column` no lugar de "row".

Posso também alinhar o conteúdo utilizando `justify-content: flex-end`.

### Flex sizing

Significa o item ser flexível, ou seja, vai alterar a largura e a altura dos itens para que haja um preenchimento dos espaços do flex container.

Utilizar flex-sizing com `flex: 1`: preenche os espaços do container, ajustando completamente a largura e altura dos elementos conforme a tela do usuário.

[Ver exemplo](https://codepen.io/frontangie/pen/NWgoVJK)

```HTML
<div class="container">
  <div class="item">A</div>
  <div class="item">B</div>
  <div class="item">C</div>
</div>
```

```CSS
.container {
  display: flex;
  border: 1px solid red;
  height: 80vh;
}

.item {
  background-color: gray;
  border: 1px solid;
  flex: 1;
}
```

## Propriedades do Flex Container

Temos agora as seguintes possibilidades adicionadas ao flex container, ao defini-lo como `display: flex`:

- Direção dos itens;
- Multilinhas;
- Alinhamento principal e cruzado;
- Espaços entre os itens.

### Direção dos itens

Flex é uma dimensão somente, ou vai inserir os itens na horizontal ou na vertical.

Podemos mudar a direção com `flex-direction`, tendo os seguintes valores:

- row (linha) | row-reverse (linha reversa) | column (coluna) | column-reverse (coluna reversa)

No exemplo abaixo, aplicando `flex-direction: row-reverse`, mudo a leitura dos itens de A-B-C para C-B-A:

```HTML
<div class="container">
  <div class="item">A</div>
  <div class="item">B</div>
  <div class="item">C</div>
</div>
```

```CSS
.container {
  display: flex;
  border: 1px solid red;
  height: 80vh;
  flex-direction: row-reverse;
}
```

É importante lembrar que toda vez que é aplicado o flex-direction qualquer outra propriedade aplicada também será impactada.

### Múltiplas linhas

`flex-wrap` é a capacidade de usar multilinhas. Cada nova linha é um novo eixo sendo criado, como novo flex container.

Se tiver o tamanho suficiente para o conteudo ser exibido, essas linhas não é criada. Mas se não tiver, acontece essa "quebra de linha", resultando na criação de mais uma.

```HTML
<div class="box">
  <div class="item">A</div>
  <div class="item">B</div>
  <div class="item">C</div>
  <div class="item">D</div>
</div>
```

```CSS
.box {
  display: flex;
  flex-wrap: wrap;

  border: 1px dashed red;
}

.box div {
  border: 1px solid;
  width: 80px;
}
```

Se eu aplicar flex-wrap: reverse, o encaixe é feito na tela de maneira reversa, como D C B A.

### Direção e multi linha em uma única propriedade

`flex-flow` é um shorthand, uma maneira curta de escrever as propriedades `flex-direction` e `flex-wrap`.

```CSS
.box {
  display: flex;
  flex-flow: column wrap;

  border: 1px dashed red;
}

.box div {
  border: 1px solid;
  width: 80px;
}
```

### Alinhamento dos itens no eixo principal

#### justify-content

- Alinhamento dos elementos dentro do container;
- Distribuição dos elementos.

**valores**:

- flex-start;
- flex-end;
- space-around (espaço por igual ao redor);
- space-between (espaço por igual entre eles);
- space-evenly (espaço por igual em cada um deles, desde o começo ao final).

### Alinhamento dos itens no eixo cruzado

#### align-items

- Alinhamento dos elementos no eixo cruzado.

**valores**:

- stretch (padrão);
- flex-start;
- flex-end;
- center.

### Espaço entre os elementos

A propriedade `gap` nos permite colocar espaços [somente] entre os elementos.

Seus valores são unidades de medidas:

- fixas: px, pt;
- flexives: %, em, rem.

```HTML
<div class="box">
  <div>A</div>
  <div>B</div>
  <div>C</div>
  <div>D</div>
</div>
```

```CSS
.box {
  border: 1px dashed red;

  display: flex;
  justify-content: center;
  gap: 2em;
}

.box div {
  border: 1px solid;
}
```

## Propriedades para os itens

### Propriedades para os itens

### Largura e altura dos itens com flex-basis

### Crescimento e adaptação dos itens

### Encolhimento e encaixe dos elementos

### Shorthand flex

### Alterando tamanho de múltiplos itens

### Ordenando itens

## Desafios

### Header menu navigation

### Layout com 2 colunas

### 9 fotos 3 colunas

### Imagem dentro de um botão

### Footer
