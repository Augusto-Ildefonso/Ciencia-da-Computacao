O livro de referência usado nesse estudo foi: 
>Estrutura de Dados Usando C
>Aaron Ai Tenenbaum, Yedidyah Langsam, Moshe J. Augenstein
# Tipo Abstrato de Dado (TAD ou TDA)
É um conjunto de valores e um conjunto de operações que podem ser realizadas sobre esses valores. Ele é um modelo para representar um tipo de dado estruturado.
# Pilha (Stack)
É um conjunto ordenado de itens, no qual podem ser adicionados novos itens ou retirados itens da pilha, através de uma extremidade chamada topo, que fica no final do conjunto. Ela é um objeto dinâmico e constantemente mutável. <br>
O conceito de pilha compreende a inserção e remoção dos itens. <br>
Ao acrescentar um item o topo da pilha move-se para cima, apontando para o novo topo. Ao remover um item da pilha, o topo move-se para baixo, apontando para o novo topo da pilha. <br>
O último elemento a ser inserido é o primeiro a ser eliminado. Isso é conhecido como política LIFO (Last-In/First-Out). <br>
A pilha não possu  i um registro dos itens que estiveram nela e saíram. <br>
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
## Listas Encadeadas com Nó-Cabeça
Em listas encadeadas a operação mais complexa é a remoção de um elemento a partir de uma chave. Isso porque o algoritmo precisa apontar para o item anterior ao que será removido, o que, no caso da remoção do primeiro elemento, necessita de uma condicional pois é uma exceção que necessita ser tratada a parte.

Para solucionar isso usa-se o nó-cabeça, nesse modelo o ponteiro que aponta para o início irá apontar para o nó-cabeça e esse apontará para o início. Desse modo sempre será possível usar o algoritmo de apontar para o próximo, até mesmo para o elemento do início.
~~~C
struct lista{
	NO* cabeca;
	NO* fim;
	int tamanho;
	bool ordenada
}
~~~

A implementação é do criar lista, do lista vazia e do remover mudam um pouco mas tirando elas, as outras implementações são bem parecidas. De modo que a única alteração é mudar as referências ao ponteiro do inicio para o ponteiro cabeça.

Nesse modelo, a remoção de um elemento é melhorada.
## Listas Encadeadas Circulares
Nessa implementação é substituída a ideia de que o próximo do último elemento é NULL para que o próximo do último elemento seja o primeiro. Esse modelo é interessante pois a partir de um nó qualquer da lista pode-se chegar até qualquer outro nó.

Nessa implementação não é necessário um ponteiro para o início da lista, somente para o fim. Além disso, junto da ideia circular, será implementado um nó sentinela que faz papel parecido com o nó cabeça, só que ele guarda como informação a chave. Começa-se a busca pelo primeiro nó e vai até o último nó, se chegar nele e não achar a chave, ele vai analisar o nó sentinela como próximo e resultará que a busca não teve sucesso. Nesse modelo é economizado um teste, já que não precisa testar se a lista acabou e também ele melhora a busca.
## Listas Encadeadas Ordenadas
Esse modelo não requer um ponteiro de fim, pois a inserção será feita em qualquer posição da lista. Novamente o emprego do nó cabeça facilita a implementação uma vez que  vamos buscar a posição anterior à de inserção, e no caso de ser o menor item da lista não representará exceção.

Além disso, esse modelo traz vantagens para a busca que por ser ordenada, podemos pará-la se achar um valor maior que a chave, não sendo preciso procurar até o final dela.
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

# Árvores
As árvores tem uma organização dos dados de forma não-linear mantendo um relacionamento hierárquico entre seus elementos. Diferente da lista que tem uma organização linear dos dados, onde sua propriedade básica é a relação sequencial mantida entre seus elementos.

Essa estrutura hierárquica permite limitar o local da busca, reduzindo, assim, a complexidade. Logo, a operação beneficiada pelo uso de árvores é a busca.

As vantagens desse tipo de representação são:
- Representatividade no relacionamento entre os dados
- Facilidades na manipulação computacional dos dados
- Uma maior facilidade de extração de informações, dependendo de que tipo de dado estará sendo armazenado pela árvore

Para extrair informações específicas de uma determinada ramificação da árvore não é necessário o percurso por toda estrutura de informação. Isso porque o relacionamento entre os dados nos permite uma consulta seletiva em regiões específicas da árvore. Isso implica em uma possibilidade de unir a vantagem da implementação encadeada com busca binária (em árvores binárias).

## Definição
Uma árvore enraizada $T$ é um conjunto finito de elementos denominados **nós** ou vértices tais que:
- $T = \emptyset$, a árvore é dita vazia
- $T = \{r\} \bigcup \{T_{1}\} \bigcup \{T_{2}\} \bigcup \{T_{3}\} \bigcup ... \bigcup \{T_{n}\}$ 

Um nó especial da árvore, *r*, é chamado de raiz da árvore. Os elementos restantes da árvore constituem um único conjunto vazio ou são divididos em $n \geq 1$ conjuntos disjuntos não vazios, $T_{1}, T_{2}, T_{3}, ..., T_{n}$, as subárvores de *r*, cada qual por sua vez é uma árvore.

Assim, para denotar uma árvore qualquer usamos $T = \{ T_{1}, T_{2}, T_{3}, ...,  T_{n} \}$, com *r* a raiz da árvore e $T_{v}$ a subárvore $T$ com raiz em *v*. Note que a definição apresentada é recursiva.
## Representação Gráfica para Árvores
A estrutura de árvore pode ser presentada graficamente de diversas maneiras, dentre elas:
- Conjuntos aninhados
	![[Pasted image 20241130170406.png]]
- Indentação
	![[Pasted image 20241130170719.png]]
- Grafos (a mais utilizada)
![[Pasted image 20241130171016.png]]
- Aninhada
	$T_{c} = \{ D, \{E, \{F\}\}, \{ G, \{ H, \{I\} \}, \{ J, \{K\}, \{L\} \}, \{M\}  \} \}$
## Terminologias
Considerando a árvore $T_{c}$ e a definição dada de árvores anteriormente, vejamos algumas terminologias básicas:
- **Grau de um nó**: é o número de subárvores relacionadas àquele nó. Se um nó não tiver nenhuma subárvore relacionada à ele, ele tem grau 0
- **Nó folha ou terminal**: é o nó com grau igual a zero, ou seja, que não possui subárvores
- **Grau da árvore**: ele é relacionado à uma limitação que se impõe a uma árvore, então se a árvore possui um grau máximo e todos os nós possuem o mesmo grau máximo, esse grau máximo será o grau da árvore

Para identificar os nós na estrutura, usamos denominações da relação hierárquica existente em uma árvore genealógica:
- Cada raiz $r_{i}$ da subárvore $T_{i}$ é chamada **filho** de r. O termo neto é usado de forma análoga
- O nó raiz $r$ da árvore $T$ é o **pai** de todas as raízes $r_{i}$ das subárvores $T_{i}$. O termo **avô** é definido de forma análoga
- Duas raízes $r_{i}$ e $r_{j}$ das sub-árvores $T_{i}$ e $T_{j}$ de $T$ são ditas **irmãs**
 
Outras definições importantes são obtidas a partir da distância de um nó em relação aos outros nós da árvore:
- **Caminho**: sequência não vazia de nós, $P = \{ r_{1}, r_{2}, ..., r_{k} \}$, onde o i-ésimo nó $r_{i}$ da sequência é pai de $r_{i+1}$
- **Comprimento**: tomando a definição de caminho, o comprimento de um caminho $P$ é igual a $k - 1$. Ele também pode ser visto como o número de arestas que formam o caminho
- **Altura de um nó**: a altura de um nó $r_{i}$ é o comprimento do caminho mais longo do nó $r_{i}$ a uma folha. As folhas tem altura zero
- **Altura de uma árvore**: é igual a altura da raiz $r$ de $T$
- **Profundidade**: a profundidade de um nó $r_{i}$ de uma árvore $T$ é o comprimento do único caminho em $T$ entre a raiz $r$ e o nó $r_{i}$
- **Nível**: um conjunto de nós com a mesma profundidade é denominado nível da árvore. A raiz está no nível zero.

A maior profundidade da árvore será justamente a altura da árvore.

Uma forma que facilita lembrar das relações acima é pensando numa árvore real. Quando falamos de uma altura estamos falando de folhas. Já quando pensamos em raízes, elas estão enterradas e possuem uma profundidade. Mas é preciso lembrar que a árvore computacional é invertida em relação a árvore do mundo real, ou seja, a raiz fica em cima e as folhas embaixo.

Geralmente usamos as árvores para fazer busca de forma mais eficiente. Entretanto, essa busca só será eficiente se conseguirmos controlar a altura da árvore.

**Ascendência e Descendência**: considerando dois nós $r_{i}$ e $r_{j}$, o nó $r_{i}$ é um ancestral de $r_{j}$ se existe um caminho em $T$ de $r_{i}$ a $r_{j}$, tal que, o comprimento de $P$ entre $r_{i}$ e $r_{j}$ seja diferente de zero. De forma análoga se define o descendente de um nó.
## Árvores Binárias
Uma árvore binária (AB) $T$ é um conjunto finito de elementos, denominados nós ou vértices, tal que:
- Se $T = \emptyset$, a árvore é dita vazia
- Se $T$ contém um nós especial $r$, chamado raiz de $T$, e os demais nós podem ser subdivididos em dois subconjuntos distintos $T_{E}$ e $T_{D}$, os quais também são árvores binárias (possivelmente vazias)

$T_{E}$ e $T_{D}$ são denominados sub-árvore esquerda e sub-árvore direita de $T$, respectivamente.

A raiz da sub-árvore esquerda/direita de um nó $v$, se existir, é denominada filho esquerdo/direito de $v$. Pela natureza da árvore binária, o filho esquerdo pode existir sem o direito, e vice-versa.

Esse tipo de árvore é interessante para busca.

Podemos implementar a árvore binária de forma encadeada, usando as duas structs a seguir:
~~~c
struct No {
	ITEM* item;
	NO* esq;
	NO* dir;
}

struct arv_bin{
	NO* raiz;
	int profundidade;
}
~~~
Operações do TAD Árvore binária:
- Criar árvore
	- Pré-condição: nenhuma
	- Pós-condição: inicia a estrutura de dados
- Inserir um nó filho:
	- Pré-condição: nó pai não nulo
	- Pós-condição: dado um nó pai, cria seu nó filho e o insere ã direita ou a esquerda do pai. Retorna verdadeiro se o nó pode ser criado e falso caso contrário
~~~c
AB* ab_criar(void){
	AB* r = (AB*) malloc(sizeof(AB));
	if(r != NULL){
		r->raiz = NULL;
		r->profundidade = -1;
	}
	return r;
}

void ab_preordem(NO* raiz){
	if(raiz != NULL){
		item_imprimir(raiz->item);
		ab_preordem(raiz->esq);
		ab_preordem(raiz->dir);
	}
}

void ab_emordem(NO* raiz){
	if(raiz != NULL){
		ab_emordem(raiz->esq);
		item_imprimir(raiz->item);
		ab_emordem(raiz->dir);
	}
}

void ab_posordem(NO* raiz){
	if(raiz != NULL){
		ab_posordem(raiz->esq);
		ab_posordem(raiz->dir);
		item_imprimir(raiz->item);
	}
}

void ab_inserir_no(NO *raiz, NO *no, int lado, int chave_pai) {
    if (raiz != NULL) {
        ab_inserir_no(raiz->esq, no, lado, chave_pai);
        ab_inserir_no(raiz->dir, no, lado, chave_pai);

        if (chave_pai == item_get_chave(raiz->item)) {
            if (lado == FILHO_ESQ)
                raiz->esq = no;
            else if (lado == FILHO_DIR)
                raiz->dir = no;
        }
    }
    return;
}

bool ab_inserir(AB *T, ITEM *item, int lado, int chave_pai) {
    if (T->raiz == NULL)
        return ((T->raiz = ab_cria_no(item)) != NULL);
    else {
        NO *novo_no = ab_cria_no(item);
        if (novo_no != NULL) {
            ab_inserir_no(T->raiz, novo_no, lado, chave_pai);
            return true;
        }
        return false;
    }
}

int ab_profundidade(NO *no) {
    if (no == NULL) 
        return -1;

    int e = ab_profundidade(no->esq);
    int d = ab_profundidade(no->dir);

    return ((e > d) ? e : d) + 1;
}

void apagar_arvore(NO **raiz) {
    if (*raiz != NULL) {
        apagar_arvore(&(*raiz)->esq);
        apagar_arvore(&(*raiz)->dir);
        item_apagar(&(*raiz)->item);
        free(*raiz);
        *raiz = NULL;
    }
}

void ab_apagar_arvore(AB **T) {
    apagar_arvore(&(*T)->raiz);
    free(*T);
    *T = NULL;
}

~~~
#### Percursos
Muitas vezes queremos percorrer uma árvore binária "visitando" cada nó uma única vez. Nesse caso, "visitar" um nó pode ser: mostrar seu valor, modificar seu valor, etc. Um percurso gera uma sequência linear de nós e podemos então falar de nó predecessor ou sucessor de um nó, segundo um dado percurso.

Não existe um percurso único para árvores (binárias ou não): diferentes percursos podem ser realizados, dependendo da aplicação.

São três percursos básicos para árvores binárias:
- Pré-ordem (pre-order)
	- Visita a raíz
	- Percorre a sub-árvore esquerda em pré-ordem
	- Percorre a sub-árvore direita em pré-ordem
- Em-ordem (in-order)
	- Percorre a subárvore a esquerda em em-ordem
	- Visita a raiz
	- Percorre a sub-árvore a direita em em-ordem
- Pós-ordem (post-order)
	- Percorre a sub-árvore esquerda em pós-ordem
	- Percorre a sub-árvore a direita em pós-ordem
	- Visita a raiz

A diferença entre eles está, basicamente, na ordem em que os nós são "visitados".

Podemos utilizar os percursos para interpretar operações aritméticas. O percurso em-ordem representa: $a+(b \times c)$. O percurso pré-ordem representa: $+a \times bc$. Por fim o pós-ordem representa $abc\times+$. Daí, os algoritmos para cálculo podem usar pilhas.

### Árvore Estritamente Binária
Uma Árvore Estritamente Binária (ou Árvore Própria) tem nós com 0 (nenhum) ou 2 filhos. Nesse tipo de árvore os nós interiores (não folhas) sempre tem 2 filhos.
![[Pasted image 20241130183657.png]]
### Árvore Binária Completa Cheia
A árvore binária completa cheia é uma árvore estritamente binária que tem como característica todos os seus nós folha estarem no mesmo nível.
![[Pasted image 20241201151826.png]]
Dada uma árvore binária completa cheia (ABCC) e sua profundidade $d$, pode-se calcular o número total de nós na árvore por:
- Nós do último nível: $2^{d}$
- Total de nós: $2^{d+1} - 1$

Portanto, se o número de nós, $n$, para uma árvore binária completa cheia de profundidade $d$ é $n = 2^{d+1}-1$, então, $n$ nós podem ser distribuídos em uma árvore binária completa cheia de profundidade:
1. $n = 2^{d+1}-1$
2. $\log_{2}{(n+1)} = \log_{2}{(2^{d+1})}$
3. $d = \log_{2}{(n+1)}-1$

O problema com esse tipo de árvore é a necessidade de manter os níveis cheios/completos.

Para implementar esse tipo de árvore podemos adotar uma organização sequencial, de modo que vamos armazenar os nós, por nível, em um array.
### Árvore Binária Completa
A árvore binária completa (ABC) tem que se a profundidade da árvore é $d$, então cada nó folha está no nível $d-1$ ou no nível $d$. O nível $d-1$ pode estar totalmente preenchido, mas não é uma regra. Além disso, os nós folhas no nível $d$ estão todos mais à esquerda possível.

Para implementar esse tipo de árvore podemos adotar uma organização sequencial, de modo que para um vetor indexado a partir da posição 0, se um nó está na posição $i$, seus filhos diretos estão nas posições $2 \times i+1$, filho da esquerda, e $2 \times i+2$, filho da direita.

A vantagem é que vamos ocupar o espaço necessário só para armazenar o conteúdo e temos ligações implícitas. Já a desvantagem é que teremos espaços vagos se a árvore não é completa por níveis ou, então, se sofrer eliminação.
### Árvore Binária Perfeitamente Balanceada
A árvore binária perfeitamente balanceada tem que para cada nó, o número de nós de suas sub-árvores esquerda e direita difere em, no máximo, 1.
![[Pasted image 20241201153452.png]]
### Árvore Binária Balanceada
A árvore binária balanceada é caracterizada de modo que para cada nó, as alturas de suas duas sub-árvores diferem de, no máximo, 1. 

Toda árvore perfeitamente balanceada é balanceada, mas o inverso não é necessariamente verdade.
### Árvore Binária de Busca
Uma árvore binária de busca possui as seguintes propriedades:
- Seja $S=\{ s_{1}, ..., s_{n} \}$ o conjunto de chaves dos nós da árvore $T$:
	- Esse conjunto satisfaz $S_{1} < ... < S_{n}$
	- A cada nó $v_{j} \in T$ está associada uma chave distinta $s_{j} \in S$, que pode ser consultada por $r(v_{j}) = S_{j}$
- Dado um nó $v$ de $T$
	- Se $v_{i}$ pertence a sub-árvore esquerda de $v$, então $r(v_{i}) < r(v)$
	- Se $v_{i}$ pertence a sub-árvore direita de $v$, então $r(v_{i}) > r(v)$ 

Ou seja, os nós pertencentes à sub-árvore direita possuem valores de chave maiores que o valor associado à chave do nó raiz $r$. Já os nós pertencentes à sub-árvore esquerda possuem valores de chaves menores que o valor associado à chave do nó raiz $r$.

Um percurso em-ordem em uma ABB resulta na sequência de valores em ordem crescente. Se invertêssemos as propriedades descritas na definição anterior, de maneira que a sub-árvore esquerda de um nó contivesse valores maiores e a sub-árvore direita valores menores, o percurso em-ordem resultaria nos valores em ordem decrescente.

Com base no parágrafo anterior, percebemos que uma ABB criada a partir de um conjunto de valores não é única, o resultado depende da sequência de inserção dos dados.

A grande utilidade da árvore binária de busca é armazenar dados contra os quais outros dados são frequentemente verificados (busca). Uma árvore binária de busca é dinâmica e pode sofrer alterações (inserções e remoções de nós) após ter sido criada.

Quando comparamos lista com ABB, percebemos que o tempo de busca é estimado pelo número de comparações entre chaves. Por exemplo, uma lista de $n$ elementos temos: se for sequencial $O(n)$ se não ordenadas ou $O(\log_{2}n)$ se ordenadas. Já as ABB constituem a alternativa que combina a vantagem de ambos: são encadeadas e permitem a busca binária $O(\log_{2}n)$.

A inserção com ABB segue o algoritmo a seguir:
- Procure um "local" para inserir o novo nó, começando a procura a partir do nó-raiz
- Se um ponteiro (filho esquerdo/direito de um nó raiz) nulo é atingido, coloque o novo nó como sendo filho do nó raiz
- Para cada nó raiz de uma sub-árvore compare:
	- Se o novo nó possui chave menor do que a a chave do nó-raiz, vai para a sub-árvore esquerda
	- Se a chave é maior do que a chave do nó-raiz, vai para sub-árvore direita

Veja abaixo o código da inserção:
~~~C
NO *abb_inserir_no(NO *raiz, NO *novo_no){
	if (raiz == NULL)
		raiz = novo_no;
	else if(item_get_chave(novo_no->item) < item_get_chave(raiz->item))
		raiz->esq = abb_inserir_no(raiz->esq,novo_no);
	else if(item_get_chave(novo_no->item) > item_get_chave(raiz->item))
		raiz->dir = abb_inserir_no(raiz->dir,item);
	return(raiz);
}

bool abb_inserir (ABB *T, ITEM *item){
	NO *novo_no;

	if(T == NULL){
		return false;
	}

	novo_no = abb_cria_no(item)

	if(novo_no != NULL) {
		T->raiz = abb_inserir_no(T->raiz, novo_no);
		return true;
	}

	return false
}
~~~

A busca em ABB segue o algoritmo a seguir:
- Comece a busca a partir do nó-raiz
- Caso o nó pesquisado seja nulo, retorne nulo; caso o nó contendo a chave pesquisada seja encontrado, retorne o "item" do nó pesquisado
- Para cada nó-raiz de uma sub-árvore compare: se o valor procurado é menor que o valor do nó-raiz (continua pela sub-árvore esquerda), ou se o valor é maior que o valor no nó-raiz (sub-árvore direita)

Veja abaixo o código da busca:
~~~C
ITEM *abb_busca2(NO *raiz, int chave){
	if(raiz = NULL)
		return NULL;
	if (chave == item_get_chave(raiz->item))
		return raiz->item;
	if(chave < item_get_chave(raiz->item))
		return (abb_busca2(raiz->esq, chave));
	else
		return (abb_busca2(raiz->dir, chave));
}

ITEM *abb_busca(ABB *T, int chave){
	return abb_busca2(T->raiz, chave);
}
~~~

A remoção em ABB precisa considerar alguns casos no seu algoritmo:
- Caso 1: o nó é folha
	- O nó pode ser retirado sem problema
- Caso 2: o nó possui uma sub-árvore (esquerda ou direita)
	- O nó raiz da sub-árvore (esquerda ou direita) "ocupa o lugar do nó retirado"
- Caso 3: o nó possui duas sub-árvores
	- O nó contendo o menor valor da sub-árvore direita pode "ocupar" o lugar
	- Ou o maior valor da sub-árvore esquerda pode "ocupar o lugar"
~~~C
bool abb_remover_aux (NO **raiz, int chave){
	NO *p;
	if(*raiz == NULL)
		return (FALSE);
	if(chave == item_get_chave((*raiz)->item)){
		if ((*raiz)->esq == NULL|| (*raiz)->dir == NULL) {/*Caso 1 se resume ao caso 2: há um filho ou nenhum*/
			p = *raiz;
			if((*raiz)->esq == NULL)
				*raiz = (*raiz)->dir;
			else
				*raiz = (*raiz)->esq;
			free(p);
			p = NULL;
		}
		else /*Caso 3: há ambos os filhos*/
			troca_max_esq((*raiz)->esq, (*raiz), (*raiz));
		return(TRUE);
	}
	else
		if(chave < item_get_chave((*raiz)->item))
			return abb_remover_aux (&(*raiz)->esq, chave);
		else
			return abb_remover_aux (&(*raiz)->dir, chave);
}

void troca_max_esq(NO *troca, NO *raiz, NO *ant){
	if(troca->dir != NULL){
		troca_max_esq(troca->dir, raiz, troca);
		return;
	}
	if(raiz == ant)
		ant->esq = troca->esq;
	else
		ant->dir = troca->esq;

	raiz->item = troca->item;
	free(troca); troca = NULL;
}

bool abb_remover(ABB *T, int chave){
	if (T != NULL)
		return (abb_remover_aux(&T->raiz, chave));
	return (FALSE);
}
~~~

O custo da busca em ABB:
- Pior caso
	- Número de passos é determinado pela altura da árvore
	- Árvore degenerada possui altura igual a $n$
- Altura da árvore depende da sequência de inserção das chaves
- Busca é eficiente se a árvore está razoavelmente balanceada
	- $O(\log_{2}n)$

O custo da inserção em ABB:
- A inserção requer uma busca pelo lugar da chave, portanto, com custo de uma busca qualquer (tempo proporcional à altura da árvore)
- O custo da inserção, após a localização do lugar, é constante, não depende do número de nós
- Logo, tem complexidade análoga à da busca

O custo da remoção em ABB:
- A remoção requer uma busca pela chave do nó a ser removido, portanto, com o custo de uma busca qualquer(tempo proporcional à altura da árvore)
- O custo da remoção, após localização do nó dependerá de dois fatores:
	- do caso em que se enquadra a remoção: se o nó tem 0, 1 ou 2 sub-árvores, se tem 0 ou 1 filho, custo é constante
	- de sua posição na árvore, caso tenha 2 sub-árvores (quanto mais próximo do último nível, menor esse custo)
- Repare que um maior custo na busca implica num menor custo na remoção propriamente dita, e vice-versa.
- Logo, tem complexidade dependente da altura da árvore
	- Chamadas à `troca_max_esq` requerem localizar o maior elemento da sub-árvore esquerda. Mas o número de operações é sempre menor que a altura da árvore

A árvore dita como ABB "aleatória" tem as seguintes características:
- Nós externos: descendentes dos nós folha (não estão, de fato, na árvore)
- Uma árvore $A$ com $n$ nós possui $n + 1$ nós externos
- Uma inserção em $A$ é considerada aleatória se ela tem probabilidade igual de acontecer em qualquer um dos $n+1$ nós externos
- Uma ABB aleatória com $n$ nós é uma árvore resultante de $n$ inserções aleatórias sucessivas em uma árvore inicialmente vazia

É possível demonstrar que para uma ABB aleatória o número esperado de comparações para recuperar um registro qualquer é cerca de $1,39 \times \log_{2}(n)$ ($39\%$ pior do que o custo do acesso em uma árvore balanceada). Pode ser necessário garantir um melhor balanceamento da ABB para melhor desempenho na busca.

As consequências das operações de inserção e remoção são:
- Uma ABB balanceada ou perfeitamente balanceada tem organização ideal para buscas
- Inserções e eliminações podem desbalancear uma ABB, tornando futuras buscas ineficientes
- Possível solução:
	- Construir uma ABB inicialmente perfeitamente balanceada
	- Após várias inserções/eliminações, aplicamos um processo de rebalanceamento

O algoritmo para criar uma ABB perfeitamente balanceada é:
1. Ordenar num array os registros em ordem crescente das chaves
2. O registro do meio é inserido na ABB vazia (como raiz)
3. Tome a metade esquerda do array e repita o passo 2 para a sub-árvore esquerda
4. Idem para a metade direita e sub-árvore direita
5. Repita o processo até não poder dividir mais

O algoritmo para rebalanceamento:
1. Percorra em em-ordem a árvore para obter uma sequência ordenada em array
2. Repita os passos 2 a 5 do algoritmo de criação de ABB perfeitamente balanceada

Resumo:
- Boa opção como Estrutura de Dados para aplicações de pesquisa (busca) de chaves, se a árvore é balanceada temos $O(\log_{2}n)$
- Inserções (como folhas) e eliminações (mais complexas) causam desbalanceamento
- Inserções: melhor se em ordem aleatória de chaves, para evitar linearização (se ordenadas)
- Para manter o balanceamento, temos 2 opções:
	- ABB perfeitamente balanceada ou rebalancear
	- Árvores Binárias Balanceadas, por exemplo, AVL
### Árvores AVL
A árvore AVL é uma árvore binária de busca na qual as alturas das duas sub-árvores de todo nó nunca diferem em mais de 1. Ela foi proposta em 1962 pelos matemáticos russos G.M. Adelson-Velskki e E.M. Landis.

Esse tipo de árvore tem o que chamamos de "Fator de Balanceamento" de nó. Ele consiste na altura da sub-árvore esquerda menos a altura da sub-árvore direita do nó. Em uma AVL, todo nó tem fator de balanceamento igual a 1, -1 ou 0.

O problema das árvores balanceadas, de uma forma geral, é como manter a estrutura balanceada após operações de inserção e remoção. As operações de inserção e remoção sobre ABBs não garantem o balanceamento.

As seguintes situações podem levar ao desbalanceamento de uma AVL:
- O nó inserido é descendente esquerdo de um nó que tinha fator de balanceamento 1
- O nó inserido é descendente direito de um nó que tinha fator de balanceamento -1

Para manter uma árvore balanceada é necessário aplicar uma transformação na árvore tal que:
- O percurso em-ordem na árvore transformada seja igual ao da árvore original (isto é, a árvore transformada continua sendo uma ABB)
- A árvore transformada fique balanceada

A transformação que mantém a árvore balanceada é chamada de rotação. A rotação pode ser feita à esquerda ou à direita, dependendo do desbalanceamento a ser tratado. A rotação deve ser realizada de maneira a respeitar as regras 1 e 2 definidas acima. Dependendo do desbalanceamento a ser tratado, uma única rotação pode não ser o suficiente.
#### Rotação Direita
Abaixo vemos uma árvore na qual o nó mais jovem a se tornar desbalanceado é o A. Além disso $T_{1},T_{2}$ e $T_{3}$ pode ser sub-árvores de qualquer tamanho, inclusive $0$.
![[Pasted image 20241207162107.png]]
Aplicando a rotação direita, obtemos a seguinte árvore.
![[Pasted image 20241207162222.png]]
Note que nessa rotação o nó $B$ assume a posição do nó $A$, o qual passa a ser o filho direito de $B$. Já o nó que anteriormente era filho direito de $B$, agora é filho esquerdo de $A$.
#### Rotação Esquerda
Abaixo vemos uma árvore na qual o nó mais jovem a se tornar desbalanceado é o A. Além disso $T_{1},T_{2}$ e $T_{3}$ pode ser sub-árvores de qualquer tamanho, inclusive $0$.
![[Pasted image 20241207164902.png]]
Aplicando a rotação esquerda, obtemos a seguinte árvore.
![[Pasted image 20241207164938.png]]
Note que o nó $B$ ocupa agora a posição que anteriormente era do nó $A$, o qual se tornou o filho esquerdo de $B$. Além disso, a sub-árvore esquerda de $B$ antes da rotação, se tornou a sub-árvore direita de $A$ após a rotação para a esquerda.
#### Rotação Simples
Tanto para a rotação direita, quanto para a rotação esquerda, a sub-árvore resultante tem como altura a mesma altura da sub-árvore original. Isso significa que o fator de balanceamento de nenhum nó acima de $A$ é afetado. 

Devemos usar a rotação direita quando o fator de balanceamento do nó $A$ é positivo. Já quando o fator de balanceamento é negativo, usamos a rotação esquerda.
#### Rotações Duplas
As rotações simples não solucionam todos os tipos de desbalanceamentos. Existem situações nas quais é necessário uma rotação dupla. Por exemplo, se o fator de balanceamento for $0$ e inserimos um nó.

Veja abaixo um exemplo.
![[Pasted image 20241207165632.png]]
#### Rotação Esquerda/Direita
É uma rotação dupla na qual primeiro se faz uma rotação para esquerda e depois uma para direita. Vamos considerar o nó $A$ como o nó mais jovem a se tornar desbalanceado. Além disso, $T_{1}, T_{2}, T_{3}$ e $T_{4}$ podem ser sub-árvores de qualquer tamanho, inclusive $0$.
![[Pasted image 20241207165911.png]]
O primeiro passo é fazer uma rotação para a esquerda em $B$. Ao realizar essa rotação, parece que a  árvore se tornou mais ainda desbalanceada. Porém mais adiante veremos que a árvore ficará balanceada.
![[Pasted image 20241207170043.png]]
O segundo passo então é rotacionar para direita em $A$. Repare que a altura final da sub-árvore é $n+2$, ou seja, manteve intacta a altura. Isso funciona também se o nó tivesse sido inserido em $T_{3}$.
![[Pasted image 20241207170422.png]]
#### Rotação Direita/Esquerda
É uma rotação dupla na qual primeiro se rotaciona para a direita e depois para a esquerda. Vamos considerar o nó $A$ como o nó mais jovem a se tornar desbalanceado. Além disso, $T_{1}, T_{2}, T_{3}$ e $T_{4}$ podem ser sub-árvores de qualquer tamanho, inclusive $0$.
![[Pasted image 20241207170254.png]]
O primeiro passo é fazer uma rotação direita em $B$. Ao realizar essa rotação, parece que a  árvore se tornou mais ainda desbalanceada. Porém mais adiante veremos que a árvore ficará balanceada.
![[Pasted image 20241207170339.png]]
O segundo passo é fazer uma rotação esquerda em $A$. Repare que a altura final da sub-árvore é $n+2$, ou seja, a altura se manteve intacta. Isso funciona também se o novo nó tivesse sido inserido em $T_{2}$.
#### Como decidir qual rotação usar
Para decidir se usamos uma rotação simples ou dupla olhamos o sinal dos nós. Se o sinal do nó $A$ e do nó $B$ forem igual, então a rotação é simples. Entretanto, se o sinal do nó $A$ e do nó $B$ forem diferentes, então a rotação é dupla.

Considerando as rotações simples, para decidir se a rotação é direita ou esquerda usamos o fator de balanceamento. Se o fator de balanceamento do nó $A$ (nó mais jovem a se tornar desbalanceado) for positivo, então a rotação é direita. Porém, se o fator de balanceamento do nó $A$ (nós mais jovem a se tornar desbalanceado) for negativo, então a rotação é esquerda.

Agora, para as rotações duplas, para decidir se a rotação é dir/esq ou esq/dir, vamos olhar o fator de balanceamento. Se o fator de balanceamento do nó $A$ (nó mais jovem a se tornar desbalanceado) for positivo, então a rotação é esq/dir. Porém, se o fator de balanceamento do nó $A$ (nó mais jovem a se tornar desbalanceado) for negativo, então a rotação é dir/esq.
#### Inserção
Nós devemos utilizar as rotinas de rotação para definir um algoritmo de inserção em árvores AVL. A maioria das implementações guardam o fator de balanceamento, porém guardar a altura dos nós facilita.

A inserção é feita em dois passos:
- O primeiro é uma inserção em ABB como já vimos
- O segundo é o rebalanceamento, se necessário

Aprofundando mais, a primeira etapa é definir uma inserção em ABB e atualizar as alturas dos nós. Na volta da inserção o balanceamento é verificado, se a árvore estiver desbalanceada, aplicar as rotações necessárias. O desbalanceamento pode ser verificado de duas formas:
- Com base na altura das sub-árvores: cada nó armazena sua altura e daí calcula-se o FB (fator de balanceamento)
- Com base no fator de balanceamento: cada nó armazena seu FB

Assim, temos que (consideremos a notação acima em que $A$ é o nó mais jovem a se tornar desbalanceado e $B$ é seu filho):
- Se FB = -2, as rotações podem ser:
	- Esquerda
	- Direita/Esquerda
	- Se FB do filho direito ($B$) é negativo, rotação esquerda, caso contrário rotação direita/esquerda
- Se FB = 2, as rotações podem ser
	- Direita
	- Esquerda/Direita
	- Se FB do filho esquerdo ($B$), é positivo, rotação direita, caso contrário rotação esquerda/direita
#### Remoção
Nós devemos utilizar as rotinas de rotação para definir um algoritmo de remoção para as AVLs. A remoção pode ser feita em dois passos:
- O primeiro é uma remoção em ABB
	- Existem três casos possíveis: o nó removido possui grau 0, 1 ou 2
- O segundo é o rebalanceamento, se necessário

Percebe-se que a função de troca é semelhante à da ABB, tirando o fato que o item é removido nesta implementação.
#### Complexidade
A altura máxima de uma ABB AVL é $1,44 \log_{2}n$, dessa forma, uma pesquisa nunca exige mais do que $44\%$ mais comparações que uma ABB completa cheia. Na prática, para $n$ grande, os tempos de busca são por volta de $\log_{2}n+0,25$. Na média, é necessária uma rotação em $46,5\%$ das inserções.
#### Implementando a AVL
Primeiramente vamos olhar na criação de um macro. Macro é uma construção fornecida ao pré-processador que permite substituir um identificador por um pedaço de código antes do processo de compilação. Quando a macro é processada pelo pré-processador, antes da compilação, ela é substituída pelo seu trecho de código equivalente. Vale ressaltar que não há verificação de tipos em macros. Então com qualquer tipo que suporte a operação irá funcionar, mas isso pode levar a erros inesperados caso o tipo não suporte a operação.

Usaremos uma macro no código a seguir. Primeiro faremos a definição de tipos:
~~~C
// avl.h
#define max(a, b) ((a > b) ? a : b)
typedef struct avl AVL;

// avl.c
#include "avl.h"

typedef struct no NO;

struct no {
    ITEM *item;
    NO *fesq;
    NO *fdir;
    int FB;
    int altura; // Para caso utilize a altura na hora da inserção
};

struct avl {
    NO *raiz;
    int profundidade;
};

~~~
Vamos, agora, criar os métodos básicos:
~~~C
AVL *avl_criar(void) {
    AVL *arvore = (AVL *) malloc(sizeof(AVL));
    if (arvore != NULL) {
        arvore->raiz = NULL;
        arvore->profundidade = -1;
    }
    return arvore;
}

void avl_apagar_aux(NO *raiz) {
    if (raiz != NULL) {
        avl_apagar_aux(raiz->fesq);
        avl_apagar_aux(raiz->fdir);
        apagar_item(&raiz->item);
        free(raiz);
    }
}

void avl_apagar(AVL **arvore) {
    avl_apagar_aux((*arvore)->raiz);
    free(*arvore);
    *arvore = NULL;
}
~~~
Vejamos os métodos auxiliares:
~~~C
#define max(a, b) ((a > b) ? a : b)

int avl_altura_no(NO *raiz) {
    if (raiz == NULL) {
        return -1;
    } else {
        return raiz->altura;
    }
}

NO *avl_cria_no(ITEM *item) {
    NO *no = (NO *) malloc(sizeof(NO));
    if (no != NULL) {
        no->FB = 0;
        no->fdir = NULL;
        no->fesq = NULL;
        no->item = item;
    }
    return no;
}
~~~
Agora, a rotação direita:
~~~C
NO *rodar_direita(NO *a) {
    NO *b = a->fesq;
    a->fesq = b->fdir;
    b->fdir = a;
    a->FB = b->FB = 0;
    /*altura = max(avl_altura_no(a->fesq),
                   avl_altura_no(a->fdir)) + 1;
      b->altura = max(avl_altura_no(b->fesq),
                      a->altura) + 1;*/
    return b;
}
~~~
Agora, a rotação esquerda:
~~~C
NO *rodar_esquerda(NO *a) {
    NO *b = a->fdir;
    a->fdir = b->fesq;
    b->fesq = a;
    a->FB = b->FB = 0;
    /*a->altura = max(avl_altura_no(a->fesq),
                      avl_altura_no(a->fdir)) + 1;
      b->altura = max(avl_altura_no(b->fdir),
                      a->altura) + 1;*/
    return b;
}
~~~
Para a rotação esq/dir:
~~~C
NO *rodar_esquerda_direita(NO *a) {
    a->fesq = rodar_esquerda(a->fesq);
    return rodar_direita(a);
}
~~~
Para a rotação dir/esq:
~~~C
NO *rodar_direita_esquerda(NO *a) {
    a->fdir = rodar_direita(a->fdir);
    return rodar_esquerda(a);
}
~~~
Inserção:
~~~C
NO *avl_inserir_no(NO *raiz, ITEM *item) {
    if (raiz == NULL)
        raiz = avl_cria_no(item);
    else if (item_chave(item) < item_chave(raiz->item))
        raiz->fesq = avl_inserir_no(raiz->fesq, item);
    else if (item_chave(item) > item_chave(raiz->item))
        raiz->fdir = avl_inserir_no(raiz->fdir, item);

    raiz->FB = (avl_altura2(raiz->fesq)) - (avl_altura2(raiz->fdir));

    if (raiz->FB == -2) {
        if (raiz->fdir->FB <= 0)
            raiz = rodar_esquerda(raiz);
        else
            raiz = rodar_direita_esquerda(raiz);
    }

    if (raiz->FB == 2) {
        if (raiz->fesq->FB >= 0)
            raiz = rodar_direita(raiz);
        else
            raiz = rodar_esquerda_direita(raiz);
    }

    return raiz;
}

bool avl_inserir(AVL *arvore, ITEM *item) {
    return ((arvore->raiz = avl_inserir_no(arvore->raiz, item)) != NULL);
}
~~~
Remoção:
~~~C
bool avl_remover(AVL *T, int chave) {
    return (T->raiz = avl_remover_aux(&T->raiz, chave)) != NULL;
}

NO *avl_remover_aux(NO **raiz, int chave) {
    NO *p;

    if (*raiz == NULL)
        return (NULL);
    else if (chave == item_get_chave((*raiz)->item)) {
        if ((*raiz)->esq == NULL || (*raiz)->dir == NULL) {
            // Caso 1 se resume ao caso 2: há um filho ou nenhum
            p = *raiz;
            if ((*raiz)->esq == NULL)
                *raiz = (*raiz)->dir;
            else
                *raiz = (*raiz)->esq;

            item_apagar(&p->item);
            free(p);
            p = NULL;
        } else {
            // Caso 3: há ambos os filhos
            troca_max_esq(&(*raiz)->esq, (*raiz), (*raiz));
        }
    } else if (chave < item_get_chave((*raiz)->item))
        (*raiz)->esq = avl_remover_aux(&(*raiz)->esq, chave);
    else if (chave > item_get_chave((*raiz)->item))
        (*raiz)->dir = avl_remover_aux(&(*raiz)->dir, chave);

    if (*raiz != NULL) {
        (*raiz)->FB = avl_altura2((*raiz)->esq) - avl_altura2((*raiz)->dir);
        if ((*raiz)->FB == 2) {
            if ((*raiz)->esq->FB >= 0) // FB Filho esq positivo = rot simples
                *raiz = rodar_direita(*raiz);
            else
                *raiz = rodar_esquerda_direita(*raiz);
        }
        if ((*raiz)->FB == -2) {
            if ((*raiz)->dir->FB <= 0) // FB Filho dir negativo = rot simples
                *raiz = rodar_esquerda(*raiz);
            else
                *raiz = rodar_direita_esquerda(*raiz);
        }
    }
    return *raiz;
}

void troca_max_esq(NO *troca, NO *raiz, NO *ant) {
    if (troca->dir != NULL) {
        troca_max_esq(troca->dir, raiz, troca);
        return;
    }
    if (raiz == ant)
        ant->esq = troca->esq;
    else
        ant->dir = troca->esq;

    ITEM *it = rem->item;
    raiz->item = troca->item;
    item_apagar(&it);
    free(troca);
    troca = NULL;
}
~~~
### Árvore Rubro-Negra
A árvore rubro-negra é um outro tipo de árvore balanceada de busca. A versão que será apresentada aqui é a Left-Leaning Red-Black Tree. Essa árvore possui as arestas coloridas de vermelho ou preto. Além disso, há algumas regras:
- Aresta vermelha sempre vai para o filho esquerdo
- Todo nó possui, no máximo, uma aresta vermelha
- Balanceamento negro perfeito: todo filho nulo está à mesma distância negra da raiz (distância das arestas pretas)

Nesse tipo de árvore, no pior caso, a altura será $h \leq 2 \log(n)$.

A inserção nesse tipo de árvore é igual na ABB, porém todo nó inserido possui aresta incidente vermelha (a aresta que liga ele à raiz é vermelha).

O primeiro nó inserido é preto.
#### Inserção em nó (pai) sem incidência vermelha
Se vamos inserir um nó sem incidência vermelha (não há uma aresta vermelha no pai) temos dois casos, ou iremos inserir ele como filho esquerdo ou como filho direito.

Como filho esquerdo, ao inserí-lo, a aresta do nó será vermelha e como ele é filho esquerdo, nenhuma regra é quebrada. Porém se inserirmos o nó como filho direito, a primeira regra será quebrada e, assim, será necessária uma rotação para que a aresta vá para o filho esquerdo (essa rotação é a mesma que já vimos anteriormente). Veja a seguir uma inserção com filho esquerdo
![[Pasted image 20241207182438.png]]
Veja agora a inserção como filho direito.
![[Pasted image 20241207182503.png]]
![[Pasted image 20241207182510.png]]
#### Inserção em nó (pai) com incidência vermelha
Para a inserção em nó com incidência vermelha, temos três possíveis casos, mas em todos quebraremos a segunda regra. Então, é preciso que após a inserção e remoção, façamos a manutenção das três regras. As operações locais que podem ser feitas para arrumar são: rotação à esquerda, rotação à direita e inversão de cores.

As rotações à esquerda e à direita são parecidas com AVL. Veja abaixo.
![[Pasted image 20241207220018.png]]
A inversão de cores é quando invertemos a cor de todas as arestas das quais o pai faz parte. Veja abaixo.
![[Pasted image 20241207220111.png]]
Importante ressaltar que nenhum das três operações infringe a regra 3. 

Vamos, agora que já vimos as três operações, ver como podemos fazer a manutenção da árvore em cada um dos três casos.
##### Primeiro caso
Inserir como filho direito de $b$ e com a aresta esquerda vermelha.
![[Pasted image 20241207221042.png]]
Após a inserção é preciso:
1. Inverter as cores de B
##### Segundo caso
Duas arestas esquerdas vermelhas consecutivas.
![[Pasted image 20241207221116.png]]
Após a inserção é preciso:
1. Rotacionar à direita o C
2. Inverter as cores do B
##### Terceiro caso
Duas arestas vermelhas consecutivas, mas a primeira é esquerda e a segunda é direita.
![[Pasted image 20241207221219.png]]
Após a inserção é preciso:
1. Rotacionar à esquerda o A
2. Rotacionar à direita o C
3. Inverter as cores do B

Fazendo um resumo da inserção, temos que:
- Ela segue o algoritmo da ABB
- Sempre insere aresta vermelha
- Pode quebrar regras 1 e 2 (mas depois é preciso arrumar)
- Operações locais (inverter e rotacionar) corrigem os problemas localmente
- Operação inverte
	- Propaga aresta vermelha para cima
	- Pode ser tratada recursivamente como inserção
	- Até alcançar um nó
		- Sem incidência vermelha; ou
		- Raiz da árvore
#### Remoção
A remoção sempre de um nó folha com aresta vermelha:
- Aplicar conceitos de remoção de ABB no caso do nó não ser folha
	- Substituição de chave não altera formato/propriedades da árvore
- Propagar aresta vermelha da raiz até a folha se necessário:
	- Se busca pela esquerda moveRedLeft
	- Se busca pela direita: moveRedRight
- Na volta da recursão: operações inverte, rotação direita e esquerda para corrigir violações

Para a remoção, podemos dividir em duas: moveRedLeft e moveRedRight. Ambos os passos a seguir são feitos antes da remoção. Então, é removido o item e depois, se for necessário, faz-se a manutenção da árvore.
##### moveRedLeft
Para esse tipo, temos dois casos:
- `h->esq` é black e `h->esq->esq` é black
- `h->dir->esq` é red
![[Pasted image 20241207224409.png]]
##### moveRedRight
Para esse tipo, temos dois casos:
- `h->dir` é preta e `h->dir->esq` é black
- `h->esq->esq` é red
![[Pasted image 20241207230318.png]]
#### Implementação
Primeiro vamos analisar a estrutura do nó:
~~~C
typedef struct no no_t;

struct no {
	no_t *esq, *dir;
	int cor; // Preto = 0 e Vermelho = 1
	int info;
};
~~~
Agora veja a operação de inverter:
~~~C
void inverte(no_t *r){
	r->cor = !r->cor;
	if(r->esq)
		r->esq->cor = !r->esq->cor;
	if(r->dir)
		r->dir->cor = !r->dir->cor;
}
~~~
Vejamos agora a operação de inverter à direita:
~~~C
no_t *rotacaoDireita(no_t *c){
	no_t *b = c->esq;
	c->esq = b->dir;
	b->dir = c;
	b->cor = c->cor;
	c->cor = 1;
	return b;
}
~~~
De modo semelhante, a rotação esquerda pode ser vista abaixo:
~~~C
no_t *rotacaoEsquerda(no_t *a){
	no_t *b = a->dir;
	a->dir = b->esq;
	b->esq = a;
	b->cor = a->cor;
	a->cor = 1;
	return b;
}
~~~
Agora que já vimos as operações locais, vamos ver a inserção:
~~~C
int Vermelho(no_t* h){
	if(h == NULL){
		return 0;
	}
	return (h->cor == 1);
}

no_t* insere_llrb(no_t* h, int data){
	if(h == NULL){
		return criarNo(data);
	}
	if(data < h->info){
		h->esq = insere_llrb(h->esq, data);
	} else if (data > h->info){
		h->dir = insere_llrb(h->dir, data);
	}

	if(Vermelho(h->dir) && !Vermelho(h->esq)){
		h = rotacaEsquerda(h);
	}
	if(Vermelho(h->esq) && Vermelho(h->esq->esq)){
		h = rotacaoDireita(h);
	}
	if(Vermelho(h->esq) && Vermelho(h->dir)){
		inverte(h);
	}

	return h;
}
~~~
### Heap
Uma heap é uma árvore binária que satisfaz as propriedades a seguir:
- Ordem: para cada nó $v$, exceto o nó raiz, tem-se que
	- chave($v$) $\leq$ chave(pai($v$)) - heap máxima
	- chave($v$) $\geq$ chave(pai($v$)) - heap mínima
- Completude: dado que $h$ é a altura, a árvore é completa se:
	- Todo nó folha está no nível $h$ ou $h-1$
	- O nível $h-1$ está totalmente preenchido
	- As folhas do nível $h$ estão todas mais a esquerda

Uma convenção para trabalharmos com heaps é que o último nó é o nó interno mais à direita de profundidade $h$, ou seja, esse nó está no último nível.

A heap é usada como estrutura de apoio para algoritmos clássicos:
- Ordenação
	- Heapsort
	- Mergesort
- Algoritmos em grafos
	- Algoritmo de Dijkstra: busca de menor caminho em grafo ponderado
	- Algoritmo de Prim: geração de MST (Minimal Spaning Tree - Árvore Geradora Mínima)
#### Altura de uma heap
Uma heap armazenando $n$ nós possui altura $h$ de ordem $O(\log n)$. A prova do teorema anterior, é: "Dado que existem $2^{i}$ chaves na profundidade $i = 0, ..., h-1$ e ao menos 1 chave na profundidade $h$ tem-se que: $n \geq 1 + 2 + 4 + ...+ 2^{h-1} + 1$. Isso é uma progressão geométrica (PG) com razão $q = 2$. Dado que a soma de uma PG pode ser calculada por $$ S_{k} = \frac{a^{k} \times q-a_{1}}{q - 1},$$ temos que $(2^{h-1} \times 2 - 1)+ 1 = 2^{h}$. Logo, $n\geq 2$, então, $h \leq \log_{2}n \longrightarrow h$ é $O(\log n)$." 
#### Fila de prioridade com arranjo
Os vetores podem ser empregados para representar árvores binárias. Nessa implementação, caminhamos pela árvore nível por nível, da esquerda para direita, armazenando os nós no vetor. O primeiro nó fica na posição $0$ do vetor, seu filho a esquerda fica na posição $1$, e assim por diante.

Usando essa definição, quando tivermos o índice de um item, podemos encontrar:
- Filho esquerdo: $2\times índice + 1$
- Filho direito: $2 \times índice + 2$
- Pai: $\displaystyle \frac{índice - 1}{2}$

Como a heap é uma árvore completa, o vetor não vai ter "buracos" faltando itens. Os itens que faltam sempre ficam no fim do vetor. Se a árvore não fosse completa, teríamos "buracos" no vetor.
##### Implementação
Veja abaixo a estrutura:
~~~C
// .h
typedef struct heap_sequencial HEAP_SEQUENCIAL;

#define TAM 100

// .c
struct heap_sequencial {
	ITEM* vetor[TAM];
	int fim;
}

// main.c
HEAP_SEQUENCIL* Heap;
~~~
Agora, veja os métodos básicos:
~~~C
HEAP_SEQUENCIAL *hep_criar() {
    HEAP_SEQUENCIAL *heap = (HEAP_SEQUENCIAL*) malloc(sizeof(HEAP_SEQUENCIAL));
    if (heap != NULL) {
        heap->fim = -1;
    }
    return heap;
}

int heap_cheia(HEAP_SEQUENCIAL *heap) {
    return (heap->fim == TAM - 1);
}

int heap_vazia(HEAP_SEQUENCIAL *heap) {
    return (heap->fim == -1);
}

~~~
Segue o código da inserção:
~~~C
int heap_enfileirar(HEAP_SEQUENCIAL *heap, ITEM *item) {
    if (!heap_cheia(heap)) {
        heap->fim++;
        heap->vetor[heap->fim] = item;
        heap_fix_up(heap);
        return 1;
    }

    return 0;
}

void heap_swap(HEAP_SEQUENCIAL *heap, int i, int j) {
    ITEM *tmp = heap->vetor[i];
    heap->vetor[i] = heap->vetor[j];
    heap->vetor[j] = tmp;
}

void heap_fix_up(HEAP_SEQUENCIAL *heap) {
    int w = heap->fim;
    int pai = (w - 1) / 2;

    while (w > 0 && item_get_chave(heap->vetor[w]) > item_get_chave(heap->vetor[pai])) {
        heap_swap(heap, w, pai);
        w = pai;
        pai = (pai - 1) / 2;
    }
}
~~~
# Fila de Prioridade
Nessa estrutura de dados os elementos são processados de acordo com sua importância, independentemente do momento que entraram na fila. Alguns exemplos são:
- Atendimento preferencial em geral
- Importância de processos em sistemas operacionais
- Substituições de páginas menos utilizadas na memória
- Filas de atendimento para análise de sinais em sistemas de controle (sensores prioritários)

Esse TAD, da forma que iremos implementar, irá armazenar item. Os itens são compostos de um par(chave, informação).

As operações principais são:
- desenfileirar(F): remove e retorna o item com maior (menor) prioridade da fila F
- enfileirar(F, x): insere um item $x = (k, i)$ com chave $k$

As operações auxiliares são:
- proximo(F): retorna o item com maior (menor) chave da fila F, sem removê-lo
- vazia(F)
- cheia(F)

Ele possui diferentes implementações:
- Estática
	- Lista sequencial (arranjo) ordenada
	- Lista sequencial (arranjo) não ordenada
	- Heap em arranjo
- Dinâmica
	- Lista encadeada ordenada
	- Lista encadeada não ordenada
	- Heap encadeada

Cada realização possui vantagens e desvantagens. Uma das escolhas diretas seria usar uma lista ordenada:
- Inserção é $O(n)$
- Remoção é $O(1)$
- Próximo é $O(1)$

Outra seria usar uma fila ou lista não-ordenada
- Inserção é $O(1)$
- Remoção é $O(n)$
- Próximo é $O(n)$

Portanto uma abordagem mais rápida precisa ser pensada quando grandes conjuntos de dados são considerados.
## Filas de prioridade com heap
Nesse tipo de implementação, iremos armazenar um item em cada nó. Mantém-se o controle sobre a localização do último nó ($w$). Remove-se sempre o item armazenado na raiz, devido a propriedade de ordem da heap:
- Heap mínima: menor chave na raiz da heap
- Heap máxima: maior chave na raiz da heap
### Inserção
O método insere do TAD fila de prioridade corresponde à uma inserção de um item na heap. O algoritmo tem três passos:
1. Encontrar e criar nó de inserção $z$ (novo último nó depois de $w$)
2. Armazenar o item com chave $k$ em $z$
3. Restaurar ordem da heap
### Restauração da Ordem (fix-up)
Após a inserção de um novo item, a propriedade de ordem da heap pode ser violada. Por isso temos que restaurar a ordem da heap trocando os itens caminho acima a partir do nós de inserção (em outras palavras, a manutenção é feita na volta da recursão). A restauração termina quando o item inserido alcança a raiz ou um nó cujo pai possui uma chave maior (ou menor).
### Remoção
O método da remoção do TAD fila de prioridade corresponde a remoção do item da raiz. O algoritmo consiste em três passos:
- Armazenar o conteúdo do nó raiz da heap (para retorno)
- Copiar o conteúdo de $w$ (último nó) no nó raiz e remover o nó $w$
- Restaurar ordem da heap

O uso do último nó para substituir a raiz tem algumas vantagens, entre elas temos:
completude garantida (passo 2) e implementação em tempo constante através de arranjo.
### Restauração da Ordem (fix-down)
Após a remoção, a propriedade de ordem da heap pode ser violada. Por isso, é preciso restaurar a ordem trocando os item caminho abaixo a partir da raiz. O algoritmo de fix-down termina quando o item movido para a raiz alcança um nó que não possui filho com chave maior que a sua.
## Implementação
A inserção é:
~~~C
inserirNoFim(F)
fix_up(F)
~~~
Para uma heap máxima temos a seguinte implementação de restauração de ordem:
~~~C
//fix_up:
w = F.ultimo;
while((!isRoot(F,w)) && (key(F,w) > key(F, parent(F,W)))){
	swap(F,w,parent(F,w));
	w = parent(F,w)
} 

~~~
A remoção é:
~~~C
x = inicio(F)
inicio(F) = fim(F)
fix_down(F)
~~~
Para uma heap máximo, temos a seguinte implementação da restauração de ordem:
~~~C
w = inicio(F);
while(tem_filho(w)){
	m = maior_filho(w);
	if(chave(w) >= chave(m)){
		break;
	}
	swap(F, w, m);
	w = m;
}
~~~
## Comparação
Via fila ordenada:
- Inserção é $O(n)$
- Remoção é $O(1)$
- Próximo é $O(1)$

Via fila não-ordenada:
- Inserção é $O(1)$
- Remoção é $O(n)$
- Próximo é $O(n)$

Via heap:
- Inserção é $O(\log n)$
- Remoção é $O(\log n)$
- Próximo é $O(1)$
