# Introdução
*HyperText Markup Language* ou HTML é a linguagem usada para criar páginas web. Ela não é uma linguagem de programação e sim uma linguagem de marcação. Ele faz o uso de *tags* para mostrar para o navegador como carregar o conteúdo.

Com o HTML que é mostrado ao navegador o conteúdo da página web. Além disso, o HTML expressa significado/semântica.

Para que os navegadores entendam o HTML, é preciso que haja um padrão. O padrão mais atual é o HTML5. 
# Estrutura
O arquivo HTML pode ser dividido em duas partes principais, de acordo com os diferentes tipos de elementos da linguagem: elementos de metadados e elementos de seção.
## Elementos de metadados
Eles trazem informações sobre a página HTML em si. Alguns exemplos de tags de metadados são: `<html>`, `<title>`,`<head>`.
## Elementos de seção
Esses elementos definem regiões das páginas. Alguns exemplos de tags de seção são: `<body>`, `<h1>`, `<div>`.
# Tags
Vamos agora estudar a linguagem em si, ou seja, vamos ver as *tags*.
## Tags de Metadados
### HTML
~~~HTML
<hmtl>
</html>
~~~
Essa tag indica que usamos HTML para representar os componentes da página web. A página web será definida entre as tags `<html>`, ou seja, ela contém todos os elementos da página. Essa tag também especifica que o padrão usado pela página será o HTML.
### Head
~~~html
<head>
</head>
~~~
Essa tag contém os elementos que trazem informações gerais sobre a página, como scripts, título, css, entre outros.
### Title
~~~HTML
<title></title>
~~~
Essa tag indica o nome que aparecerá na aba do navegador. Ele deve estar entre as tags do `<head>`.
## Tags de Seção
### Body
~~~html
<body>
</body>
~~~
Essa tag indica que todo conteúdo dela será o corpo da página, ou seja, será o conteúdo mostrado na página.
### Header
~~~html
<h1></h1>
~~~
Ele é um header de seção. Ele terá um destaque maior (tanto de tamanho quanto de espessura). Existem também `h2`, `h3`, ..., `h6`, sendo que ele é o último e menor.
### Paragraph
~~~html
<p></p>
~~~
Essa tag representa um parágrafo, um texto que aparecerá na página.
### Div
~~~html
<div>
</div>
~~~
Essa tag representa uma seção, uma divisão, da página web. Ela é útil para agrupar elementos para o CSS.
## Tags de Semântica ou Estilo
Essas tags ficam ao redor de textos ou elementos da página.
### Bold
~~~HTML
<b></b>
~~~
Essa tag deixa o texto em negrito ou então com um estilo diferente do resto do texto
### Emphasize
~~~html
<em></em>
~~~
Essa tag é usada para enfatizar o texto, deixando-o estilisticamente diferente do resto do texto e é usada para auxiliar leitores de telas ou outros dispositivos de acessibilidade.
## Tags de Imagem e Multimídia
Páginas web podem incluir imagens, vídeos, audios, entre outros. Cada um desses formatos terá sua própria tag.
### Image
~~~html
<img src="link da imagem" width="porcentagem do tamanho dela"/>
~~~
Essa tag adiciona uma imagem no site. A opção *width* é opcional, já a *src* é obrigatória. Essa tag não tem uma tag de fim.
### Anchor
~~~html
<a href="link do site">texto que aparecerá no site</a>
~~~
Essa tag transforma o texto entre ela em um link para um site. Ele tem o atributo *href* que especifica o site para qual será direcionado. O texto entre a tag é obrigatório. Ele é um texto clicável.

## Tags de Listas e Tabelas
### Unordered List
~~~html
<ul></ul>
~~~
Essa tag cria listas sem ordem, que utiliza círculos, pontos, entre outros. O estilo dos pontos pode ser alterado com CSS.
### Ordered Lists
~~~html
<ol></ol>
~~~
Essa tag cria listas ordenadas.
### List Item
~~~HTML
<li></li>
~~~
Essa tag cria os elementos da lista, ou seja, cada item que estará na lista terá que estar entre uma tag dessa. Essa tag deve estar dentro da tag `ul` ou `ol`.
### Tables
As informações são organizadas em linhas e colunas.
~~~html
<table>
	<tr> table row
		<th></th> table header
		<th></th> table header
		<th></th> table header
	</tr>
	<tr>
		<td></td> table cells
		<td></td>
		<td></td>
	</tr>
	<tr>
		<td></td>
		<td></td>
		<td></td>
	</tr>
</table>
~~~