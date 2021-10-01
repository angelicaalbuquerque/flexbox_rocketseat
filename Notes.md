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

- flex-basis (serve para mudar o tamanho do item);
- flex-grow (adapta e faz o item crescer automaticamente);
- flex-shrink (faz o item encurtar/comprimir ou ficar menor, dependendo do tamanho da caixa);
- flex (shorthand para os tres acima);
- order (como ordenar elementos).

### Largura e altura dos itens com flex-basis

Por padrão, o flex-basis é auto, ou seja, pega o tamanho dos elementos e deixa automático. Eu posso, por exemplo, em vez de utilizar `width: 25px` para definir a largura, posso fazer essa definição via `flex-basis: 25px`.

Agora, perceba que se eu quiser pegar um elemento só e aplicar a largura de 2500px, não consigo porque o flex-basis já faz o controle com 15%. Só funcionaria se eu deixasse como auto o flex-basis.

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
}

.box div {
  border: 1px solid;
  flex-basis: 15%;
}

.box div:nth-child(1) {
  width: 2500px;
}
```

Ponto de atenção: se mudar a direção para coluna, o fle-basis não signifca mais a largura, significa se eu colocar 50px a caixa vai aumentar de altura e se eu quiser usar 400px no primeiro filho, não vou conseguir pois o flex-basis já tomou pra si essa responsabilidade de aplicar 50px (a não ser que eu deixe auto):

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
}

.box div {
  border: 1px solid;
  flex-basis: 50px;
}

.box div:nth-child(1) {
  width: 25px;
  height: 400px;
}
```

### Crescimento e adaptação dos itens

`flex-grow` é o crescimento do item dentro do container em relação aos espaços vazios.

Por exemplo, se eu quiser que o item C tome conta de todo o espaço vazio, faço da seguinte forma:

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
}

.box div {
  border: 1px solid;
}

.box div:nth-child(3) {
  flex-grow: 1;
}
```

Esse "1" significa "pega todo o espaço e aplique o alongamento". Mas se eu aplicar a outro elemento, ao elemento C, por exemplo, esse "1"/esse espaço vazio é dividido um pedaço para um e um pedaço para outro.

Ou seja, a distribuição é feita conforme os elementos que estamos aplicando.

### Encolhimento e encaixe dos elementos

`flex-shrink` é a capacidade do item encolher dentro do container.

Se eu coloco o `flex-shrink: 0`, significa que eu não quero que o elemento seja encurtado mais.

### Shorthand flex

A propriedade `flex` é um atalho para:

- flex-grow;
- flex-shrink;
- flex-basis.

Ela pode receber 1, 2 ou 3 valores (na ordem acima), como no [exemplo](https://codepen.io/frontangie/pen/dyRrbBK).

### Alterando tamanho de múltiplos itens

Aplicação da propriedade flex, vista acima, em diversos elementos.

Código [aqui](https://codepen.io/frontangie/pen/JjJzjGL), que prova que o flex-basis dá mais força às caixas. Se não existe basis, podemos trabalhar com as adaptações (grow e shrink).

### Ordenando itens

Por padrão, "order" é 0. Mas se mudamos essa ordem, por exemplo, para "1", como é maior que 0 esse elemento vai para o final da lista.

Podemos usar também números negativos. No exemplo abaixo, o "D" que era o 4º item vai para a primeira posição por receber "-1".

Detalhe: muda visualmente, mas não estruturalmente (no código).

[Exemplo](https://codepen.io/frontangie/pen/zYzbYKP?editors=1100).

## Desafios

### Header menu navigation

- Crie o `<header>` de um site que contenha uma logo e um menu.
- Um elemento deverá ficar ao lado do outro.
- A logo que ficará na extrema esquerda e o menu na extrema direita.
- Os itens do menu ficarão um ao lado do outro, com um espaço de .8rem entre eles.
- O último elemento do menu será um botão de contato e você poderá utilizar o seletor `:last-child` para estilizar.

[Ver o exercício aqui](https://codepen.io/frontangie/pen/GRELqaK?editors=1100).

### Layout com 2 colunas

- Crie um layout com 2 colunas, uma ao lado da outra.
- A coluna da esquerda deverá ter 25% de tamanho e a coluna da direita deverá ocupar todo o espaço que sobra.
- Faça uma separação de 1rem entre os elementos.

[Ver o exercício aqui](https://codepen.io/frontangie/pen/eYRozqy?editors=1100).

### 9 fotos, 3 colunas

- Crie uma galeria de fotos onde teremos 3 colunas e 9 fotos.
- Deixe um espaço de .8rem entre os elementos da galeria.

[Ver o exercício aqui](https://codepen.io/frontangie/pen/PojgGZZ?editors=1100).

### Imagem dentro de um botão

- Crie um botão que contenha um ícone (img) e um texto.
- Coloeque um espaço de .4rem entre os elementos.

[Ver o exercício aqui](https://codepen.io/frontangie/pen/VwWNKmo).

### Footer

- Crie o `<footer>` de um site que contenha a data de criação do site.
- Usando flex, alinhe o elemento do footer bem ao meio.
- Deixe uma altura de 8rem para o footer.
- O footer deverá ficar no final da página.

[Ver o exercício aqui](https://codepen.io/frontangie/pen/KKqYgqy?editors=1100).
