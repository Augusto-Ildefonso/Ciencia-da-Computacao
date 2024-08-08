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
Um TAD é um modelo matemático que pode ser representado por uma tupla (v, o), onde v é o conjunto de valores e o é o conjunto de operações.
## Ocultamento de Informação
Os dados armazenados podem ser manipulados apenas pelas operações definidas na interface - *Information Hiding (Ocultamento de Informação)*
Ocultamento dos detalhes de representação e implementação, sendo que apenas a funcionalidade (interface) é conhecida.
Só tem acesso às operações de manipulação dos dados e não aos dados em si.
## Estruturas de Dados e TAD
Uma vez definido um TAD e especificadas as operações associadas, ele pode ser implementado em uma linguagem de programação.
Uma estrutura de dados pode ser vista, então, como uma implementação de TAD. Ela implica na escolha de uma estrutura de dados para representá-lo, a qual é acessada pelas operações que o TAD define.
Uma estrutura de dados é construída a partir dos tipos básicos (inteiros, real, char) ou dos tipos estruturados (array, struct) de uma linguagem de programação.
Podem existir diversas implementações para um mesmo TAD, cada uma com suas vantagens e desvantagens.
## Vantagens
- É possível esconder os detalhes de implementação do usuário. Ele só olha o módulo de interface e sabe como usar (usuário)
- Organização dos dados e controle, pois impede os usuários de acessarem o TAD (desenvolvedor)
- Reuso
- Manutenção
- Correção
- Independência de representação
## Implementação
Requer que operações sejam definidas sobre os valores sem estarem atreladas a uma implementação específica. O programador que usa um tipo de dado double, int ou um array de int, não precisa saber como os mesmos são representados internamente na memória do computador. O mesmo princípio pode ser aplicado a listas, pilhas, etc. Se existe uma implementação disponível de uma lista, por exemplo, um programador pode utilizá-la como se fosse uma caixa preta, e acessá-la por meio das operações que o TAD lista suporta.
O conceito de TAD é suportado por algumas linguagens de programação procedimentais. Exemplo: Java, C, C++, Python, entre outras.
Para definir um TAD:
- O programador projetista descreve o TAD em dois módulos separados:
	- Um módulo de implementação que contém a definição do TAD: representação (declaração) da estrutura de dados e implementação de cada operação suportada (em C este módulo é um (ou alguns) arquivos .c).
	- Um módulo de interface de acesso: apresenta as informações possíveis.
- Os programadores usuários podem, por meio da interface de acesso, usar o TAD sem conhecer os detalhes representacionais e sem acessar o módulo de definição.
Na implementação de um TAD, a escolha da estrutura de dados empregada tem papel importante. Uma escolha mal feita pode resultar em implementações ineficientes ou mesmo não-factíveis.
## Encapsulamento
Usamos uma struct para fazer o encapsulamento. Criamos ela no módulo de definição.

## Módulo de interface
É um arquivo .h que contém os protótipos das funções. Temos um outro arquivo .c que contém o código das funções e nele também estão definidas as estruturas de dados. Para usarmos temos que colocar na pasta do código principal o .o e o .h.
## Makefile
É um arquivo que contém um conjunto de diretivas usadas pela ferramente de automação de compilação make para gerar um alvo/meta.
Flags:
- -std: indica o padrão C a ser seguido na compilação
- -o: define o nome de arquivos de saída
- -Wall: mostra todos os warnings
- -pedantic-errors: mostra todos os erros, independente do padrão
- -lm: include a biblioteca matemática
- -c: somente compila (gera o .o)
