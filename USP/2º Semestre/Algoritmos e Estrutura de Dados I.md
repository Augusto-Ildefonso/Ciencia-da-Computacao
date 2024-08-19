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
Ela permite organizar, armazenar e processar esses dados.
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
É um arquivo que contém um conjunto de diretivas usadas pela ferramenta de automação de compilação make para gerar um alvo/meta. O nome do arquivo tem que ser Makefile.
O `all` é uma receita para o que deve ser compilado no final.
Flags:
- -std: indica o padrão C a ser seguido na compilação
- -o: define o nome de arquivos de saída
- -Wall: mostra todos os warnings
- -pedantic-errors: mostra todos os erros, independente do padrão
- -lm: include a biblioteca matemática
- -c: somente compila (gera o .o)
## Item 
O cliente irá usar o item, definir o tipo de dado que será passado para ele, entre outros. A vantagem de usar o item é que não será necessário mudar o TAD para mudar o tipo de dado que será trabalhado. A estrutura de dados não acessa os dados, ela acessa o item.
### Interface do Item
```
#ifndef ITEM_H -> Esse nome _H é uma convenção assim como escrever em maiúsculo
	#define ITEM_H

	#include <stdbool.h>

	typedef struct item_ ITEM;

	ITEM* item_criar(int chave, void* comp);
	bool item_apagar(ITEM* **item);
	int item_get_chave(ITEM* item);
	bool item_set_chave(ITEM* item, int chave);
	void* item_get_dados(ITEM* item);
#endif
```
Os # são instruções de pré-processamento, ou seja, ele define coisas que devem ser definidas, executadas, antes da compilação.
O ifndef significa "if not defined", ou seja, ele só irá executar esse trecho uma vez, caso ele já tenha sido executado e o ITEM_H tenha sido definido, ele não irá executar. Isso é bom pois como temos vários arquivos usando essas funções, várias funções com mesmo nome seriam criadas, o que é um problema. Então, usando esse ifndef ele só ira executar se não tiver sido definido anteriormente.
### Implementação
```
#include <stdlib.h>
#include <stdio.h>
#include "item.h"

struct item_{
	int chave; // Indexador
	void *dados; // Ponteiro para o dado
}

ITEM* item_criar(int chave, void *dado){
	...
}

...
```
O que permite o cliente usar o tipo de dado que ele quiser, sem ter que mudar o TAD, é o uso do tipo `void` para o ponteiro dos dados.
Outra convenção é usar nos nomes das funções o nome do TAD, exemplo: item_{resto do nome}.

# Pilhas (Stacks)
O conceito é de objetos empilhados um em cima do outro. A pilha tem uma ordem de entrada e saída, começa enchendo pela base (primeiro) e quando for retirar, retira por cima (último).
Elas auxiliam em problemas práticos em computação. Exemplos:
- O botão "back" de um navegador web ou a opção "undo" de um editor de textos
- Controle de chamada de procedimentos (memória stack)
- Estrutura de dados auxiliar em alguns algoritmo como a busca em profundida
Pilhas são estruturas de dados nas quais as inserções e remoções são realizadas na mesma extremidade da estrutura, chamada de topo. Dessa maneira o último elemento que foi inserido é sempre o primeiro a ser removido. Isso se chama Política Last-in/First-out (LIFO).
Geralmente usamos pilhas quando queremos que os elementos entrem em uma ordem e saiam na ordem contrária.
## Organização vs Alocação de memória
Alocação Estática: reserva memória em tempo de compilação
Alocação Dinâmica: em tempo de execução
![imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/f08fdfbac13c0f1d3cd30aa9529357bae376f0d0/Imagens/1.png)
1. Sequência e Estática: uso de arrays
2. Encadeada e Estática: arrays simulando a memória principal
3. Sequência e Dinâmica: alocação dinâmica de array
4. Encadeada e Dinâmica: uso de ponteiros
## Operações principais
- Empilhar(P, x): insere o elemento x no topo de P
- Desempilhar(P): remove o elemento do topo de P, e retorna esse elemento
## Operações auxiliares
- Criar(P): cria uma pilha P vazia
- Apagar(P): apaga a pilha P da memória
- Topo(P): retorna o elemento do topo de P, sem remover
- Tamanho(P): retorna o número de elementos em P
- Vazia(P): indica se a pilha P está vazia
- Cheia(P): indica se a pilha está cheia (útil para implementações sequenciais)
## Implementação Sequencial
É uma implementação simples.
Uma variável mantém o controle da posição do topo, e pode ser utilizada também para informar o número de elementos da pilha (tamanho).
O tamanho da pilha é topo-1.