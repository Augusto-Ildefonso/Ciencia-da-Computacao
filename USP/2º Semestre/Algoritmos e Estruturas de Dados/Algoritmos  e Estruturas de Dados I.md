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

Podemos utilizar os percursos para interpretar operações aritméticas. O percurso em-ordem representa: $a+(b \times c)$. O percurso pré-ordem representa: $+a \times bc$. Por fim o pós-ordem representa $abc\times+$. Daí, os algoritmos para cálculo podem usar pilhar

### Árvore Estritamente Binária
Uma Árvore Estritamente Binária (ou Árvore Própria) tem nós com 0 (nenhum) ou 2 filhos. Nesse tipo de árvore os nós interiores (não folhas) sempre tem 2 filhos.
![[Pasted image 20241130183657.png]]
### Árvore Binária Completa Cheia
A árvore binária completa cheia é uma árvore estritamente binária que tem como característica todos os seus nós folha estarem no mesmo nível.
![[Pasted image 20241201151826.png]]
Dada uma árvore binária completa cheia ABCC e sua profundidade $d$, pode-se calcular o número total de nós na árvore por:
- Nós do último nível: $2^{d}$
- Total de nós: $2^{d+1} - 1$

Portanto, se o número de nós, $n$, para uma árvore binária completa cheia de profundidade $d$ é $n = 2^{d+1}-1$, então, $n$ nós podem ser distribuídos em uma árvore binária completa cheia de profundidade:
1. $n = 2^{d+1}-1$
2. $\log_{2}{(n+1)} = \log_{2}{(2^{d+1})}$
3. $d = \log_{2}{(n+1)}-1$

O problema com esse tipo de árvore é a necessidade de manter os níveis cheios/completos.

Para implementar esse tipo de árvore podemos adotar uma organização sequencial, de modo que vamos armazenar os nós, por nível, em um array.
### Árvore Binária Completa
A árvore binária completa (ABC) tem que se a profundidade da árvore é $d$, então cada nó folha está no nível $d-1$ ou no nível $d$. O nível $d-1$ pode estar totalmente preenchido, mas não é uma regra. Além disso, os nós folhas no nível d estão todos mais à esquerda possível.

Para implementar esse tipo de árvore podemos adotar uma organização sequencial, de modo que para um vetor indexado a partir da posição 0, se um nó está na posição $i$, seus filhos diretos estão nas posições $2_{i}+1$, filho da esquerda, e $2_{i}+2$, filho da direita.

A vantagem é que vamos ocupar o espaço necessário só para armazenar o conteúdo e temos ligações implícitas. Já a desvantagem é que teremos espaços vagos se a árvore não é completa por níveis ou, então, se sofrer eliminação.
### Árvore Binária Perfeitamente Balanceada
A árvore binária perfeitamente balanceada tem que para cada nó, o número de nós de suas sub-árvores esquerda e direita difere em, no máximo, 1.
![[Pasted image 20241201153452.png]]
### Árvore Binária Balanceada
A árvore binária balanceada é caracterizada de modo que para cada nó, as alturas de suas duas sub-árvores diferem de, no máximo, 1. 

Toda árvore perfeitamente balanceada é balanceada, mas o inverso não é necessariamente verdade.