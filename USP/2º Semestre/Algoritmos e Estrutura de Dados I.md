# Tipos Abstratos de Dados
## Tipo de dado 
Método para interpretar o conteúdo da memória do computador. Define a quantidade de bytes a serem utilizados para representar um valor (dado) e como interpretar a sequência de bits correspondentes a esse valor.
Caracteriza o conjunto de valores a que uma constante pertence, ou que podem ser assumidos por uma variável ou expressão, ou que podem ser gerados por uma função.
Tipos simples são int, float, double, etc. 
Tipos estruturados: composições de tipos simples utilizando structs.
## Algoritmo
Pode ser visto como uma sequência de ações executáveis para a obtenção de uma solução para um determinado tipo de de problema.
## Estrutura de Dados
Organização de dados e operações (algoritmos) que podem ser aplicadas sobre os dados como forma de apoio à solução de problemas (complexos). 
É um tipo abstrato de dados.
## Definição de Tipo Abstrato de Dados (TAD)
Um "tipo abstrato de dados" é um conjunto de valores e uma sequência de operações sobre estes valores (conjunto de propriedades lógicas).
Este conjunto e estas operações formam uma construção matemática que pode ser implementada usando determinada estrutura de dados.
"Tipo abstrato de dados" refere-se a um modelo para definir e representar um tipo de dado estruturado.
Características:
- É usado para encapsular (organizar) tipos de dados (pensar em termos das operações suportadas e não como são implementadas). Uma vantagem é a organização
- Não há necessidade de o desenvolvedor saber a representação interna de um tipo de dado
- Não se preocupa com a eficiência de tempo e espaço, porque elas são questões de implementação
Para ser TAD tem que ser encapsulado.
## Ocultamento de Informação
Os dados armazenados podem ser manipulados apenas pelas operações definidas na interface - *Information Hiding (Ocultamento de Informação)*
Ocultamento dos detalhes de representação e implementação, sendo que apenas a funcionalidade (interface) é conhecida.
Só tem acesso às operações de manipulação dos dados e não aos dados em si.
## Vantagens
- É possível esconder os detalhes de implementação do usuário. Ele só olha o módulo de interface e sabe como usar (usuário)
- Organização dos dados e controle, pois impede os usuários de acessarem o TAD (desenvolvedor)
- Reuso
- Manutenção
- Correção
- Independência de representação
## Implementação
O conceito de TAD é suportado por algumas linguagens de programação procedimentais. Exemplo: Java, C, C++, Python, entre outras.
Para definir um TAD:
- O programador projetista descreve o TAD em dois módulos separados:
	- Um módulo de implementação que contém a definição do TAD: representação (declaração) da estrutura de dados e implementação de cada operação suportada (em C este módulo é um (ou alguns) arquivos .c).
	- Um módulo de interface de acesso: apresenta as informações possíveis.
- Os programadores usuários podem, por meio da interface de acesso, usar o TAD sem conhecer os detalhes representacionais e sem acessar o módulo de definição.
## Encapsulamento
Usamos uma struct para fazer o encapsulamento. Criamos ela no módulo de definição.

## Módulo de interface
É um arquivo .h que contém os protótipos das funções. Temos um outro arquivo .c que contém o código das funções e nele também estão definidas as estruturas de dados. Para usarmos temos que colocar na pasta do código principal o .o e o .h.
## Extra
Ele pode ser implementado por hardware ou por software. No caso do software, existe um programa que consiste de instruções de hardware já existentes que serão usadas para interpretar esse dado. Ou seja, há uma especificação de como o novo tipo de dado pode ser interpretado a partir dos tipos de dados já existentes e também de como as operações definidas para ele ocorrerão.
Um TAD consiste em duas partes: uma definição de valores e uma definição de operadores. A definição de valores determina o conjunto de valores para o TAD e é dividida em duas partes:
- Uma cláusula de definição
- Uma cláusula de condição
Vale mencionar que usamos a notação de colchetes para indicar as partes de um tipo abstrato.
A outra parte é a definição de operadores. Cada operador é definido como uma função abstrata com três partes:
- Cabeçalho
- Pré-condições opcionais
- Pós-condições
Veja agora um exemplo em C de um tipo de dado abstrato chamado RATIONAL:
```
// Definição de valor
abstract typedef <integer, integer> RATIONAL;
condition RATIONAL[1] <> 0;

// Definição de operador
abstract RATIONAL makerational(a, b)
int a, b;
precondition b <> 0;
postcondition makerational[0] == a;
			  makerational[1] == b;

abstract RATIONAL add(a,b) /* written a + b */
RATIONAL a,b;
postcondition add[1] == a[1] * b[1] ;
              add[0] == a[0] * b[1] + b[0] * a [1];
              
abstract RATIONAL mult(a,b) /* written a * b*/
RATIONAL a,b;
postcondition mult[0] == a[0] * b[0] ;
              mult[1] == a[1] * b[1] ;
              
abstract equal(a,b) /* written a == b */
RATIONAL a,b;
postcondition equal == (a[0] * b[1] == b[0] * a[1]) ;
```
As palavras abstract typedef introduzem uma definição de valor e a palavra condition é usada para indicar condições impostas sobre o tipo recém-definido.
Agora para a definição de operadores, o cabeçalho é as duas primeiras linhas de cada operação. A palavra abstract indica que não é uma função de C e sim uma função abstrata. O comentário com a palavra-chave written indica uma nova forma de escrever a função. A pós-condição (postcondition) indica o que a função faz.
A pré-condição (precondition) especifica restrições que devem ser atendidas antes da aplicação da operação.

