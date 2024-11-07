# O que é React-Native?
É um framework para desenvolvimento de aplicativos utilizando javascript e JSX.

A principal diferença de desenvolver app em React-Native do que em outros frameworks é a flexibilidade de código. O aplicativo feito nessa tecnologia funciona em ambos os sistemas, Android e iOS. Logo para consertar erros e dar upgrades, basta codificar apenas uma vez.
# React DOM
O aplicativo é como se fosse um servidor e ele cria um react virtual DOM (uma DOM como se fosse da web para trocar as divs, mas no caso de apps ele usa o react-native mesmo) e o DOM é a tela do usuário.
# Código Nativo
Todo JSX feito em React-Native é transformado em componentes nativos do SO utilizado para rodar. Por isso, possui um desempenho igual ao de  apps feitos em Java/Swift.
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
# Criando Projeto React-Native com Expo
~~~
$ expo init nome-do-projeto
~~~
Esse modo de criar é mais antigo, porém é o que está funcionando com o Expo no celular.
# Usando Ícones do React-Native
Primeiramente tem que instalar a biblioteca `react-native-vector-icons` usando a seguinte linha de comando:
~~~
$ npm install --save react-native-vector-icons
~~~
Então, com a biblioteca instalada, deve-se importá-la e também especificar qual a biblioteca de ícones que vai ser usada:
~~~js
import NomedaBiblioteca from ' react-native-vector-icons/NomedaBiblioteca'
~~~
Então, para usar o ícone basta usar o método:
~~~js
<NomedaBiblioteca
	name="nome-do-icone"
	size={20} // Exemplo
	color={'#ffffff'} // Exemplo
/>
~~~
# Hook
Hooks são funções que permitem ligar-se aos recursos de state e ciclo de vida do react a partir de componentes funcionais. Eles não funcionam dentro de classes, ele permite que usem o react-native sem classes
# Estado
No React-Native não da para alterar o valor da variável diretamente, pois o reac-native usa o conceito de imutabilidade no estado, ou seja, você não pode alterar diretamente valores com estado. Por isso, utiliza-se um Hook do Reac-Native, que permite essa alteração.

O hook que será usado para mudar o valor é o `useState`, ele sempre renderiza novamente a tela quando altera o valor. Ela vai ter dois parâmetros: o primeiro é a variável e a segunda é uma função que armazena o valor que será passado para a variável.
~~~js
const [numero, setNumber] = useState(0);
~~~
# FlatList
É usado para criar listas no react-native.
~~~js
<FlatList
	data={lista}
	renderItem={(item) =>
		<View>
		...
		</View>
	}
/>
~~~
# Navigation
## Stack Navigation
Com o stack navigation conseguimos alternar entre as telas. Ele geralmente é montado no App.js e tem a seguinte estrutura:
~~~js
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';

const Stack = createStackNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator initialRouteName="TelaLogin"> // Essa propriedade é para especificar qual a primeira tela
        <Stack.Screen name="TelaLogin" component={TelaLogin} options={{headerShown: false}}/> // Será só um identificador, component é a função que está sendo usada e a opção headerShown é para falar se quer q mostre o nome da tela (true) ou não (false)
        <Stack.Screen name="TelaCadastro" component={TelaCadastro} options={{headerShown: false}}/>
        <Stack.Screen name="TelaTarefas" component={TelaTarefas} options={{headerShown: false}}/>
      </Stack.Navigator>
    </NavigationContainer>
  );
}
~~~
## Drawer Navigation
Com o drawer navigation é possível criar menus laterais que deslizam de qualquer lado da tela.
~~~js
<NavigationContainer>
	<Drawer.Navigator initialRouteName="menu" drawerStyle={style.menu}>
		<Drawer.Screen
			name="Alterar Dados"
			component={Tela}
		/>
	</Drawer.Navigator>
</NavigationContainer>
~~~
Esse método irá já criar um ícone para o menu. Mas podemos nós mesmos criar o botão:
~~~js
export default function Menu = ({navigation}) => {
	return (
		<Button title="Toggle" onPress={() => navigation.toggleDrawer()}		
	);
};
~~~
# Criando Menus Laterais
## DrawerNavigation (não está completo)
Para criar menus laterais temos que usar as funções NavigationContainer e createDrawerNavigator. Para criar o menu usa-se:
~~~js
<NavigationContainer>
	<Drawer.Navigator
		initialRouteName="nome do arquivo que tem o menu"
		drawerStyle={style.menu}
    >
    
</Drawer.Navigator>
</NavigationContainer>
~~~
## Modals
~~~js
const [visible, setVisibleModal] = useState(false);

<TouchableOpacity onPress={() => setVisableModal(true)}>
	...
<\TouchableOpacity>

<Modal
	visible={var} // Isso serve para garantir se o modal vai aparecer (true) ou não (false), nele colocamos a variável que controlará o estado ou direto o booleano
	transparent={true} // Com ele como true, o fundo dele será transparente e quem criará todo o estilo será nós
	onRequestClose={() => setVisibleModal(false)} // Essa propriedade serve para fechar o modal
>

<\Modal>
~~~
# SafeAreaView
É uma função para o iOS para garantir que a tela não ficara sobre o notch. É só colocar ela ao redor de todo o view.
# Import com {} ou sem?
Quando importamos uma função default não é necessário as {}. Porém se não for default, é necessário importar dentro das chaves.