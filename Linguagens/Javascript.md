É uma linguagem que foi criada para ser usada em páginas web, ele as torna dinâmicas. Quando uma página mostra em tempo real conteúdos atualizados, mapas interativos, animações gráficas em 2D/3D, vídeos, etc, você pode apostar que o javascript provavelmente está envolvido.

O javascript altera o DOM do HTML (DOM é a estrutura em árvores das páginas HTML, tem-se um nó (qualquer elemento do HTML é um nó) e seus filhos), ou seja, ele altera a estrutura do HTML, tornando as páginas dinâmicas.
# Tipos de Variáveis
O javascript possui dois tipos de variáveis principais: let e const. As variáveis do tipo let podem mudar de valor. Já as variáveis do tipo const são constantes. 

O javascript tem tipagem fraca (o javascript decide automaticamente o tipo das variáveis). Por causa disso, é necessário um cuidado, principalmente ao fazer comparações pois o javascript converte automaticamente (geralmente para número) os tipos de variáveis. Então em uma comparação tipo `' ' == 0` ele dará que é verdadeiro. Para evitar isso, pode-se utilizar `===` que é um operador de comparação que compara o tipo também.

Para concatenar textos com variáveis (tipo a fstring do python) usa-se as crases para escrever a string e o operador ${} para escrever a variável.

Para declarar uma variável usamos:
~~~js
var x = 1;

ou

let x = 1;

ou

const x = 1;
~~~
Quando usamos `new` para criar uma variável, estamos falando para o javascript que estamos criando um objeto. Um objeto é um dado que possui métodos com os quais pode ser operado. Métodos permitem realizar operações sobre objetos.
~~~js
var image = new SimpleImage('nome_da_imagem.png')
~~~

# Operador Ternário
É uma simplificação da estrutura if.
~~~js
if(condicao) return 0;
else return 1;

return condicao ? 0 : 1;
~~~
# Outros Operadores
Outro operadores importantes são: && e ||. O operador && representa um AND lógico, então se uma condição e a outra forem verdadeiras. Já o operador || representa um OR lógico, então se uma condição ou a outra for verdadeira. Há também o operador not: !, ele é usado antes de um valor, exemplo "!true" que é falso.
# Arrow Function
Há três formas de definir funções em javascript. As mais tradicionais:
~~~js
function somar(a, b){
	return a + b;
}

ou

const somar = function(a, b){
	return a + b;
}
~~~
Porém existe também as arrow functions:
~~~js
const somar = (a, b) => {
	return a + b;
}

se tiver só uma variável pode fazer

const somar = a => {
	return a + 1;
}

quando não há uma lógica, somente um return pode fazer

const somar = a => a + 1;
~~~
# Objetos
Os objetos são muito parecidos com o JSON. Para declarar os objetos usa-se as {} e nele há uma chave e um valor. Exemplo:
~~~js
const usuario = {name: 'Fulano', age: 180};
~~~
Acessando objetos (semelhante a acessar estruturas em C):
~~~js
usuario.name
ou
usuario['name']
~~~
Desconstrutores pegam os valores de objetos e colocam em outras varáveis:
~~~js
const {name, age} = usuarios
~~~
# Arrays
Para criar um array:
~~~js
let numeros = [1, 2, 3, 4, 5];
~~~
Para adicionar números:
~~~js
numeros.push(6);
~~~
Para remover números do final:
~~~js
numeros.pop();
~~~
Esse método acima remove do original (o array original é modificado) e retorna o número removido.
Para filtrar um array (selecionar apenas os valores que satisfazem alguma condição) utiliza-se a seguinte função (ela recebe como parâmetro uma função que deve receber cada um dos elementos e retornar uma condição para se aquele elemento deve continuar ou não):
~~~js
numeros = numeros.filter((numero) => {return numero > 3})
~~~
Para alterar todos os elementos do array, usa-se a função map. Ela recebe como parâmetro uma função e essa função recebe cada um dos elementos e retorna o novo elemento. Geralmente é usado para criar um elemento para cada elemento do objeto (tipo imprimir cada elemento na tela). Exemplo:
~~~js
numeros = numeros.map(numero => numero + 1)
~~~
Tanto o map quanto o filter fazem um loop, internamente, para percorrer todos os elementos.
# Promises
Promessas são assíncronas e recebem como parâmetro uma função que tem como os parâmetros:
- resolve: quando a função assíncrona deu certo
- reject: quando a função assíncrona não deu certo
Quando se tem um código assíncrono, ele não espera o trecho assíncrono acabar para continuar a executar o código, ele executa o resto do código sem esperar (executando, assim, duas coisas ao mesmo tempo).
Veja abaixo um exemplo de promise:
~~~js
const carregarDados = () => Promise((resolve, reject) => {
	let dados;

	// Carregar dados

	if(dados.length > 0) resolve(dados);
	else reject (new Error('Erro ao carregar dados!'));
});
~~~
Para trabalhar com a função assíncrona tem que fazer o seguinte:
~~~js
carregarDados.then(() => {
	return 1;
}).catch(() => {
	return 0;
});
//O then é para quando é resolve
//O catch é para quando é reject

//Um outro jeito é

const dados = await carregarDados(); mas desse jeito só armazena o resolve

//para armazenar também o catch teria que usar um try/catch:
try{
	const dados = await carregarDados();
} catch (err){
	console.log(err);
}
~~~
# Async e Await
Outra forma de trabalhar com funções assíncronas é usando o async e o await. Quando quer que o resto do código não execute enquanto uma função assíncrona não for concluída, usa-se o await:
~~~js
await funcao assincrona{

}

funcao não assincrona;
~~~
Desse jeito a função não assíncrona só será executada quando a função assíncrona terminar.
Porém, para usar o await, ele tem que estar dentro de uma outra função assíncrona. Veja abaixo como arrumar isso:
~~~js
const renderizar = () => {
	const users = await carregarDados();

	return users.map(user => `<div>${user.nome}</div>`)
}

// Nesse modelo acima dará erro pois a função renderizar não é assíncrona, para resolver isso, usa-se o async

const renderizar = async () => {
	const users = await carregarDados();

	return users.map(user => `<div>${user.nome}</div>`)
}

// Assim a função será assícrona e não terá problema.
~~~
# Import e Export
Utiliza-se o import e o export para trabalhar com módulos, ou seja, arquivos diferentes. Primeiramente, para exportar uma função, ou seja, para permitir que outros arquivos usem a função feita em um arquivo x, usa-se o export:
~~~js
export const somar = (a, b) => a + b;
~~~
Para importar um função que está em outro arquivo, é necessário listar cada uma das funções que deseja-se importar. Veja abaixo:
~~~js
import {somar, ...} from './caminho/do/arquivo.js'
// É necessário fazer assim pois ele exporta os objetos, que são formados das várias funções

// Uma outra forma de fazer é:
import Funcoes from './caminho/do/arquivo.js'

Funcoes.somar
Funcoes.etc
...
~~~
Há como determinar uma função default para ser exportada. Se for feito isso, quando importar uma função de um arquivo e não especificar qual função é, será importada a função default. Veja abaixo:
~~~js
// No arquivo A
export const somar = (a, b) => a + b;
export default mult = (a, b) => a * b;

// Pode fazer um objeto como export default também
const somar = (a, b) => a + b;
const mult = (a, b) => a * b;

export default {somar, mult, ...}

// No arquivo B
import Funcao from './caminho/do/arquivo.js'
Funcao(1, 2) // Vai resultar 2
Funcao.somar // Não da para fazer

// Para poder acessar as outras funções também, tem que declarar um outro objeto para elas
import Funcao, {somar, ...} from './caminho/do/arquivo.js'
Funcao(1, 2) // Vai resultar 2
somar(1, 2) // Vai resultar 3

~~~

