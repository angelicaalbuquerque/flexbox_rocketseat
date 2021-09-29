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

### Flex container

### Flex item e Nesting

### Eixo principal e cruzado

### Flex sizing

## Propriedades do Flex Container

### Propriedades do Flex Container

### Direção dos itens

### Multiplas linhas

### Direção e multi linha em uma única propriedade

### Alinhamento dos itens no eixo principal

### Alinhamento dos itens no eixo cruzado

### Espaço entre os elementos

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
