# Revisão de C
## Algoritmo
Procedimento computacional bem definido que recebe valores de entrada e produz valores de saída. Ele é uma sequência de passos computacionais que transformam em uma entrada e uma saída.
Exemplo de programa em C:
```
#include <stdio.h>
#include <stdlib.h>

float potencia(float base, int exp);

float potencia(float base, int exp){
	float res = 1;
	int i;

	for(i = 0; i < exp; i++){
		res *= base;
	}

	return res;
}

int main(void){
	float x;
	int exp;

	scanf("%f %d", &x, &exp);

	printf("%f\n", potencia(x, exp));

	return EXIT_SUCCESS;
}
```
## Ponteiros
Padrões de armazenamento de inteiros:
- Little Endian: 4º 3º 2º 1º (bytes menos significativos primeiros)
- Big Endian: 1º 2º 3º 4º (bytes mais significativos primeiro)
Intel é little endian e Sun Microsystens é big endian.
Diferentes arquiteturas:
- 32 bits -> o ponteiro vai ter 4 bytes
- 64 bits -> o ponteiro vai ter 8 bytes
## Funções Novas
- memcpy - copia os valores do número de bytes da origem para o destino
# Recursão
Recursividade consiste na ideia de dividir o problema consecutivamente em pedaços menores até se tornar algo trivial.
Para ter um algoritmo recursivo, ele deve cumprir três regras:
- Deve ter um caso básico
- Deve se aproximar do caso básico a cada estado
- Deve chamar a si mesmo recursivamente
Uma função é recursiva quando é definida em seus próprios termos, direta ou indiretamente.
A função recursiva ocupará mais espaço na memória (stack) do que a iterativa. Caso dê para criar uma iterativa é melhor. Mas tem certos problemas que a função iterativa dará muito mais trabalho do que a recursiva e por isso vale a pena usar ela.
Exemplo de código recursivo:
```
#include <stdio.h>

int fat(int x){
	if(x == 1){
		return(1);
	} else{
		return(x * fat(x-1));
	}
}

int main(void){
	int x;

	scanf("%d", &x);

	printf("%d! = %d\n", x, fat(x));

	return(0);
}
```
## Efeitos da recursão
### A cada chamada
- Empilham-se na memória os dados locais (variáveis e parâmetros) e o endereço de retorno. A função corrente só termina quando a função chamada terminar
- Executa-se a nova chamada (que também pode ser recursiva)
- Ao retornar,  desempilham-se os dados da memória, restaurando o estado antes da chamada recursiva
### Mesmo resultado com diferença de haver duplicação de código
Para usar recursão depende do problema, pois nem sempre a recursão será a melhor forma de resolver o problema, já que pode haver uma versão simples e não recursiva da função (que não duplica o código e não consome mais memória).
## Quando usar
Quando o problema pode ser definido recursivamente de forma natural.
### Como usar
1. Definir o problema de forma recursiva, ou seja, em termos dele mesmo
2. Definir a condição de término (ou condição básica)
3. A cada chamada recursiva, deve-se tentar garantir que se está mais próximo de satisfazer a condição de término
## Extra
### time.h
Essa biblioteca possui funções que permitem calcular o tempo de execução.
```
clock_t inicio, fim;

inicio = clock();

fim = clock();

printf("%f", (double) ((fim - inicio) / CLOCKS_PER_SEC));
```
## Recursão de Cauda
É quando tem uma chamada recursiva no final do código. Eles são mais facilmente transformáveis em programas iterativos. A recursão pode virar uma condição
Uma rotina apresenta recursão de cauda se a chamada recursiva está no final do seu código, tendo como única função criar um "looping" que será repetido até que a condição de parada seja satisfeita.
Pode ser eliminada facilmente se empregarmos, em seu lugar, uma estrutura de repetição que esteja condicionada à expressão de teste usada na versão recursiva.
# Análise de Algoritmos
## Algoritmo
É um conjunto de instruções que devem ser seguidas para solucionar um determinado problema.
Qualquer procedimento computacional bem definido que toma algum valor ou conjunto de valores de entrada e produz algum valor ou conjunto de valores de saída.
Ferramenta para desenvolver um problema computacional bem especificado.
Assim como o hardware de um computador, constitui uma tecnologia, pois o desempenho total do sistema depende da escolha de um algoritmo eficiente tanto quanto da escolha de um hardware rápido.
Deseja-se que um algoritmo termine e seja correto.
## Recursos de um algoritmo
Uma vez que um algoritmo está pronto/disponível, é importante determinar os recursos necessários para sua execução:
- Tempo
- Memória
## Análise de algoritmos
Um algoritmo que soluciona um determinado problema, mas requer o processamento de um ano, não deve ser usado. Antes de escolher trocar um algoritmo por outro, só porque ele roda mais rápido em determinada máquina, temos que considerar alguns fatores:
- Características da máquina em que o algoritmo foi testado (quantidade de memória)
- Linguagem de programação
	- Compilada x Interpretada
 	- Alto x Baixo Nível
- Implementação pouco cuidadosa do algoritmo x contra a "super" implementação do algoritmo y.
- Quantidade de dados processados
A comunidade de computação começou a pesquisar formas de comparar algoritmos de forma independente de:
- Hardware
- Linguagem de programação
- Habilidade do programador
Portanto, deseja-se comparar algoritmos e não programas (essa área é conhecida como "análise/complexidade de algoritmos").
## Eficiência de algoritmos
Estimamos a eficiência de um algoritmo em função do tamanho do problema. Em geral, assume-se que "n" é o tamanho do problema, ou número de elementos que serão processados. E calcula-se o número de operações que serão realizadas sobre os n elementos.
O melhor algoritmo é aquele que requer menos operações sobre a entrada, pois é o mais rápido e, diferente do tempo de execução que varia de máquina para máquina, o número de operações não, então é uma boa medida de desempenho de um algoritmo. As operações que falamos são as usadas para resolver o problema. O tempo de cada operação é constante, o que muda é a quantidade de vezes.
## Análise assintótica
Deve-se preocupar com a eficiência de algoritmos quando o tamanho de n for grande. A eficiência assintótica de um algoritmo descreve a eficiência relativa dele quando n torna-se grande. 
Portanto, para comparar 2 algoritmos, determinam-se as taxas de crescimento de cada um: o algoritmo com menor taxa de crescimento rodará mais rápido quando o tamanho do problema for grande.
Vale ressaltar que algumas funções podem não crescer com o valor de n.
Também pode-se aplicar os conceitos de análise assintótica para a quantidade de memória usada por um algoritmo. Mas não é tão útil, pois é difícil estimar os detalhes exatos do uso de memória e o impacto disso.
Usaremos potências e logaritmos nas análises. Para os logaritmos usaremos a base 2, a menos que seja dito o contrário. Também usaremos algumas séries:
$$\sum_{i=0}^{n} 2^i = 2^{n+1} - 1$$
$$\sum_{i=0}^{n} a^i = \frac{a^{n+1} - 1}{a-1}$$
$$\sum_{i = 1}^{n} i = \frac{n(n+1)}{2} \approx \frac{n^2}{2}$$
## Notações
Nessas notações T(n) é a taxa do nosso próprio algoritmo. Quando eu falo que meu algoritmo (T(n)) é uma das notações abaixo eu estou falando que eles seguem a regra de cada algoritmo. Para verificar se a notação está correta, eu substituo as fórmulas e acho a constante c, se existir é verdade, se não, não é verdade.
### Big-Oh
Também chamado de Oh ou "da ordem de", ele é usado quando a taxa de crescimento de T(n) é menor ou igual à taxa de f(n). Se existirem constantes c e $n_0$ tal que T(n) $\leq$ c * f(n) quando n $\geq$ $n_0$, temos:
$$T(n) = O(f(n))$$
Ao dizer que T(n) = O(f(n)), garante-se que T(n) cresce em uma taxa não maior do que f(n), ou seja, f(n) é seu limite superior.
### Ômega
Ele é usado quando a taxa de crescimento de T(n) é maior ou igual à taxa de f(n). Se existirem constantes c e $n_0$ tal que T(n) $\geq$ c * f(n) quando n $\geq$ $n_0$, temos:
$$T(n) = \Omega(f(n))$$
Ao fizer que f(n) = $\Omega (T(n))$ tem-se que T(n) é o limite inferior de f(n).
### Theta
Ele é usado quando a taxa de crescimento de T(n) é igual à taxa de f(n). Ou seja, se e somente se T(n) = O(f(n)) e T(n) = $\Omega(f(n))$. Temos:
$$T(n) = \Theta(f(n))$$
ou
$$c_1 \times f(n) \leq T(n) \leq c_2 \times f(n)$$
Quando $T(n) = \Theta(f(n))$, então existem constantes positivas $c_1$ e $c_2$ tais que T(n) pode ser "imprensada" entre $c1 \times f(n)$ e $c_2 \times f(n)$.
### Little-Oh
Também chamado de o minúsculo, ele é usado quando a taxa de crescimento de T(n) é menor do que à taxa de f(n). Se existirem quaisquer constantes c e $n_0$ tal que T(n) < c * f(n) quando n $\geq$ $n_0$, temos:
$$T(n) = o(f(n))$$
O uso das notações permite comparar a taxa de crescimento das funções correspondentes aos algoritmos. Não faz sentido comparar pontos isolados das funções, já que podem não corresponder ao comportamento assintótico.
## Taxas de crescimento
### Regras
Se $T_1 (n) = O(f(n))$ e $T_2 (n) = O(g(n))$:
- $T_1 (n) + T_2 (n) = max(O(f(n)), O(g(n)))$, ou seja, pegamos para o valor de O(n) a função cuja a taxa de crescimento é maior
- $T_1 \times T_2 = O(f(n) \times g(n))$ 
Se T(x) é um polinômio de grau n, então $T(x) = \Theta(x^n)$ 
Se $log_{k}n = O(n)$ para qualquer constante k, pois logaritmos crescem muito vagarosamente. 
### Funções e taxas de crescimento
A tabela está em ordem de eficiência, no topo o mais eficiente (menor crescimento) para o menos eficiente.
![Tabela](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-22%2008-59-03.png)
![Gráfico](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-22%2009-01-08.png)
Apesar de ser importante, não se costuma incluir constantes ou termos de menor ordem em taxas de crescimento. Queremos medir a taxa de crescimento da função, o que torna os "termos menores" irrelevantes. As constantes também dependem do tempo exato de cada operação, como ignoramos os custos reais das operações, ignoramos também as constantes. Não se diz que $T(n) = O(2n^2)$ ou que $T(n) = O(n^2+2)$, diz-se apenas $T(n) = O(n^2)$.
### Exercício
Dados $f(n) = n^{1,5}$ e $g(x) = n \log n$, qual é o melhor algoritmo?
$$f(n) = n^{1,5} = \frac{n^{1,5}}{n} = n^{0,5} = (n^{0,5})^2 = n$$
$$g(x) = n \log n = \frac{n \log n}{n} = \log n = (\log n)^2 = \log^2n$$
Como o crescimento de $\log^2n$ é maior do que o crescimento de $n$, temos que o algoritmo g(x) é mais eficiente.
## Análise de algoritmos
Para proceder a análise de algoritmos e determinar as taxas de crescimento, necessitamos de um modelo de computador e das operações que executa. Assume-se o uso do computador tradicional, em que as instruções de um programa são executadas sequencialmente e com memória infinita, por simplicidade.
Temos que ter um repertório de funções simples, como soma, multiplicação, comparação, atribuição, etc. Por simplicidade e viabilidade da análise, assume-se que cada instrução demora exatamente uma unidade de tempo para ser executada (obviamente em situações reais, isso pode não ser verdade: a leitura de um dado do disco pode demorar mais do que uma soma).
Operações complexas como inversão de matrizes e ordenação de vetores, não são realizadas em uma única unidade de tempo, obviamente: devem ser analisadas em partes.
Considera-se somente o algoritmo e suas entradas (de tamanho n). Para uma entrada de tamanho n, pode-se calcular $T_{melhor} (n)$, $T_{média}$, $T_{pior}(n)$, ou seja, o melhor tempo de execução, o tempo médio e o pior, respectivamente:
$$T_{melhor}(x) \leq T_{média}(x) \leq T_{pior}(x)$$
Atenção, para mais de uma entrada, essas funções teriam mais de um argumento.
Geralmente, utiliza-se somente a análise do pior caso $T_{pior}(x)$, pois ela fornece os limites para todas as entradas, incluindo particularmente as entradas ruins.
Logicamente, muitas vezes, o tempo médio pode ser útil, principalmente em sistemas executados rotineiramente. Porém dá mais trabalho calcular o tempo médio. E o melhor tempo não tem muita utilidade.
Existem basicamente duas formas de estimar o tempo de execução de programas e decidir quais são os melhores:
- Método Empírico
	- Executando e anotando o tempo de processamento e a quantidade de memória gasta
	- Diferentes complexidades -> tempos diferentes
- Método Analítico ou Teórico
	- Determinar uma expressão matemática que descreva o comportamento do algoritmo em relação ao tempo e à memória
	- Número de operações realizadas -> independe do computador, sistema operacional ou linguagem de programação
É desejável e possível estimar qual o melhor algoritmo sem ter que executá-los. O objetivo é obter uma expressão matemática que avalie complexidades. O modelo possui as seguintes características:
- Somente o comportamento assintótico será avaliado
	- A expressão fornecerá valores válidos somente quando a quantidade de dados correspondentes crescer o suficiente
- Não serão consideradas constantes aditivas ou multiplicativas na expressão obtida
- Fornece número de passos executados pelo algoritmo em função de uma certa entrada
	- Somente a operação dominante é considerada
## Regras para o cálculo
### Repetições
O tempo de execução de uma repetição é pelo menos o tempo dos comandos dentro da repetição (incluindo testes) vezes o número de vezes que é executada.
### Repetições aninhadas
A análise é feito de dentro para fora. O tempo total de comandos dentro de um grupo de repetições aninhadas é o tempo de execução dos comandos multiplicado pelo produto do tamanho de todas as repetições.
### Comandos consecutivos
É a soma dos tempos de cada um, o que pode significar o máximo entre eles.
### Se, senão, então
Para a cláusula condicional, o tempo de execução nunca é maior do que o tempo do teste mais o tempo do maior entre os comandos relativos ao então e os comandos relativos ao senão.
### Chamadas à sub-rotinas
Uma sub-rotina deve ser analisada primeiro e depois ter suas unidades de tempo incorporadas ao programa/sub-rotina que a chamou.
### Sub-rotinas recursivas
Se a recursão é um disfarce da repetição (e, portanto, a recursão está mal empregada, em geral), basta analisá-la como tal.
Em muitos casos (incluindo casos em que a recursividade é bem empregada), é difícil transformá-la em repetição. Nesses casos, para fazer a análise do algoritmo, pode ser necessário recorrer a análise de recorrência. Recorrência é a equação ou desigualdade que descreve uma função em termos do seu valor em entradas menores (caso típico: algoritmo de dividir-e-conquistar, algoritmos que desmembram o problema em vários subproblemas que são semelhantes ao problema original, mas menores em tamanho, resolvem os subproblemas recursivamente e depois combinam essas soluções com o objetivo de criar uma solução para o problema original).
### Resolução de recorrências
Muitas vezes, a recorrência pode ser resolvida com base na prática e experiência do analista. Alguns métodos para resolver recorrências:
- Método da substituição
- Método da árvore de recursão
- Método mestre
#### Método da substituição
Supõe-se (aleatoriamente ou com base na experiência) um limite superior para a função e verifica-se se ela não extrapola este limite. Faz o uso da indução matemática. O nome do método vem da substituição da resposta pelo palpite. Pode-se apertar o palpite para achar funções mais exatas.
O passo a passo é
1. Faço uma hipótese
2. Verifico ela para o caso base (Base da indução)
3. Assumimos que a hipótese é verdadeira para n
4. Mostramos que T(n) = expressão da hipótese
##### Exemplo
1. Hipótese
$$T(n) = O(n^2) <=> T(n) \leq c \times n^2$$
2. Base da indução
$$T(0) = 2 <=> T(0) = 2 \leq c \times 0^2 <=> 2 \leq 0$$
Para o caso base já falha, logo não funciona para n = 0.
$$T(1) = 2 <=> T(1) = 2 \leq c \times 1^2 <=>2 \leq c$$
Logo para n = 1 funciona
3. Assumindo que é verdadeira para n
$$T(n) = T(n-1) + T(n-2) + 6$$
$$T(k) = c \times(k-1)^2 + c \times (k-2)^2 + 6$$
$$T(k) = c \times (k^2 - 2k + 1) + c \times (k^2 - 4k +4) + 6$$ $$T(k) = 2ck^2 - 6ck +5c + 6$$
Usando a hipótese:
$$T(k) \leq O(k^2)$$
$$2ck^2 - 6ck +5c + 6 \leq c k^2$$
$$ck^2 -6ck + 5c + 6 \leq 0$$
O que não é verdadeiro sempre.
##### Busca binária
Ele é um algoritmo de dividir-e-conquistar. Tem que ter um vetor, não pode usar uma lista encadeada. O vetor tem que estar ordenado.
Funcionamento: vamos dividir ele no meio. Comparamos esse elemento com a chave. Se for igual, já sai, se for menor fazemos mais uma chamada da função para o lado esquerdo, se for maior fazemos o mesmo para o lado direito. E ai repetimos esse processo para cada sub vetor que obtemos até achar o elemento igual a chave.
![imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-26%2011-23-04.png)
~~~C
int busca_binaria(int v[], int inf, int sup, int x) {
	int meio;
	if (inf<=sup) {
		meio=(inf+sup)/2;
		if (x==v[meio]){
			return(meio);
		} else if (x<v[meio]){
			return(busca_binaria(v,inf,meio-1,x));
		} else{
			return(busca_binaria(v,meio+1,sup,x));
		}
	} else{
		return(-1);
	}
}
~~~
Custo:
$T(n) = O(c)$, se n = 0
$$T(n) = T(\frac{n}{2}) + O(c)$$Se n > 1.
Nesse caso, temos um tempo constante O(c) para as operações da função (comparações e divisão/diminuição do problema) e o tempo $T(\frac{n}{2})$ para os subprocessos recursivos. Fazendo pela substituição, podemos escolher $T(n) = O(\log{n})$, e resolvendo vemos que é verdade. Então $T(n) = O(\log{n})$.
#### Método da árvore de recursão
Esboça-se uma árvore que, nível a nível, representa as recursões sendo chamadas. Em seguida, em cada nível/nó da árvore, são acumulados os tempos necessários para o processamento. No final, tem-se a estimativa de tempo do problema. Este método pode ser utilizado para fazer uma suposição mais informada no método da substituição.
![[Imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-29%2008-52-12.png)
Percebe-se que a cada nível divide-se por 2, então como no último nível é 1, temos que $\frac{n}{2^i} = 1$, assim, $n = 2^i$ -> $log_{2}{n} = i$.
##### Mergesort
É um algoritmo de ordenação de arranjos por intercalação. Ele é do tipo dividir-e-conquistar. Ele usa uma ordenação por intercalação.
Exemplo de árvore
![imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-29%2009-09-24.png)
E assim por diante. O custo de cada nível é $n$. O total de largura da árvore vai ser $\log{n}$. Por isso:
$$T(n) = n \times (\log{n}+1) = n\times \log{n}+n = O(n\log{n})$$
O mais 1 é porque ele começa no 0.
Abaixo tem a lógica do mergesort:
![imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-29%2009-14-59.png)
Se for um número ímpar é só colocar o meio para um dos lados.
#### Método Mestre
Fornece limites para recorrência da forma: $T(n) = aT(\frac{n}{b})+f(n)$, em que $a \geq 1$, $b > 1$ e f(n) é uma função dada. Envolve a memorização de três casos básicos que podem ser aplicados para muitas recorrências simples.
Teorema:
- Seja $a \geq 1$ e $b > 1$ constantes, seja f(n) uma função e seja T(n) definida como:
$$T(n) = aT(\frac{n}{b}) + f(n)$$
- Então T(n) pode ser limitado assintoticamente como:
	- Se $f(n) = O(n^{log_{b}a-x})$ para algum x > 0, então $T(n) = \Theta(n^{\log_ba})$
	- Se $f(n) = \Theta(n^{\log_ba})$, então $T(n) = \Theta(n^{\log_ba}logn)$
	- Se $f(n) = \Omega(n^{\log_ba+x})$ para algum x > 0 e se $a\times f(\frac{n}{b}) \leq c \times f(n)$ para algum c < 1 e para todo n suficientemente grande, então $T(n) = \Theta(f(n))$
# O Problema da Ordenação
Ordenação ou classificação é largamente utilizada:
- Listas telefônicas
- Grandes sistemas de Banco de Dados e processamento de dados
	- 25% da computação em ordenação
- Algoritmos de ordenação são ilustrativos:
	- Como resolver problemas computacionais
	- Como lidar com estruturas de dados
	- Como desenvolver algoritmos elegantes e como analisar e comparar seus desempenhos
Ordenar é organizar uma sequência de elementos de modo que os mesmos estabeleçam alguma relação de ordem. Diz-se que os elementos $k_1,\, ...\, , \, k_n$ estarão dispostos de modo que $k_1 \leq k_2 \leq \, ... \, \leq k_n$.
Facilita a busca/localização/recuperação de um elemento dentro do conjunto a que pertence.
Ocasionalmente, dá menos trabalho buscar um elemento em um conjunto desordenado do que ordenar primeiro e buscar depois. Por outro lado, se a busca for uma operação frequente, vale a pena ordenar (a classificação pode ser feita somente uma vez). Mas isso depende das circunstâncias.
Terminologia:
- Ordenação de registros (em um "arquivo"), em que cada registro é ordenado por sua chave
- Ordenação interna x externa
	- Interna: se todos os registros cabem na memória principal (um único array)
	- Externa: se os dados não cabem na memória principal, precisando ser armazenados em fita ou disco
- Ordenação estável
	- Ordenação original de registros com mesma chave é preservada após a ordenação dos registros
- Ordenação sobre os próprios registros
	- Os registros são trocados de posição
- Ordenação por endereços
	- Mantém-se uma tabela de ponteiros para os registros e alteram-se somente os ponteiros durante a ordenação
- Registros a serem ordenados podem ser complexos ou não
	- Exemplos:
		- Dados de empregados de uma empresa, sendo que a ordenação deve ser pelo RG do empregado
		- Números inteiros
	- Métodos de ordenação independem desse fator
Existem vários meios de implementar ordenação. Dependendo do problema, um algoritmo apresenta vantagens e desvantagens sobre outros. Para comparar faz-se análise de complexidade.
Os algoritmos mais conhecidos baseados em troca são:
- Bubble-sort, também chamado de método da bolha
- Quick-sort, ou ordenação rápida ou ordenação por troca de partição
## Bubble-sort
É um dos métodos mais conhecidos e intuitivos. A ideia básica é percorrer o vetor várias vezes e a cada iteração comparar cada elemento com o seu sucessor (vetor[i] com vetor[i+1]) e trocá-los de lugar caso estejam na ordem incorreta.
~~~C
void bubblesort(int v[], int n){
	int i, j, aux;

	for
}
~~~