# Criando Projeto
Vamos usar o `npx` para criar o projeto. Esse comando baixa temporariamente as bibliotecas que precisa para executar os comandos e depois automaticamente desinstala elas.
~~~
$ npx create-react-app nome-do-projeto
~~~
# Exibindo string na tela
Vamos usar a dependência ReactDOM para exibir rendenizar informações na tela.
~~~jsx
import ReactDOM from 'react-dom'

const componente = document.getElementById('id')
ReactDOM.render('string que vai ser rendenizada', componente)
~~~
Importante ressaltar que aqui estamos usando só o próprio javascript, não estamos usando o react ainda.
# JSX
Usando o método anterior não é possível colocar o texto rendenizado dentro de uma tag HTML. Por isso, usa-se a sintaxe JSX.

A sintaxe JSX se parece com HTML, mas na realidade ela faz uma conversão disso para código javascript. Para usar o JSX, temos sempre que importar a biblioteca do React.

Para usarmos o código anterior com JSX construímos o código da seguinte forma:
~~~jsx
import ReactDOM from 'react-dom'
import React from 'react'

ReactDOM.render(
	<div>Olá React!</div>,
	document.getElementById('root')
)
~~~
Portanto, usamos o JSX para poder escrever um código semelhante ao HTML no react. O import do React tem que ser do exato modo que está escrito acima, se usar outro nome dará erro.
# Referenciando arquivo CSS
Primeiramente cria-se um arquivo `css`. Assim, temos que importar o arquivo:
~~~jsx
import './index.css'
~~~
Dentro do arquivo `css` criamos o estilo do modo de sempre.
# Criando componentes
Cria-se uma pasta chamada *components* e dentro dela cria-se pastas para cada componente. Então cria-se o arquivo `js` ou `jsx` (do ponto de vista do react não faz diferença ser `js` ou `jsx`) do componente:
~~~jsx
export default function Component () {
	return 'Ola Mundo';
}
~~~
Observe que é necessário exportar o componente com o export default. Agora no arquivo principal é preciso importar o componente e referenciá-lo através de tags (o JSX trata os componentes como tags semelhantes ao HTML):
~~~jsx
import Component from 'caminho/do/arquivo'

ReactDOM.render(
	<div>
		<Component></Component>
	</div>,
	document.getElementById('id')
)
~~~
No HTML podemos chamar o componente da forma mostrada acima como usando só uma tag: `<Component/>`.

Pode-se usar JSX dentro do component também:
~~~jsx
import React from 'react';  
  
<<<<<<< HEAD
export default function Primeiro(){  
=======
export default  function Primeiro(){  
>>>>>>> 4f0f45b2b323508e4b22a0ac405aa8e60e0f4d9f
    const msg = 'Seja bem-vindo(a)'  
    return(  
        <div>  
            <h1>Primeiro Componente</h1>  
            <p>{msg}</p>  
        </div>  
    )  
}
~~~
Repare que podemos usar uma variável ou constante dentro da sintaxe JSX se usarmos as chaves.

Os componentes apresentados nessa seção são denominados funcionais, pois eles se baseiam em funções.
# Componentes com Propriedades
Aqui queremos criar componentes com parâmetros, ou seja, igual para HTML passamos parâmetros como o id dentro da tag, faremos o mesmo no `JSX`. Primeiro passo é criar o arquivo do componente. Em seguida, vamos criar o componente em si:
~~~jsx
import React from 'react';  
  
export default function ComParametro(props) {   
    return(  
        <div>  
            <h2>{props.titulo}</h2>  
            <h3>{props.subtitulo}</h3>  
        </div>  
    )  
}
~~~
E dentro do arquivo principal, depois de importar o componente, referenciamos ele:
~~~jsx
<ComParametro titulo="Segundo Componente" subtitulo="Muito Legal!"  
/>
~~~
No React é padronizado usar o `props` para referenciar os parâmetros, onde `props` vem de propriedades.

Pode-se atribuir o valor de um parâmetro à uma variável e passar ela no return.

Importante mencionar que no arquivo principal, quando for passar o parâmetro, usa-se as chaves quando o valor não é uma string, então se for um número ou então uma variável é preciso passá-lo entre chaves e não entre aspas.

Agora, podemos ver o principal objetivo de utilizar componentes: reutilização. Visto que, como podemos passar parâmetros, é possível criar um componente básico e só mudar alguns dos seus valores através dos parâmetros.

As propriedades que são passadas como parâmetros são somente de leitura. Se tentar alterar o valor delas dará um erro.
# React Fragment
Veremos agora um erro conhecido como componentes `jsx` adjacentes que ocorre quando tentamos retornar dois elementos sem que haja algo envolvendo ambos. Veja um exemplo de um código que resultaria nesse erro:
~~~jsx
ReactDOM.render(   
	<Primeiro></Primeiro>  
	<ComParametro titulo="Segundo Componente" subtitulo="Muito Legal!"  
	/>,   
    el  
)
~~~
Veja que temos dois componentes adjacentes sendo retornados.

Para resolver esse problema usamos o `jsx fragment`:
~~~jsx
import React from 'react'

export default function Fragmento(props){
	return(
		<React.Fragment>
			<h2>Fragmento</h2>
			<p>Cuidado com esse erro</p>
		</React.Fragment>
	)
}
~~~
Nessa resolução, quando inspecionarmos o código no navegador veremos que não tem nenhuma tag envolvendo o componente. Uma outra sintaxe para o `jsx fragment` é:
~~~jsx
import React from 'react'

export default function Fragmento(props){
	return(
		<>
			<h2>Fragmento</h2>
			<p>Cuidado com esse erro</p>
		</>
	)
}
~~~
A diferença entre as duas sintaxes é que na tag com o react fragment escrito é possível passar parâmetros, já na tag vazia não é possível passar parâmetro.

Uma outra solução é simplesmente envolver o componente em uma div.
# Componente App
No React usamos o componente App para criar, da forma mais enxuta, um componente funcional, usando uma arrow function. Primeiramente cria-se um componente chamado `App`. O código dele é:
~~~jsx
import React from 'react';

export default () => {
	return(
		...
	);
}
~~~
Assim, no `index.js` importamos somente o `App.js` e assim para atualizar a aplicação é necessário atualizar o `App.js`. Tem como fazer de forma mais reduzida, deixando somente o export default _ => e ai tirar as chaves e o corpo da função, deixando somente o código JSX.
# Componente Card
~~~jsx
import React from 'react';

export default (props) => {
	return (
		<div className='Card'>
			<div className='Title'>{props.titulo}</div>
			<div className='Content'>Conteúdo</div>
		</div>
	);
}
~~~
Usa-se className porque o javascript tem a palavra reservada class.

~~~css
.Card{
	background-color: red;
	border: 3px solid red;
	border-radius: 10px;
	overflow: hidden
}

.Card .Title {
	padding: 10px 0px;
	 
}

.Card .Content {
	background-color: #fff;
	color: #000;
}
~~~
Se passarmos um componente dentro do Card, nós podemos referenciar ele usando o `props.children`, então se dentro do card tiver um `<p>` podemos usar o props.children para referenciá-los dentro do componente. Importante ressaltar que o props.children devem estar dentro de chaves.
## Flexbox
Podemos usar o flexbox para mudar a organização dos elementos na tela, de modo que quando a tela é grande eles ficam todos na mesma linha, mas se for pequena ficam um embaixo do outro.
~~~css
display: flex -> Habilita o flexbox
flex-direction: column
flex-grow: 1 -> faz ocupar todo o espaço
flex-wrap: wrap -> ele quebra a linha conforme o tamanho da tela
~~~
# React Router
Usaremos a biblioteca `react-router-dom`, ela serve para navegar entre telas. Uma vez instalada a biblioteca, para fazer navegação entre páginas podemos fazer o seguinte código no `App.jsx`:
~~~jsx

import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';

function App() {
	return(
		<Router>
			<Routes>
				<Route path='caminho da url, exemplos: /, /sobre, /login' element={<TagDoElemento/>} />
				...
			</Routes>
		</Router>
	);
}
~~~
E dentro de cada elemento, para mudar de tela, usamos a tag `Link`:
~~~jsx
import { Link } from 'react-router-dom';

const Element = () => {
	return(
		<button className="button-primary">
			<Link to="/planos" >Assine o plano</Link>
		</button>
	);
}
~~~