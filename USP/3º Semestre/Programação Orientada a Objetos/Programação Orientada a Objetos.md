# Introdução
## O que são paradigmas de programação
Os paradigmas de programação referem-se a diferentes estilos e abordagens para escrever código.
Entre os mais conhecidos estão o procedimental, orientado a objetos, funcional e lógico.
## Paradigmas de programação
Os paradigmas de programação podem ser categorizados em dois grupos principais: imperativo e declarativo. A categoria imperativa inclui os paradigmas procedural e orientado a objetos, enquanto a categoria declarativa inclui outros paradigmas como programação funcional e lógica.
## Paradigma procedural
O paradigma procedural é um estilo de programação que se concentra em procedimentos ou funções, em que sequencias de comandos são executadas para atingir um resultado. As linguagens C, Pascal e Basic são exemplos de linguagens de programação procedurais.
## Paradigma orientada a objetos
O paradigma orientado a objetos modela um sistema em termos de objetos, que são instâncias de classes que interagem entre si. Alguns princípios dela são: encapsulamento, herança, polimorfismo e abstração são fundamentais para este paradigma. Exemplos de linguagens são: Java, Python, C++ e C#.
## Paradigma funcional
O paradigma funcional se baseia no uso de funções puras e imutabilidade de dados, priorizando a expressão de lógica matemática na programação.
A recursão e a composição de funções são características essenciais desse paradigma, promovendo a modularização e o reuso de código.
Ela tem um foco forte na descrição de comportamento e na minimização de efeitos colaterais o que torna o funcionamento adequado para ambientes concorrentes e distribuídos.
Exemplos de linguagens são: Lisp, Haskell e Scala.
## Paradigma lógico
As linguagens principais são Prolog, Datalog, Answer set Programing. Ele tem uma abordagem baseada em lógica matemática e regras de inferência. Ela trabalha com resolução de problemas a partir de fatos, regras e consultas.
## Vantagens e desvantagens de cada paradigma
### Procedural
Vantagens:
- Simplicidade e controle preciso
Desvantagens:
- Dificuldade em lidar com sistemas complexos
### Orientado a objetos
Vantagens:
- Reutilização de código e modelagem do mundo real
Desvantagens:
- Overhead e curva de aprendizado
### Funcional
Vantagens:
- Imutabilidade e facilidade de paralelização
Desvantagens:
- Dificuldade de compreensão para iniciantes
### Lógico
Vantagens:
- Declaração de lógica pura e inferência automática
Desvantagens:
- Dificuldade em tarefas não lógicas e performance
## Como escolher o paradigma adequado para um objeto
## Analisar as necessidades do projeto
Entender os requisitos e o escopo para determinar a abordagem mais adequada.
## Avaliar as habilidades da equipe
Considerar as competências e experiências para escolher um paradigma que melhor se alinhe com o conhecimento existente.
## Testar a viabilidade e eficiência
Realizar protótipos ou estudos de caso para avaliar a adaptabilidade e desempenho de cada paradigma no contexto do projeto
# O que é POO?
## Definição
A POO é um paradigma de programação que permite a modelagem de conceitos do mundo real, como objetos e suas interações por meio de estruturas de dados e métodos.
### Representando objetos do mundo real
#### Modelagem precisa
A POO permite a representação fiel de objetos reais, incluindo suas propriedades e comportamentos, através de classes e objetos.
#### Simulação de comportamentos
É possível simular a interação entre objetos do mundo real, como veículos, animais e dispositivos eletrônicos, facilitando a compreensão e análise de cenários complexos.
### Estruturas que fazem sentido nos programas
Além de representar objetos, os objetos também podem ser utilizados para representar estruturas de dados, como filas e pilhas. Essas estruturas são amplamente utilizadas em programação para organizar e manipular dados de forma eficiente.
### Desafios na implementação de POO
#### Abstração adequada
A identificação e criação de abstrações precisas para os objetos do mundo real podem representar um desafio significativo.
#### Complexidade crescente
À medida que os projetos crescem, a estrutura e a relação entre os objetos podem se tornar complexas e difíceis de manter
## Princípios
Na POO, os objetos são as principais entidades. Eles podem conter dados na forma de campos (atributos) e código na forma de procedimentos (métodos).
### Estado (são os atributos)
São representados por variáveis
### Operações (são os métodos)
São representados por funções. As funções modificam o estado do objeto.
### Atributos
Também chamados de membros de dados, propriedades ou campos, os atributos representam as características dos objetos pertencentes à classe. Eles armazenam dados que descrevem o estado de um objeto.
### Método
Também conhecidos como funções ou procedimentos, os métodos representam os comportamentos dos objetos. Eles são blocos de códigos que definem as ações que um objeto pode realizar ou responder. Alguns métodos comuns de colocar nas classes são aqueles que retornam o estado de um atributo.

Atributos e métodos são chamados de membros da classe ou do objeto.
### Objetos
Um objeto é uma instância de uma classe. Ele é uma entidade individual que possui características específicas e pode realizar ações ou métodos conforme definido pela classe à qual pertence.
### Classe
Uma classe é um modelo ou uma planta baixa para criar objetos. Ela define as características e comportamentos comuns a um grupo de objetos relacionados. Uma classe é como um molde a partir do qual múltiplos objetos individuais podem ser criados.
### Construtor
Um construtor é um método especial dentro de uma classe que é automaticamente invocado quando um objeto dessa classe é criado. Ele é usado para inicializar o estado interno do objeto, definir valores padrão para os atributos da classe ou executar outras operações necessárias para garantir que o objeto seja criado corretamente.
## Composição
A composição de objetos envolve a criação de objetos complexos combinando vários objetos menores. É uma forma de organizar e estruturar a funcionalidade dos objetos.
### Membros estáticos
É como se fosse uma variável global. Ela é uma variável da classe em si e não somente do objeto. Então ela modifica valores para todos os objetos da classe. Podem ser tanto atributos estáticos quando métodos estáticos.
Por exemplo, numa classe que representa cadeira. Se tivermos criando várias cadeiras e tivermos um atributo estático que conta quantas cadeiras, quando imprimirmos esse valor ele terá a quantidade de cadeira, desde que o valor seja alterado toda vez que uma cadeira é criada.
# Ambiente de Programação JAVA
## Java Oracle
Existem diversos compiladores e ferramentas Java. O mais usado é o da oracle, o Java Plataform, Standard Edition (JDK). Ele inclui um conjunto de ferramentas e código que permite o desenvolvimento de aplicações Java. O Java utiliza uma máquina virtual (JVM) para executar o "executável"
## Primeiro programa
~~~java
public class MeuPrograma
{
	public static void main(String args[])
	{
		System.out.println("Meu primeiro programa Java.")
	}
}
~~~
## Compilando
Rodamos o seguinte comando para compilar
```
$ javac MeuPrograma.java
```
Esse arquivo é o arquivo "executável" do seu programa Java. Na verdade, ele contém uma representação intermediária do seu programa. Essa representação precisa da JVM.
O nome do arquivo tem que ser o mesmo nome usado para a classe.
## Executando
Rodamos o seguinte comando para executar.
```
$ java MeuPrograma
```
Esse comando vai procurar o arquivo e vai executá-lo, através da JVM. Em tese ela interpreta o código Java. Ela segue a lógica "*Write once, run anywhere*" (WORA), isso significa que qualquer máquina que tem a JVM vai executar o programa independente da arquitetura.
# Linguagem Java
## Uma classe em Java
O modificador de acesso `public` torna essa classe acessível a outras classes. Isso significa que outras classes, independentemente de estarem no mesmo pacote ou em pacotes diferentes, ordem criar instâncias dessa classe.
Veja abaixo um exemplo para uma classe chamada cadeira.
~~~java
public class Cadeira
{
	String posicao;
	boolean ocupado;
	// Métodos
	void sentar(){ 
	}
	void levantar(){
	}
	void virar(){
	}
	String getPosicao(){
	}
	
}
~~~
Tem um erro no código, pois cada membro tem que ter o seu controle de acesso. Veja o código arrumado abaixo.
~~~java
public class Cadeira
{
	// Atributos
	private String posicao;
	private boolean ocupado;
	
	// Métodos
	public void sentar(){ 
	}
	public void levantar(){
	}
	public void virar(){
	}
	public String getPosicao(){
	}
	
}
~~~
Os membros declarados como ``private`` significa que esse membro só pode ser acessado dentro da própria classe onde foi definido. Isso cria um encapsulamento dos detalhes internos da classe, impedindo o acesso direto a esses membros por outras classes.
Já os membros declarados como ``public`` são acessíveis de fora da classe em que são definidos. Isso significa que eles podem ser acessados e utilizados por outras classes, independentemente de estarem no mesmo pacote ou em pacotes diferentes.
Também é preciso que a classe tenha um construtor. O construtor é um método que tem o mesmo nome da classe. Ele não tem um tipo declarado. Podemos ter mais do que um construtor.
~~~java
public class Cadeira
{
	// Atributos
	private String posicao;
	private boolean ocupado;

	// Construtores
	public Cadeira(){
	}
	public Cadeira(String p, boolean oc){
	}
	
	// Métodos
	public void sentar(){ 
	}
	public void levantar(){
	}
	public void virar(){
	}
	public String getPosicao(){
	}
	
}
~~~
Veja que ela tem dois construtores. Isso pode ser feito e para selecionar qual deles usar é só passar os parâmetros de acordo com os parâmetros do construtor. Veja abaixo.
~~~java
c1 = new Cadeira(); // Usa o primeiro construtor
c2 = new Cadeira("Oi", True); // Usa o segundo construtor
~~~
Java é uma linguagem com verificação estática de tipos. Por causa disso, todos os membros precisam ser declarados e ter um tipo. Isso permite que o compilador verifique se existe alguma inconsistência.
Repare nos nomes das classes e dos membros. O padrão (não é regra, mas é convenção) é usar as classes com a primeira letra maiúscula, se tiver duas palavras a primeira letra de cada palavra é maiúscula. Variáveis são todas minúsculas, porém se tiver mais de uma palavra o início das próximas palavras são maiúsculas.
Os comentários seguem o mesmo padrão da linguagem C.
## Tipos de dados
- int -> 4 bytes
- long -> 8 bytes
- float -> 4 bytes
- double -> 8 bytes
- char -> 2 bytes
- short -> 2 bytes
- byte -> 1 byte
- boolean -> 1 bit
Em C o int tem o tamanho da palavra que o computador usa, se a palavra da arquitetura for de 4 bytes, o int tem 4 bytes, se a palavra tiver 8 então int tem 8 bytes. Isso não acontece em Java, pois tudo é executado na JVM que segue um padrão fixo. Os tipos da linguagem Java são semelhantes aos tipos da linguagem C. O char tem 2 bytes pois em Java não é usada a representação ASCII, e sim UTF-8 por exemplo.
Condições de comando como if e while aceita apenas booleano.
## Operadores
- Sufixal: ++ ou --
- Prefixal: ++, --, +, -, !
- Multiplicativos: ``*``, /, %
- Aditivos: + ou -
- Shift binário: <<, >>, >>>
- Comparativos: <, >, <=, >=, instanceof
- Igualdade: == ou !=
- Bit-a-bit E: &
- Bit-a-bit XOU: ^
- Bit-a-bit OU: |
- Lógico E: &&
- Lógico OU: ||
- Ternário: ? e :
- Atribuição: =, +=, -=, $*=$, /=, %=, &=, ^=, |=, <<=, >>= ou >>>=
Obs: o `==` para strings verifica se os objetos são iguais, ou seja, é como se verificasse se dois ponteiros apontam para a mesma variável, no caso objeto. Para verificar o conteúdo é preciso usar o método `equals`, exemplo: `variável.equals("Meu texto")`
## Casting
Em C é possível fazer casting dos tipos. Em Java é obrigatório um muitos casos fazer o casting. Quando há a possibilidade de se perder informação o casting é requerido. Caso seja necessário, o compilador vai avisar.
Veja abaixo a tabela de conversão.
![[Pasted image 20250327131614.png]]
Se for ir de uma variável maior para uma menor é obrigatório o uso do casting, caso contrário não é obrigatório. Além disso, não é possível fazer o casting de uma variável boolean para outro tipo.
## Declaração de variáveis
As variáveis podem ser declaradas na hora que forem usadas. Vale a mesma regra de escopo. Por exemplo uma variável declarada dentro de um ``if`` vale apenas naquele escopo. Os parâmetros são variáveis locais.
## Comandos de seleção
### If-else
~~~java
if (expressão booleana)
{
	comando 1;
	comando 2;
}
else {
	comando 3;
	comando 4;
}
~~~
### Switch
~~~java
switch (s) {
	case "abc":
		b = 10;
		break;
	case "cde":
		c = 20;
		break
	default:
		b = 0;
}
~~~
Diferente de C que o valor do case tem que ser um inteiro, aqui em Java pode ser qualquer tipo.
## Comandos de repetição
O comando for não muda, mas podemos declarar a variável que será usada como controle. Também existe for para percorrer arrays, strings e outros. Os comandos while não mudam.
### For (padrão, igual C)
~~~java
for (int i = 0; i < 10; i++){
}
~~~
### For (para arrays, strings, etc)
~~~java
for (int k : v){
}
~~~
### While
~~~java
while (i < 10){
}
~~~
### Do-While
~~~java
do{
} while (i < 10)
~~~
## Break e Continue
Tudo igual ao C, mas podemos ter um rótulo que indica qual comando quebrar ou continuar.
~~~java
boolean achou = False;
label1: // Aqui está o rótulo
for (int i = 0; i < 10; i++){
	for (int j = 0; j < 10; j++){
		if(t[i][j] == 0){
			achou = True;
			break label1; // Ele vai dar break no for de fora
		}
	}
}
~~~
## Exceções
Para tratar os erros tem o `try` e `catch`. Qualquer exceção dentro do bloco é tratada. Evita que a exceção seja propagada para quem chamou o método em questão. Se a exceção for propagada, quem fez a chamada ainda pode tratar a exceção.
~~~java
try {
	código
}
catch (Exception nome_da_variavel) {
	código
}
~~~
Obs: O `fscanf` retorna o número de variáveis que leu, assim dá para saber se ocorreu um erro ou não.
### Tratamento de exceções
![[Pasted image 20250327131843.png]]
## Print
~~~java
System.out.println(variável ou string);
~~~
## Arrays

Em Java, um array é um objeto que tem uma sequência de valores do mesmo tipo.
~~~java
private int [] table; // Define uma variável

table = new int[16];
tamanho = table.length

for (int i = 0; i < tamanho; i++){
	table[i] = i;
}
~~~
Uma matriz é um array de array. Para criar é semelhante à C, basta só usar int`[][]`.
## Criando variável
Além de declarar a variável, é preciso usar o comando `new` para instanciar ela e criá-la de fato.
# POO com Python
## Classe
~~~python
class Cadeira:
	def __init__(self): # Construtor da classe
		self.posição = "Em pé" # Como não temos declaração de variáveis, o que for criado aqui será os atributos da classe. Só pode ter um construtor
		# Para fazer referência a uma variável da classe tem que usar o self.
		self.ocupado = False
~~~
Na declaração dos métodos sempre tem que ter o self como parâmetro. Python não permite dois métodos com mesmo nome. Para contornar usamos valores default para parâmetros.
~~~Python
class Cadeira:
	def __init__(self, p="Em pé", oc=False):
		self.posição = "Em pé"
		self.ocupado = False
~~~
Definição dos métodos é igual a definição de função normal do python, mas com o self como um dos parâmetros.
O mesmo arquivo pode conter mais do que uma classe e não precisa ter o mesmo nome. Pode ter código fora da classe também.
# Herança
Herança é um conceito fundamental que permite que uma classe herde atributos e métodos de outra classe. A herança permite que você crie hierarquias de classes, onde classes mais específicas (subclasse) podem herdar características de classes mais gerais (superclasses), e ao mesmo tempo adicionar novos comportamentos ou substituir comportamentos existentes, se necessários.
A classe que herda é chamada de classe filha ou subclasse, e a classe da qual ela herda é chamada de classe pai ou superclasse.
A principal vantagem da herança é a reutilização de código. Ao invés de escrever novamente (completar).
## Herança com Java
Para declarar uma subclasse em Java usamos:
~~~java
public class Nome_Subclass extends Nome_Superclass{
	public Nome_Subclass(){
		super(...);
	}

	@Override
	public void funcao_super(){
		...
	}

	// Sem override pq é um método específico da subclasse
	public void funcao_sub(){
		...
	}
}
~~~
Para chamar um construtor da própria classe dentro dela usamos o `this()`. Mas quando queremos chamar o construtor da superclasse usamos `super()`.
Para sobrescrever um método da superclasse usamos o `@Override` antes de criar o método.
Em Java toda classe tem uma superclasse. Mesmo que seja implícito, por exemplo, se você tiver só um objeto em Java, ele vai usar a superclasse Object do próprio Java. Um exemplo de método dessa superclasse é o ``toString()``.
Se quer chamar um método da superclasse dentro da subclasse, usa-se `super.nome_metodo()`. Vale ressaltar que o método tem que ser public ou então protected (que não é possível acessar fora da classe, mas dentro das subclasses é possível acessar, assim como dentro da própria classe).
Quando nossa superclasse serve só para fornecer características gerais e ele não será instanciada e sim será usada somente por subclasses, usamos o `abstract` para que ele não possa ser instanciada sozinha. Exemplo: `public abstract class Animal`. Podemos exigir que toda subclasse tenha um método, mas que esse método só seja definido na subclasse e não na superclasse. Para isso usamos também o `abstract` para o método, exemplo `public abstract void fazerSom()`, desse jeito, as subclasses terão que implementar e definir o método marcado como ``abstract``. Os métodos que não são marcados como `abstract` não precisam necessariamente serem reimplementados na subclasse. Para ter um método `abstract` temos que ter uma superclasse `abstract`. O contrário do `abstract` é concreto, então uma classe concreta é aquela que não tem métodos abstratos.
Em Java, uma classe só tem uma classe pai. Isso é conhecido como herança simples
### Criando Interface gráfica
Usamos a superclasse ``JFrame``. Dentro dela são criados todos os componentes e na subclasse só chamamos eles.
## Herança com Python
Os conceitos teóricos de Java valem para Python também. Mas ele tem mudanças em como são implementados os conceitos.
~~~python
class Animal: # Superclasse
	def __init__(self, nome):
		self.nome = nome

	def fazer_som(self):
		print("O animal faz som não identificado")

	def get_nome(self):
		return self.nome

class Cachorro(Animal):
	def fazer_som(self):
		print("O cachorro late")
~~~
Em python não é preciso chamar o construtor da subclasse nem da superclasse, se não tiver um ``__init__`` dentro da subclasse ele usa o construtor da superclasse. Caso eu coloque um construtor na subclasse, temos:
~~~python
class Gato(Animal):
	def __init__(self, nome, sobre):
		super().__init__(nome)
		self.sobrenome = sobre

	def fazer_som(self):
		print("O gato mia")

	def get_nome(self):
		return self.nome + ' ' + self.sobrenome
~~~
Aqui o uso do super é `super().nome_do_método`, até mesmo para o construtor. Perceba que não é necessário um override para redefinir a função.
Para criarmos uma classe abstrata é preciso usar uma biblioteca:
~~~python
from abc import ABC, abstractmethod

class Animal(ABC): # Definindo classe abstrata
	def __init__(self, nome):
		self.nome = nome

	@abstractmethod # Criando método abstrato, para isso usa-se esse decorator
	def fazer_som(self):
		pass ## Para poder deixar sem implementar

	def get_nome(self):
		return self.nome
~~~
Em python temos herança múltipla, ou seja, podemos ter mais de uma classe pai. É recomendado evitar usar herança múltipla, exceto no caso que é para usar uma classe abstrata. Essa recomendação existe pois pode resultar em um comportamento inesperado.
Para contornar esse problema, recorremos ao MRO (Ordem de Resolução de Métodos). Ele estabelece qual a ordem de procura do método na hierarquia. Em python é da esquerda para direita. Para conhecer a ordem, basta usar o método MRO da classe. Toda linguagem que tem herança múltipla vai ter esse método MRO.
PORÉM, ainda sim é recomendado evitar esse uso. Além disso, temos esse problema nos construtores também. Para complicar, construtores de classes diferentes podem ter parâmetros diferentes. Nesse caso não tem como passar os parâmetros corretos para os construtores corretos.
# Polimorfismo
## Java
Na programação orientada a objetos, o polimorfismo permite que referência de tipos de classes mais abstratas representem o comportamento das classes concretas que referenciam. Assim, é possível tratar vários tipos de maneira homogênea (através da interface do tipo mais abstrato). 
O tipo é definido pela declaração e não pela instanciação. Então se declarar `Animal c = new Cachorro ("Rex")` o `c` será do tipo animal e não cachorro.
(Inserir exemplos de polimorfismo)
### Polimorfismo de Sobrecarga
Sobrecarga é quando temos o mesmo método (mesmo nome) mas com assinaturas diferentes.
~~~Java
private int altura () {
	...
}

private int altura (int no){
	...
}
~~~

~~~Java
int k = altura();
int j = altura(16);
~~~
Podemos até mesmo chamar um método dentro do outro
## Python
O que falamos pra Java sobre polimorfismo vale para Python também. Mas como ele não tem tipo estático, ele se difere um pouco do Java na questão da Herança. Em Python o que temos de fato é Duck Typing, que possui algumas diferenças quando comparada com herança em Java.
### Duck typing
Duck typing é um estilo de tipagem em que os métodos e propriedades de um objeto determinam a semântica válida, em vez de sua herança de uma classe particular. Se parece um pato, nada como um pato e anda como um pato, então é um pato.
### Parâmetros Opcionais
Não é possível (completar)