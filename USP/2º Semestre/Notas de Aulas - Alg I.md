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
Link: https://www.geeksforgeeks.org/stack-data-structure/
O conceito é de objetos empilhados um em cima do outro. A pilha tem uma ordem de entrada e saída, começa enchendo pela base (primeiro) e quando for retirar, retira por cima (último).
Elas auxiliam em problemas práticos em computação.
Pilhas são estruturas de dados lineares que seguem uma ordem específica para as operações. Nesse TAD, as inserções e remoções são realizadas na mesma extremidade da estrutura, chamada de topo. Dessa maneira o último elemento que foi inserido é sempre o primeiro a ser removido. Isso se chama Política Last-in/First-out (LIFO).
Geralmente usamos pilhas quando queremos que os elementos entrem em uma ordem e saiam na ordem contrária.
Aplicações das pilhas são:
- Recursão
- Evaluating e Parsing de expressões
- Busca em profundidade
- Operações de refazer e desfazer
- Histórico do navegador
- Chamadas de funções
## Organização vs Alocação de memória
Alocação Estática: reserva memória em tempo de compilação
Alocação Dinâmica: em tempo de execução
![imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/1.png)
1. Sequência e Estática: uso de arrays
2. Encadeada e Estática: arrays simulando a memória principal
3. Sequência e Dinâmica: alocação dinâmica de array
4. Encadeada e Dinâmica: uso de ponteiros
## Operações principais
- **Empilhar(P, x)**: insere o elemento x no topo de P (push)
- **Desempilhar(P)**: remove o elemento do topo de P, e retorna esse elemento (pop)
- Topo(P): retorna o elemento do topo de P, sem remover
- Vazia(P): indica se a pilha P está vazia
- Cheia(P): indica se a pilha está cheia (útil para implementações sequenciais)
## Operações auxiliares
- Criar(): cria uma pilha P vazia
- Apagar(P): apaga a pilha P da memória
- Tamanho(P): retorna o número de elementos em P
## Implementação Sequencial (Estática)
É uma implementação simples.
Uma variável mantém o controle da posição do topo, e pode ser utilizada também para informar o número de elementos da pilha (tamanho).
O tamanho da pilha é topo-1.
**Módulo de interface**
```
#ifndef PILHA_H
	#define PILHA_H
	#include <stdbool.h>

	typedef struct pilha_ PILHA;

	PILHA *pilha_criar(void);
	void pilha_apagar(PILHA **pilha);
	bool pilha_vazia(PILHA *pilha);
	bool pilha_cheia(PILHA *pilha);
	int pilha_tamanho(PILHA *pilha);
	ITEM *pilha_topo(PILHA *pilha);
	bool pilha_empilhar(PILHA *pilha, ITEM *item);
	ITEM *pilha_desempilhar(PILHA *pilha);
	void pilha_print(PILHA *p);
	void pilha_inverter(PILHA *p);
#endif
```
**Módulo de Implementação**
```
struct pilha{
	ITEM* item[TAM];
	int tamanho;
};

PILHA* pilha_criar(void) {
	PILHA* pilha = (PILHA *) malloc(sizeof (PILHA));
	if (pilha != NULL)
		pilha->tamanho = 0;
	return (pilha);
}

bool pilha_vazia(PILHA* pilha) {
	if (pilha != NULL)
		return ((pilha->tamanho == 0) ? true : false);
	return(false);
}

bool pilha_cheia(PILHA *pilha) {
	if (pilha != NULL)
		return ((pilha->tamanho == TAM) ? true : false);
	return(false);
}

int pilha_tamanho(PILHA *pilha) {
	return ((pilha != NULL) ? pilha->tamanho : -1);
}

bool pilha_empilhar(PILHA *pilha, ITEM* item) {
	if ((pilha!=NULL) && (!pilha_cheia(pilha)) {
		pilha->item[pilha->tamanho] = item;
		pilha->tamanho++;
		return (true);
	}
	return (false);
}

ITEM* pilha_desempilhar(PILHA* pilha) {
	ITEM* i;
	if ((pilha != NULL) && (!pilha_vazia(pilha))) {
		i = pilha_topo(pilha);
		pilha->item[pilha->tamanho-1] = NULL;
		pilha->tamanho--;
		return (i);
	}
	return (NULL);
}

Falta algumas funções
```
## Implementação Encadeada (Dinâmica)
Ponteiros podem ser usados para construir estruturas, tais como Pilhas, a partir de componentes simples chamados nós. Substituímos os itens por nós. Dividimos o nó em duas regiões: uma que tem as informações e uma que tem um ponteiro para outro nó. Veja abaixo o que é o nó:
```
typedef struct no_ NO;

// Pode ter o que quiser dentro, só é necessário um dos elementos ser um
// ponteiro para a própria struct

struct no_{
	ITEM* item;
	NO* anterior;
};
```
Encadeamentos são úteis pois podem ser utilizadas para implementar o TAD pilha. Uma vantagem é o fato de não ser necessário informar o número de elementos em tempo de compilação.
A função pilha_cheia retorna verdadeiro quando atingir o limite da memória, não ter mais memória disponível para alocar.
Por exemplo, uma operação de empilhar pode ser feita da seguinte maneira:
Antes
![Pilha Encadeada](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-22%2011-45-27.png)
Depois
![Pilha encadeada](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-22%2012-46-40.png)
Por exemplo, uma operação de desempilhar pode ser feita da seguinte maneira:
Antes
![Pilha encadeada](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-22%2012-50-41.png)
Depois
![Pilha Encadeada](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-22%2012-53-56.png)
O topo é o início. Pode-se implementar as operações utilizando a abordagem de listas ligadas simples. Utilizando o TAD Pilha, a interface e o programa cliente não mudam, apenas a implementação (Pilha.c) muda.

**Módulo de interface**
```
#ifndef PILHA_H
	#define PILHA_H
	#include <stdbool.h>

	typedef struct pilha_ PILHA;

	PILHA *pilha_criar(void);
	void pilha_apagar(PILHA **pilha);
	bool pilha_vazia(PILHA *pilha);
	bool pilha_cheia(PILHA *pilha);
	int pilha_tamanho(PILHA *pilha);
	ITEM *pilha_topo(PILHA *pilha);
	bool pilha_empilhar(PILHA *pilha, ITEM *item);
	ITEM *pilha_desempilhar(PILHA *pilha);
	void pilha_print(PILHA *p);
	void pilha_inverter(PILHA *p);
#endif
```
**Módulo de implementação**
```
struct pilha_ {
	NO* topo;
	int tamanho;
}

PILHA* pilha_criar(void){
	PILHA* p = (PILHA*) malloc(sizeof(PILHA));

	if((p = (PILHA*) malloc(sizeof(PILHA))) != NULL){
		p->topo = NULL;
		p->tamanho = 0;
	}
}

bool pilha_empilhar(PILHA* p, ITEM* it){
	if(!pilha_cheia(p)){
		NO* aux;
		aux = (NO*) malloc(sizeof(NO));

		if(aux != NULL){
			aux->item = it;
			aux->anterior = pilha->topo;
			p->topo = aux;
			p->tamanho++;
			return true;
		}

		return false;
	}
	
}

ITEM* pilha_desempilhar(PILHA* pilha){
	if((pilha != NULL) && (!pilha_vazia(pilha))){
		NO* pno = pilha->topo;
		ITEM* item = pilha->topo->item;

		pilha->topo = pilha->topo->anterior;
		pno->anterior = NULL;
		free(pno);
		pno = NULL;
		pilha->tamanho--;
		return item;
	}
	return NULL;
}
```
Nessa implementação não existe indexação.
Além disso, a vantagem dessa implementação é:
- Não tem que saber a quantidade de dados previamente
A desvantagem é:
- O código fica mais complexo
- Não tem acesso indexado
## Sequencial x Encadeada
![Imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-22%2013-00-19.png)
Na sequencial, há um array de ponteiros para itens, por isso, terei que percorrer o vetor para apagar os itens, por causa disso é O(n), depende de n (isso ocorre porque usamos o TAD item, se tivesse usado um tipo sem ser de ponteiro, não precisaríamos percorrer ele todo, daria um free no array maior só). Na encadeada é a mesma coisa, só que para os nós.
### Sequencial
- Implementação simples
- Tamanho da pilha definido a priori
### Encadeada
- Alocação dinâmica permite gerenciar melhor estruturas cujo tamanho não é conhecido a priori ou que variam muito de tamanho
## Aplicação de pilhas
### Avaliação de expressões aritméticas
#### Notação Infixa
Ela é ambígua. Tem a necessidade de precedência de operadores ou utilização de parênteses. Sintaxe: A + B * C.
#### Notação Polonesa (prefixa)
Os operadores precedem os operandos. Ela dispensa o uso de parênteses. Sintaxe: - * AB/CD (expressão: (A  * B) - (C / D)).
#### Notação Polonesa Reversa (posfixa)
Os operadores sucedem os operandos. Ela dispensa o uso de parênteses. Sintaxe: AB * CD /- (expressão: (A * B) - (C / D)).
Expressões nessa notação podem ser avaliadas usando pilhas. A expressão é avaliada da esquerda para direita. Os operandos são empilhados. Os operadores fazem com que: dois operandos sejam empilhados, o cálculo realizado e o resultado empilhado.
### Sequência de parênteses e chaves
Dada uma sequência de parênteses, ela pode ser bem formada: ( ( ) { ( ) } ), ou mal formada: ( { ) }.
## Extra
A flag -I no Makefile serve para especificar o caminho dos arquivos .h (para quando eles estão em outra pasta).
# Filas (Queue) e Deques
Quando há uma competição por recursos em programação, é normal usar uma fila.
## O que é?
É uma estrutura para armazenar um conjunto de elementos, que funciona da seguinte forma:
- Novos elementos sempre entram no fim da fila
- O único elemento que se pode retirar da fila em um dado momento é seu primeiro elemento
## Para que serve?
Modelar situações em que é preciso armazenar um conjunto ordenado de elementos, no qual o primeiro elemento a entrar no conjunto será também o primeiro elemento a sair do conjunto e assim por diante. Política FIFO: First-In/First-Out.
## Operações Principais
- fila_criar(): cria uma fila F vazia (aloca espaço para fila e retorna o endereço)
- fila_inserir(fila, x): insere o elemento x no final da fila. Retorna true se foi possível inserir e false caso contrário.
- fila_remover(fila): remove o elemento no início da fila e retorna esse elemento. Retorna NULL se não foi possível remover.
## Operações Auxiliares
- fila_frente(fila): retorna o elemento no início da fila, sem remover
- fila_tamanho(fila): retorna o número de elementos da fila
- fila_vazia(fila): indica se a fila está vazia
- fila_cheia(fila): indica se a fila está cheia (útil para implementações estáticas)
## Implementação
## Sequencial
Os elementos da fila ficam, necessariamente, em sequência (um do lado do outro), na memória. Todo o espaço reservado permanece reservado durante todo o tempo de execução do programa, independentemente de estar sendo efetivamente usado ou não.
**Início:** aponta para/indica o primeiro da fila, ou seja, o primeiro elemento a sair.
**Fim:** aponta para/indica o fim da fila, ou seja, onde o próximo elemento estará.
Podemos manter o início fixo e sempre fazer um shift para esquerda quando removemos um elemento ($O(n)$), e quando adicionamos mudamos o fim($O(1)$). Isso é custoso porque quando tivermos arrays grandes irá demandar muito. 
Para não ter esse problema, faz-se uma implementação circular. Ou seja, fazer com que o início não seja fixo na primeira posição do vetor. Pode-se permitir que Fim volte ao início do vetor quando esse contador atingir o final do vetor. Essa implementação é conhecida como fila circular. Para isso deve-se ver a fila como um anel (fila circular). Também deve-se ter um campo extra para guardar o número de elementos, a fim de evitar problemas com as verificações de vazio e cheio. Não há diferença de fila sequencial e fila circular, por isso vale mais a pena implementar uma fila circular.
~~~C
#include "fila.h"

struct fila_{
	ITEM* fila{TAM_MAX};
	int inicio; // Posição do 1º elemento da fila
	int fim; // Posição do último elemento da fila
	int tamanho;
}
~~~
## Encadeada
O módulo de interface é o mesmo da implementação dinâmica. A implementação encadeada utiliza o nó. Há também uma mudança na estrutura da fila, que passará a usar um ponteiro para o início e um para o fim.
~~~C
struct no{
	ITEM *item;
	NO *proximo;
}

struct fila_{
	NO *inicio;
	NO *fim;
	int tamanho;
}
~~~
# Listas
## Listas Lineares Sequenciais
Uma lista linear é uma sequência de componentes de um mesmo tipo. É uma sequência de zero ou mais itens $x_1, x_2,\, ... , x_n$ na qual $x_i$ é de um determinado tipo e $n$ representa o tamanho da lista.
Sua principal propriedade estrutural diz respeito às posições relativas dos itens:
- Se $n \geq 1$, $x_1$ é o primeiro item e $x_n$ é o último (considerando que a indexação inicia a partir de 1)
- Em geral, $x_i$ precede $x_{i+1}$ para $i = 1, 2, \, ... \, , n-1$ e $x_i$ sucede $x_{i-1}$ para $i = 2, 3, \, ... \, , n$.
### Operações
As operações mais frequentes em listas são a busca, a inclusão e a remoção de um determinado elemento.
Outras operações: alteração de um elemento da lista, combinação de duas ou mais listas lineares em um única, ordenação dos nós segundo um determinado campo, determinação do primeiro ou último elemento da lista, etc.
### Aplicação
Diversos tipos de aplicações requerem uma lista:
- Informações sobre funcionários de uma empresa
- Notas de compras
- Itens do estoque
- Notas dos alunos
- Lista telefônica
- Lista de tarefas
- Gerenciamento de memória
- Simulações em geral
- Compiladores, etc
### Casos Particulares de Listas
- Deque (Double Ended QUEue): se as inserções e remoções são permitidas apenas nas extremidades da lista
- Pilha (Stack): se as inserções e remoções são realizadas somente em um extremo
- Fila (Queue): se as inserções são realizadas em um extremo e as remoções em outro.
### Como escolher o tipo de lista?
Escolher entre uma ou outra organização de memória (sequencial ou encadeada) vai depender do comportamento da lista na aplicação (tamanho, operações mais frequentes, etc.).
A eficiência das operações depende da organização usada e de outros fatores: se a lista está ordenada, se é grande ou pequena, etc.
Escolhe-se a partir da operação mais frequente. Por exemplo, a operação de busca é melhor na ordenada, então se ela for a mais frequente usa-se a lista ordenada.
### TAD Lista
Vamos definir um TAD com as principais operações sobre uma lista. Para simplificar vamos definir apenas as operações podem ser definidas:
- Criar lista
- Inserir item (última posição)
- Remover item (última posição)
- Recuperar item (dada uma chave)
- Contar número de itens
- Verificar se a lista está vazia
- Verificar se a lista está cheia
- Imprimir lista
### Módulo de interface
~~~C
#ifndef LISTA_H
	#define LISTA_H
	
	#define TAM_MAX 100 /*Estimativa do tamanho máximo da lista*/
	#define inicial 0
	#define ERRO -32000
	#define ORDENADA 0 /*0 = lista não ordenada; 1 = lista ordenada*/
	#include "item.h"

	typedef struct lista_ LISTA;

	LISTA *lista_criar(void);
	bool lista_inserir(LISTA *lista, ITEM *item);
	bool lista_apagar(LISTA **lista);
	ITEM *lista_remover(LISTA *lista, int chave);
	ITEM *lista_busca(LISTA *lista, int chave);
	int lista_tamanho(LISTA *lista);
	bool lista_vazia(LISTA *lista);
	bool lista_cheia(LISTA *lista);
	void lista_imprimir(LISTA *lista);

#endif
~~~
### Implementação Sequencial da Lista Não Ordenada
É um array de ponteiros para item.
Características:
- Os itens da lista são armazenados em posições contíguas de memória
- A lista pode ser percorrida em qualquer direção
- A inserção de um novo item pode ser realizada após o último item com custo constante
Abaixo tem a implementação de uma lista sequencial não ordenada
~~~C
#include "lista.h"
#include <stdbool.h>
#include <stdlib.h>

struct lista_ {
	ITEM *lista[TAM_MAX];
	int inicio; // Início da lista
	int fim; // Fim da lista -1a posição livre para inserção
	int tamanho;
}

LISTA *lista_criar(void){
	LISTA *lista = (LISTA *) malloc(sizeof(LISTA));

	if(lista != NULL){
		lista->inicio = inicial;
		lista->fim = lista->inicio; // Para lista vazia
	}

	return lista;
}

// A implementação abaixo é para uma lista não ordenada, pois ele adiciona no fim por padrão. A implementação de inserir no início é a mesma só trocando pelo inicio.
bool lista_inserir_fim(LISTA *lista, ITEM *item){
	if((lista != NULL) && (!lista_cheia(lista))){
		(lista->lista[lista->fim]) = item;
		lista->fim++;
		lista->tamanho++;
		return true;
	}

	return false;
}

bool lista_inserir_posicao(LISTA *l, int pos, ITEM *item){
	int i;

	if(!lista_cheia(l) && (pos <= l->fim - 1)){
		for(i = (l->fim-1); i >= pos; i--){
			l->lista[i+1] = l->lista[i];
		}

		l->lista[pos] = item; // insere novo item
		l->fim++; // incrementa tamanho
		l->tamanho++;

		return true;
	} else{
		return false;
	}

	// (fim-pos) + 1 deslocamentos (cópia dos registros!)
}
~~~
Podemos criar um 4º campo na lista (struct lista_) para especificar se ela é ordenada ou não. Nesse caso, quando criarmos uma lista, teremos um parâmetro para a função que será um booleano para representar se é ordenado ou não. Isso implicará em como iremos implementar as outras funções.
A inserção no fim serve para lista não ordenada. Para lista ordenada não vale isso pois não há garantir que ao adicionar o item no fim a lista continuará ordenada.
Ao inserir no meio da lista, teremos um problema de deslocamento dos itens, pois ao colocar o item na posição n, todos os elementos na posição n+1 até o final terão que ser deslocados. O procedimento: achamos a posição (estará ocupada), pegamos o elemento no i e copiamos para o i+1 e assim em diante. Uma dica para fazer isso é começar pelo final e ir até o i+1. O problema disso é que ele é custoso, justamente por isso que quando a lista é não ordenada, insere-se no fim.
### Lista Ordenada
Características:
- Uma lista pode ser mantida em ordem crescente/decrescente segundo o valor de alguma chave
- Essa ordem facilita a pesquisa/busca de itens
- Por outro lado, a inserção e remoção são mais complexas pois deve manter os itens ordenados.
### TAD Lista Ordenada
O TAD da lista ordenada é o mesmo do TAD lista, apenas difere na implementação. As operações diferentes serão a inserção, remoção e busca (recuperação) de itens.
### Implementação Sequencial da Lista Ordenada
Usa as mesmas funções da não ordenada, porém fazemos a função inserir servir para os dois tipos de busca.
~~~C
bool lista_inserir(LISTA *l, ITEM *item){
	if(!ORDENADA){
		return (lista_inserir_fim(l, item));
	} else{
		int x = lista_busca_ordenada(l, item_get_chave(item));

		return lista_inserir_posicao(lista, x, item);
	}
}
~~~
### Busca em Listas Sequenciais
Uma tarefa comum a ser executada sobre listas é a busca de itens dada uma chave. No caso da lista não ordenada, a busca será sequencial (consultar todos os elementos). Porém, com uma lista ordenada, diferentes estratégias podem ser aplicadas que aceleram a busca:
- Busca sequencial "otimizada"
- Busca binária
Na busca sequencial (ideal para lista não ordenada), a ideia é procurar um elemento que tenha uma determinada chave, começando do início da lista, e parar quando a lista terminar ou quando o elemento for encontrado. Código:
~~~C
int lista_busca_sequencial(LISTA *l, int x){
	int i;

	if(l != NULL && (!lista_vazia(l))){
		for(i = 0; i < l->fim; i++){
			if(item_get_chave(l->lista[i]) == x){
				return i;
			}
		}
	}
	return ERRO;
}
~~~
A função buscar na lista ordenada tem como pré-condição uma chave c válida é informada