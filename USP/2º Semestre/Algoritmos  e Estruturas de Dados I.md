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
<br>
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
Para a fila, surgem alguns problemas, pois usando dois vetores,conforme removesse elementos e acrescentasse a posição do rear, ele chegaria ao final do vetor, mesmo removendo os elementos da fila e, assim, não seria possível adicionar mais elementos.
<br>
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
