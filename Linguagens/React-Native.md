# O que é React-Native?
É um framework para desenvolvimento de aplicativos utilizando javascript e JSX.

A principal diferença de desenvolver app em React-Native do que em outros frameworks é a flexibilidade de código. O aplicativo feito nessa tecnologia funciona em ambos os sistemas, Android e iOS. Logo para consertar erros e dar upgrades, basta codificar apenas uma vez.
# React DOM
O aplicativo é como se fosse um servidor e ele cria um react virtual DOM (uma DOM como se fosse da web para trocar as divs, mas no caso de apps ele usa o react-native mesmo) e o DOM é a tela do usuário.
# Código Nativo
Todo JSX feito em React-Native é transformado em componentes nativos do SO utilizado para rodar. Por isso, possui um desempenho igual ao de  apps feitos em Java/Swift
# Requisitos para usar o React-Native
Ter o Nodejs instalado e também será usado um app chamado Expo para visualizar o aplicativo
# Sintaxe
O React-Native utiliza elemento que se parecem com o HTML mas é um componente próprio dele. Temos as seguintes tags:
~~~javascript
<View> </View> (se assemelha a div)
<Text> </Text> (se assemelha ao p)
~~~

Existem diversos outros componentes que podem ser achados na documentação do react-native.

No projeto, importa-se cada um dos componentes que serão utilizados na seguinte linha no início do arquivo:
~~~js
import { StyleSheet, Text, View } from 'react-native';
~~~

No react-native, a estilização é igual ao CSS, porém praticamente tudo é flexbox.

No react pode-se usar o && para renderizar componentes quando uma informação for verdadeira:
~~~js
{isLoading && <p>Carregando</p>}
~~~
No exemplo acima, o componente `<p> Carregando </p>` tem valor lógico 1 porque é diferente de 0, então a condição vai depender somente do isLoading. Se ele for verdadeiro, então ele irá renderizar o "Carregando".
# Entrada de texto
Para inserir textos usa-se o componente TextInput. Esse componente dá opções de estilização de diversas features, como: corretor automático, auto capitalização, texto placeholder e diferentes tipos de teclado.
~~~js
const [text, onChangeText] = React.useState('Useless Text');
const [number, onChangeNumber] = React.useState('');

<TextInput
	style
	onChangeText={onChangeText ou onChangeNumber}
	value={text ou number}
	placeholder={"useless placeholder"} // Ele deixa o placeholder como fundo só
	keyboardType="numeric" // ou então não colocar
/>
~~~