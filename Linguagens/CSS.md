# Introdução
Cascading Style Sheets ou CSS é uma linguagem usada para especificar a aparência e formato da página web. Ela separa o conteúdo da apresentação. Alguns dos motivos para usar CSS são: reutilização e facilita manutenção.

Para usar o CSS usa-se ou a tag `<style>` para escrever o CSS dentro do arquivo HTML ou então a tag `<link>` para linkar com o arquivo CSS.
# Estrutura
~~~CSS
seletor {
	propriedade1: valor1;
	propriedade2: valor2;
	...
}
~~~
O seletor especifica o elemento que queremos estilizar. Ele pode ser tanto uma tag do HTML quanto uma classe ou ID.
## Classes
É uma forma de estilizar somente alguns determinados elementos. É preciso adicionar um atributo na tag HTML:
~~~HTML
<li class="item"> Valor1 </li>
<li class="item"> Valor2 </li>
<li> Valor3 </li>
~~~
Agora temos que estilizar com CSS:
~~~CSS
.item {
	color: green;
}
~~~
Assim, somente os dois primeiros valores vão ficar verde e o último vai ficar a cor padrão. É importante mencionar que as classes podem ser usadas para diversos elementos.
## ID
É uma forma de estilizar somente um elementos. É preciso adicionar um atributo na tag HTML:
~~~HTML
<li id="item"> Valor1 </li>
<li > Valor2 </li>
<li> Valor3 </li>
~~~
Agora temos que estilizar com CSS:
~~~CSS
#item {
	color: green;
}
~~~
Assim, somente primeiro valor vai ficar verde e o resto vai ficar a cor padrão. É importante mencionar que o ID pode ser usado somente para um elemento
## Combinators
São usados para selecionar elementos a partir da relação entre eles. Por exemplo, para selecionar somente imagens dentro de links usamos o seguinte código no CSS:
~~~CSS
a img {
	...
}
~~~