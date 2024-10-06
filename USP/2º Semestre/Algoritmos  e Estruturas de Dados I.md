O livro de referência usado nesse estudo foi: 
>Estrutura de Dados Usando C
>Aaron Ai Tenenbaum, Yedidyah Langsam, Moshe J. Augenstein
# Tipo Abstrato de Dado (TAD ou TDA)
É um conjunto de valores e um conjunto de operações que podem ser realizadas sobre esses valores. Ele é um modelo para representar um tipo de dado estruturado.
# Pilha (Stack)
É um conjunto ordenado de itens, no qual podem ser adicionados novos itens ou retirados itens da pilha, através de uma extremidade chamada topo, que fica no final do conjunto. Ela é um objeto dinâmico e constantemente mutável. <br>
O conceito de pilha compreende a inserção e remoção dos itens. <br>
Ao acrescentar um item o topo da pilha move-se para cima, apontando para o novo topo. Ao remover um item da pilha, o topo move-se para baixo, apontando para o novo topo da pilha. <br>
O último elemento a ser inserido é o primeiro a ser eliminado. Isso é conhecido como político LIFO (Last-In/First-Out). <br>
A pilha não possui um registro dos itens que estiveram nela e saíram. <br>
A pilha pode ser implementada de duas formas: sequencial (possui um limite de itens) ou encadeada (não possui limite de itens (exceto o limite físico da memória)).
## Operações Principais
- push(Pilha, item): empilho/adiciono o item na Pilha. Conhecida como empilhar.
- pop(Pilha): desempilho/retorno o item do topo da Pilha e removo ele da Pilha. Conhecida como desempilhar.
- empty(Pilha): retorna verdadeiro se a pilha está vazia, e falso se não estiver. Conhecida como vazia.
- full(Pilha): retorna verdadeiro se a pilha está cheia, e falso se não estiver. Conhecida como cheia.
## Operações Secundárias
- stacktop(Pilha): retorna o item do topo da pilha sem removê-lo. Conhecida como topo. Ela pode ser decomposta em um pop seguido de um push. Ele não é definido para uma pilha vazia.
- criar(void): cria uma pilha vazia e retorna ela.
- apagar(Pilha): apaga a pilha da memória.
- tamanho(Pilha): retorna quantos elementos tem na pilha.

É conhecido como underflow a tentativa, inválida, de acessar a memória/desempilhar uma pilha vazia. <br>
Uma pilha é usada para casos em que o último a entrar é o primeiro a sair ou então casos de padrão de agrupamentos.
## Implementação Estática
Utiliza um vetor estático para implementar a pilha.
## Implementação Dinâmica
Utiliza uma estrutura chamada nó para implementar a estrutura, esse nó possui como um dos seus componentes um ponteiro para um outro nó, desse modo, não há um limite igual o vetor estático (exceto o limite físico da memória). Exemplo de um nó:
~~~C
typedef struct no{
	ITEM* item;
	NO* anterior;
} NO;
~~~
A vantagem dessa implementação é que não precisa saber o número de itens previamente. A desvantagem é que fica mais complexo e também não é possível acessar por indexação. <br>
A implementação da estrutura fica:
~~~C
typedef struct pilha{
	NO* topo;
	int tamanho;
} Pilha;
~~~
A lógica é que iremos ter um nó fixo chamado topo e criaremos novos nós conforme adicionarmos um novo item, aí muda-se o ponteiro do topo para o novo nó e seta o ponteiro do novo nó para o espaço de memória que anteriormente era o último elemento.
# Filas
A fila é um conjunto de dados, no qual os elementos são retirados por uma extremidade, denominada início da fila, e são adicionados por outras extremidade, denominada final da fila. <br>
O primeiro elemento a ser inserido é o primeiro a sair. Isso é conhecido como política FIFO (First-In/First-Out). <br>
Não ha limite para o número de elementos de uma fila. <br>
## Operações Principais
- insert(Fila, item): insere o item no final da fila. Denominada por inserir.
- remove(Fila): remove o primeiro elemento (do início) da fila, e retorna ele. Denominada por remover.
- empty(Fila): retorna verdadeiro se a fila está vazia e falso caso contrário. Denominada por vazia.
- criar(void): retorna um ponteiro para uma fila (aloca espaço para a fila e retorna o endereço).
## Operações Secundárias
- full(Fila): retorna verdadeiro se a fila está cheia (ou no caso de implementação dinâmica, se não há mais espaço de memória) e falso se não estiver. Denominada como cheia.
- frente(Fila): retorna o elemento no início da fila sem removê-lo.
- tamanho(Fila): retorna o número de elementos da fila. <br>
A ideia é usarmos dois vetores, chamados de front (para representar o início) e rear (para representar o final). <br>
Para a fila, surgem alguns problemas, pois usando dois vetores, conforme removesse elementos e acrescentasse a posição do rear, ele chegaria ao final do vetor, mesmo removendo os elementos da fila e, assim, não seria possível adicionar mais elementos.

Por isso adota-se a estratégia de quando retirar um elemento do início, deslocar todos os outros elementos para frente. Com essa estratégia, não necessita mais do ponteiro front, pois ela está fixa no 0. Entretanto, nessa implementação, para filas com diversos elementos, quando removesse um único elemento, seria necessário deslocar diversos elementos, o que possui um custo alto. <br>
Para melhorar a implementação, pode-se visualizar o vetor como um círculo (fila circular). Nessa implementação, sempre haverá um espaço para implementar um novo elemento, desde que o elemento seguinte esteja vazio (quando o contador atingir o fim do vetor, o ponteiro do fim será setado para o início). E não é mais necessário deslocar todos os elementos quando retirar um, pois, utilizando novamente um ponteiro para o início, é necessário deslocá-lo para a próxima posição. A desvantagem dessa implementação é que ela torna difícil determinar quando a fila está vazia. A condição para que a fila esteja vazia é que o ponteiro front seja igual ao ponteiro rear. <br>
## Implementação Sequencial/Circular
Os elementos ficam um do lado do outro (em sequência) na memória. Os elementos ocupam a memória o tempo todo de execução do programa. <br>
De modo semelhante a pilha, essa implementação tem a desvantagem de ter um limite para o número de elementos, de modo que se passar o limite haverá overflow. Nessa implementação, pode-se fazer tanto a fila sequencial quanto a circular, como não há diferença de custo nos dois métodos, vale mais a pena usar a circular. <br>
Pensando na implementação circular, além do ponteiro de início e fim, é necessário um inteiro para armazenar o tamanho (quantidade de elementos) a fim de evitar problemas com as verificações de cheio e vazio (nesse caso a condição mencionada acima não será necessária, bastando verificar somente o número de elementos). Abaixo segue um exemplo de implementação da fila circular:
~~~C
struct fila_{
	ITEM* fila{TAM_MAX};
	int inicio; // Posição do 1º elemento da fila
	int fim; // Posição do último elemento da fila
	int tamanho;
}
~~~

## Filas Dinâmicas Encadeadas
A implementação encadeada faz uso de dois ponteiros, um para o início e um para o fim, permitindo ter um acesso direto as posições de inserção e remoção.

As operações são as mesmas, com a diferença que as operações de inserir e remover são mais eficientes. Deve-se também tomar cuidado para que os ponteiros para o início e o fim tenham valor NULL quando a lista for vazia.

Como foi usada alocação dinâmica, não é necessário ter o tamanho da lista a priori.
# Deques
Double Ended Queue (Deque) são estruturas que permitem inserir e remover de ambos os extremos.

Algumas das suas aplicações são: sistemas de escalonamento de processos com múltiplas CPU's, verificadores de palíndromos e opções de desfazer e refazer.

## Operações Principais
- inserir_inicio(D, x): insere o elemento x no início da deque D. Retorna true se foi possível inserir e false se não foi
- inserir_fim(D, x): insere o elemento x no fim da deque D. Retorna true se foi possível inserir e false se não foi
- remover_inicio(D): remove o elemento do início de D. Retorna NULL se não foi possível remover
- remover_fim(D): remove o elemento do fim de D. Retorna NULL se não foi possível remover
## Operações Auxiliares
- primeiro(D): retorna o elemento no início de D. Retorna NULL se o elemento não existe
- ultimo(D): retorna o elemento no final de D. Retorna NULL se o elemento não existe
- contar(D): retorna o número de elementos em D
- vazia(D): indica se a deque está vazia
- cheia(D): indica se a deque está cheia

Como as deques requerem inserção e remoção, tanto do fim quanto do início, os tipos de implementações que podem ser boas são: sequencial circular e dinâmica duplamente encadeada.
# Listas
## Operações Principais
- busca/recuperar item (caso tenha mais de um item com a mesma chave, retorna a primeira aparição)
- inserir item
- remover item
- criar lista
## Operações auxiliares
- contar número de itens
- verificar se lista está vazia
- verificar se lista está cheia
- imprimir lista
- alteração de um elemento da lista
- combinação de duas ou mais listas lineares em uma única
- ordenação dos nós segundo um determinado campo
- determinação do primeiro ou último elemento da lista
- etc

Algumas aplicações das listas são:
- informações sobre funcionários de uma empresa
- notas de compras
- itens de estoque
- notas de alunos
- lista telefônica
- lista de tarefas 
- gerenciamento de memórias
- simulações em geral
- compiladores
- etc

Deques (se inserções e remoções são permitidas apenas nas extremidades), pilhas (se as inserções e remoções são realizadas somente em um extremo) e filas (se as inserções são realizadas em um extremo e remoções em outro) são casos particulares de listas.
## Organização em memória
As listas podem ser classificadas quanto a posição dos elementos na memória. Ela é classificada como sequencial se o sucessor de um elemento ocupa posição fixa consecutiva na memória (endereços consecutivos), elas fazem o uso de arrays (estática). E ela também pode ser classificada como encadeada se elementos consecutivos não implicam em endereços consecutivos na memória e elas usam ponteiros (dinâmica).

## Ordenação
Qualquer que seja o tipo de organização, a lista pode diferir quanto a ordenação. A lista é dita ordenada se os elementos são ordenados segundos valores do campo chave e, eventualmente, de outros campos. E a lista é dita não ordenada se os elementos não possuem uma relação de ordem entre si.

Em listas ordenadas, ao realizar a inserção de um valor, é necessário inserí-lo em um local específico de modo a manter a ordem. Tal cuidado não é necessário inserir em listas não ordenadas e por isso, e também por ser mais barato, adiciona-se no final.
## Lista Ordenada
As características da lista ordenada são:
- A lista é mantida em ordem crescente ou descrente de acordo com o valor de uma chave
- Essa ordem facilita a pesquisa de itens
- Porém a inserção e remoção são mais complexas pois deve manter os itens ordenados

O TAD de uma lista ordenada é o mesmo da lista não ordenada, só a implementação que se difere. As operações diferentes serão a inserção, remoção e busca e itens.

Para inserir um item mantendo a ordenação é necessário fazer uma busca que retorna a posição desejada.
## Listas Lineares Sequenciais
Uma lista linear é uma sequência de elementos do mesmo tipo. Sua principal propriedade diz respeito as posições relativas dos itens: 
- Se $n \geq 1$, $x_{1}$ é o primeiro item e $x_{n}$ é o último
- Em geral, $x_{i}$ precede $x_{i+1}$ para $i = 1, 2, ..., n-1$ e $x_{i}$ sucede $x_{i-1}$ para

As características dessa implementação são:
- Os itens da lista são armazenados em posições contíguas da memória
- A lista pode ser percorri em qualquer direção
- A inserção de um novo item pode ser realizada após o último item com custo constante

Nesse tipo de implementação há um problema quando se quer inserir um item no meio da lista, pois terá que deslocar em uma casa todos os itens a frente da posição desejada.

A busca em listas sequenciais é uma tarefa comum a ser executada sobre listas. No caso de uma lista não ordenada, a busca será sequencial. Porém em uma lista ordenada, diferentes estratégias podem ser aplicadas, entre elas: busca sequencial otimizada ou busca binária.

Em uma busca sequencial, a ideia é procurar um elemento que tenha uma determinada chave, começando do início da lista e parando somente quanto encontrar a chave ou a lista terminar. Ela funciona com vetores ordenados ou não.

Caso a lista seja ordenada, é possível otimizá-la. Para isso, paramos antes a busca caso ela encontre um elemento maior do que a chave, já que por estar ordenada, se um elemento é maior que a chave, é garantido que ela não estará depois dele. Porém essa melhoria não altera a complexidade da busca que é $O(n)$.

Por último, a busca binária é um algoritmo de busca mais sofisticado e bem mais eficiente que a busca sequencial. Entretanto ela somente pode ser aplicada em estruturas que permitem acessar cada elemento em tempo constante, tais como vetores (então em listas encadeadas não é possível usá-las). A ideia é a cada iteração dividir o vetor ao meio e descartar a metade que não contém o valor desejado. É importante lembrar que ela só funciona com vetores ordenados. A complexidade dela é $O(\log{n})$.

Já a remoção também possui diferenças dependendo se a lista é ou não ordenada. Se a lista não é ordenada, pode-se dividir a remoção em três casos:
- Remover do fim: custo constante
- Remover do início: requer deslocamentos
- Remover do meio:
	- Item qualquer, desde que esteja no meio exato da lista, requer deslocamentos
	- Item com chave específica que pode estar em qualquer posição da lista, requer uma busca e pode precisar de deslocamentos (se o item não estiver no fim).

Já em listas ordenadas, a remoção não pode alterar a ordem. Aqui também pode-se remover em três casos:
- Remover do fim: custo constante
- Remover do início: requer deslocamentos
- Remover do meio: igual ao anterior

Logo, a lista linear sequencial tem as seguintes vantagens: tempo constante de acesso as dados e simplicidade. Já de desvantagens, ela tem: custo para inserir e retirar elementos da lista dada uma posição (devido os deslocamentos), a lista ordenada (busca facilitada e inserções/remoções implicam em deslocamentos) e o tamanho máximo da lista é definido em tempo de compilação (depende da linguagem).

Esse tipo de implementação é comumente utilizado quando:
- Se tem listas pequenas
- O tamanho máximo é conhecido
- Se tem poucas ocorrências de utilização de métodos de inserção e remoção
## Listas Lineares Simplesmente Encadeadas
As listas encadeadas fazem uso de ponteiros para estruturas conhecidas como nós. Esse tipo de implementação torna as operações de inserção e remoção mais eficientes. Além disso, não é necessário informar previamente o número de elementos da lista (ou seja, não é necessário informar em tempo de compilação). E, também, ele possui o mesmo TAD que as listas anteriores.

A forma como será implementada é:
~~~C
~~~C
typedef struct no NO;
struct no{
	ITEM* item;
	NO* proximo;
}

struct lista{
	NO* inicio;
	NO* fim;
	int tamanho;
	bool ordenada
}
~~~

Convenciona-se também que a variável ponteiro da lista deve ter valor NULL quanto a lista estiver vazia. Logo ela deve ser inicializada e também deve ter uma forma de verificar se ela está vazia.

Nesse tipo de implementação, por não depender de vetores, não há um tamanho final já estabelecido para a lista. Porém a memória heap não é ilimitada e é sempre importante verificar se existe memória disponível ao chamar a função malloc (em C é atribuído NULL ao ponteiro se a memória não está disponível).

Pode-se melhorar a lista encadeada simples usando alguns outros algoritmos: 
- Listas Encadeadas Circulares
- Nó-cabeça
- Listas Ordenadas
### Listas Encadeadas Nó-Cabeça
## Listas Duplamente Encadeadas
Nas listas duplamente encadeadas, cada nó mantém um ponteiro para o nó anterior e o posterior. A manipulação da lista é mais complexa, porém algumas operações são diretamente beneficiadas. Por exemplo: as operações de inserção e remoção em uma dada posição. A interface é a mesma das outras listas.

As listas duplamente encadeadas são usadas em qualquer aplicação que necessite de navegação em dois sentidos, como playlists de músicas (skip e back).

Já a implementação possui algumas diferenças:
~~~C
typedef struct no_ NO;
struct no_{
	ITEM* item;
	NO* anterior;
	NO* proximo;
}
struct lista_{
	NO* inicio;
	NO* fim;
	int tamanho;
	bool ordenada;
}

LISTA* lista_criar(bool ordenada){
	LISTA* lista = (LISTA*) malloc(sizeof(LISTA));
	if(lista != NULL){
		lista->inicio = NULL;
		lista->fim = NULL;
		lista->tamanho = 0;
		lista->ordenada = ordenada;
	}

	return lista;
}

void lista_esvazia(NO* p){
	if(p != NULL){
		if(p->proximo != NULL){
			lista_esvazia(p->proximo);
		}

		item_apagar(&p->item);
		p->anterior = NULL;
		free(p);
		p = NULL;
	}
}

void lista_apagar(LISTA** p){
	if(*p = NULL){
		return;
	}
	lista_esvazia((*p)->inicio);
	free(*p);
	*p = NULL;
}
~~~
As mudanças aparecem na inserção e remoção praticamente. 
