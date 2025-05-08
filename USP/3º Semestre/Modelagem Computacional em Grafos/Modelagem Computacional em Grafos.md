# História
## Leonhard Paul Euler (1707-1783)
Considerado o pai da teoria dos grafos, ele foi um matemático e físico que viveu na Rússia e na Alemanha. Ficou parcialmente cego aos 28 anos e totalmente cego nas últimas 2 décadas de vida. Ele resolveu o problema das 7 pontes na cidade de Konigsberg na Alemanha em 1735.
O problema era: na antiga cidade prussiana de Konigsberg (atual Kaliningrado na Rússia) havia 7 pontes que conectavam 2 ilhas. Hoje somente três pontes daquela época ainda existem no local (duas da época de Euler e uma que foi reconstruída). Duas foram destruídas durante a segunda guerra, outras duas foram destruídas para formar juntas uma só via moderna. A questão que inquietava os moradores da cidade era: é possível fazer um caminho por todas as pontes passando uma e somente uma vez em cada uma delas?
A solução: considerando vértices de partida, de chegada e intermediários. Vértices intermediários devem ter número par de arestas, pois é preciso chegar e sair do vértice sem passar pela mesma aresta. Vértices de partida e de chegada não fazem diferença. Todos os vértice tem número ímpar de arestas.
# Conceitos Básicos
## Definição Básica
Um grafo é uma abstração matemática constituída de um conjunto de vértices $V$ e um conjunto de arestas $E$ conectando pares de vértices. $G = (V, E)$, na nomenclatura usual temos vértices ou nó e aresta (ou arco, link, ligação). Grau é o número de arestas de um vértice.
Grafos podem ser direcionados ou não. Grafos podem ter ciclos. Arestas podem ter peso. Grau pode ser de entrada ou de saída.
## Multigrafo
Quando um grafo possui mais de uma aresta interligando os mesmos dois vértices diz-se que este grafo possui arestas múltiplas (ou arestas paralelas). Ele é chamado de multigrafo ou grafo múltiplo. Por exemplo:
![[Pasted image 20250324143959.png]]
Um grafo simples é um grafo que não possui arestas múltiplas.
## Grafo Trivial e Grafo vazio
Um grafo é dito trivial se for de ordem 0 ou 1. Por exemplo:
![[Pasted image 20250324144049.png]]
Um grafo vazio $G = (\emptyset, \emptyset)$ pode ser representado somente por $G = \emptyset$. 
## Laço
Se houver uma aresta $e$ do grafo $G$ que possui o mesmo vértice como extremos, ou seja, $e=(x,x)$, então é dito que este grafo possui um laço. Exemplo:
![[Pasted image 20250324144103.png]]
## Arestas Adjacentes
Diz-se que duas arestas são adjacentes (ou vizinhas) quando possuírem um mesmo extremo ou vértice. Assim:
![[Pasted image 20250324144121.png]]
A aresta $e = (v_3, v_4)$ é dita incidente a $v_3$ e a $v_4$. Ou, duas arestas adjacentes são incidentes a um vértice comum.
## Grafo Completo
Um grafo é completo se todos os seus vértices forem adjacentes (possuem uma aresta em comum). Um grafo completo $K_n$ possui $\frac{n(n-1)}{2}$ arestas.
![[Pasted image 20250324144139.png]]
## Aplicações
- Cada vértice é uma tarefa de um grande projeto. Há uma aresta de x a y se x é pré-requisito de y, ou seja, se x deve estar pronta antes que y possa começar.
- Cada vértice é uma página na teia WWW. Cada aresta é um link que leva de uma página a outra (Há cerca de 2 milhões de vértices e 5 milhões de arcos).
- Outros: rede de computadores, rotas de voos, redes de telefonia, etc
## Grafos Orientados
Um grafo orientado (ou dígrafo) $D = (V, E)$ consiste de um conjunto $V$ (vértices) e de um conjunto de $E$ (arestas) de pares ordenados de vértices distintos.
![[Pasted image 20250324144219.png]]
Em um grafo orientado, cada aresta $e = (x, y)$ possui uma única direção de $x$ para $y$. Diz-se que $(x, y)$ é divergente de $x$ e convergente a $y$.
![[Pasted image 20250324145209.png]]
## Grau
O grau $d(v)$ de um vértice $v$ corresponde ao número de vértices adjacentes a v (ou ao número de arestas incidentes a $v$).
![[Pasted image 20250324145236.png]]
Em um grafo orientado
- O grau de saída $d_{out}(v)$ de um vértice $v$ corresponde ao número de arestas divergentes (que saem) de $v$.
- O grau de entrada $d_{in}(v)$ de um vértice $v$ corresponde ao número de arestas convergentes (que chegam) em $v$.
![[Pasted image 20250324145724.png]]
Um vértice com grau de saída nulo, ou seja, $d_{out}(v) = 0$, é chamado de **sumidouro (ou sorvedouro)**. Já um vértice com grau de entrada nulo, ou seja, $d_{in}(v) = 0$, é chamado de **fonte**. Diz-se que um grafo é **regular** se todos os seus vértices tiverem o mesmo grau.
## Grafo Valorado
Um grafo valorado $G(V, A)$ consiste de um conjunto finito não vazio de vértices $V$, ligados por um conjunto $A$ de arestas (ou arcos) com pesos. O conjunto $A$ consiste de triplas distintas da forma $(v, w, valor)$ em que $v$ e $w$ são vértices pertencentes a $V$ e o valor é um número real.
Exemplo:
- Quão minha amiga é uma certa pessoa?
	- Grafos podem ter arestas com pesos representando a força da relação entre os vértices.
	- Ex: 0 inimiga, 5 colega, 10 amiga
![[Pasted image 20250324150409.png]]
## Caminho
Um caminho entre dois vértices, $x$ e $y$, é uma sequência de vértices e arestas que une $x$ e $y$. Um caminho de k-vértices é formado por $k - 1$ arestas $(v_{1}, v_{2}), (v_{2}, v_{3}), ..., (v_{k-1}, v_{k})$, e o valor de $k-1$ é o comprimento do caminho.
![[Pasted image 20250324150714.png]]
### Caminho Simples
Um caminho é simples se todos os vértices que o compõem forem distintos.
![[Pasted image 20250324151053.png]]
### Menor Caminho
A multiplicidade de possíveis caminhos num grafo pode gerar a necessidade de buscar o menor caminho a um determinado vértice.
### Circuito e Ciclo
Um circuito é um caminho $P = v_{1}, v_{2}, ..., v_{k}, v_{k+1}$, onde $v_{1} = v_{k+1}$. Um ciclo é um circuito onde todos os vértices são distintos (exceto pelo primeiro e o último). Um grafo é cíclico se apresentar ao menos um ciclo.
![[Pasted image 20250324151449.png]]
### Caminho Hamiltoniano
Um caminho hamiltoniano é aquele que contém cada vértice do grafo exatamente uma vez. Um ciclo $v_{1}, v_{2}, ..., v_{k}, v_{k+1}$ é hamiltoniano quando o caminho $v_{1}, v_{2}, ..., v_{k}$ for um caminho hamiltoniano.
![[Pasted image 20250324151713.png]]
### Caminho Euleriano
Um caminho euleriano é aquele que contém cada aresta do grafo exatamente uma vez.
![[Pasted image 20250324152031.png]]
## Grafo Hamiltoniano
Um grafo é Hamiltoniano se contiver um ciclo hamiltoniano.
![[Pasted image 20250324151808.png]]
## Grafo euleriano
Um grafo é euleriano se há um circuito em $G$ que contenha todas as arestas.
![[Pasted image 20250324152043.png]]
## Subgrafo
Um subgrafo $G' = (V', E')$ de um grafo $G = (V, E)$ é um grafo tal que $V' \subseteq V$ e $E' \subseteq E$.
![[Pasted image 20250324152713.png]]
## Grafo Conexo
Um grafo $G = (V, E)$ é conexo quando existe um caminho entre cada par de vértices de $G$, caso contrário, $G$ é desconexo. Para um grafo orientado, a decisão é feita sem considerar a orientação das arestas.
![[Pasted image 20250415142815.png]]
![[Pasted image 20250415142823.png]]
Um grafo é totalmente desconexo quando não possui arestas.
![[Pasted image 20250415142835.png]]
Todo grafo euleriano é conexo e todos os seus vértices possuem grau par.
## Dígrafo Fortemente Conexo
Um grafo orientado $D = (V, E)$ é dito ser fortemente conexo quando existe um caminho entre cada par de vértices $(x, y)$ e também entre $(y, x)$.
![[Pasted image 20250415204640.png]]
## Componente Conexa
Uma componente conexa corresponde a um subgrafo conexo maximal.
![[Pasted image 20250415204842.png]]
## Grafo Bipartido
Um grafo $G = (V, E)$ é bipartido quando o seu conjunto de vértices $V$ puder ser dividido em dois subconjuntos $V_1$, $V_2$ tais que toda aresta do conjunto $E$ une um vértice de $V_1$ a outro vértice de $V_2$. Matematicamente falando: $$V = V_1 \cup V_2; V_1 \cap V_2 = \emptyset$$ e
$$\forall e = (u, v) \in E \longrightarrow u \in V_1 \, e \, V=v \in V_2$$
![[Pasted image 20250424131027.png]]
### Grafo Bipartido Completo
Um grafo bipartido completo tem a notação $K_{|V_{1}||V_{2}|}$. Matematicamente falando, temos: $$V = V_1 \cup V_2; V_1 \cap V_2 = \emptyset; \forall e = (u, v) \in E \longrightarrow u \in V_1 \, e \, V=v \in V_2; \forall u \in V_{1}, \forall v \in V_{2} \longrightarrow e = (u,v) \in E$$
## Complemento
O complemento de um grafo $G = (V, E)$ é um grafo $G' = (V', E')$ tal que $V = V'$ e $E'$ é complementar a $E$.
![[Pasted image 20250424131648.png]]
## Isomorfismo
Dois grafos $G = (V, E)$ e $G’ = (V’, E’)$ são isomorfos entre si se existe correspondência entre os seus vértices e arestas de forma a preservar a relação de incidência, ou seja, $| V | = | V’| , | E | = | E’|$ e existe uma função unívoca $f : V → V’$ , tal que $e=(x,y) \in E$ se e somente se $e’=(f(x),f(y)) \longrightarrow E’$. Em outras palavras, eles tem o mesmo número de vértices e arestas e tem uma função que leva de um grafo ao outro (parece uma mudança de base e visualmente parece que aumentou de tamanho ou deslocou).
![[Pasted image 20250424132756.png]]
![[Pasted image 20250424132804.png]]
## Árvore
Uma árvore é um grafo conexo e acíclico.
![[Pasted image 20250424132851.png]]
## Árvore enraizada
Uma árvore enraizada é um grafo orientado no qual há um vértice (raiz) do qual todas as arestas se afastam (saem dele).![[Pasted image 20250424132958.png]]
## Florestas
Florestas é um conjunto de árvores.![[Pasted image 20250424133126.png]]
## Subgrafo Gerador
Um subgrafo gerador $G' = (V', E')$ de um grafo $G = (V, E)$ é um grafo tal que $V = V'$ e $E' \subset E$ (está contido).![[Pasted image 20250424133750.png]]
## Árvore Geradora
Uma árvore geradora $G' = (V', E')$ de um grafo $G = (V, E)$ é um subgrafo gerador que é uma árvore.
![[Pasted image 20250424133921.png]]
![[Pasted image 20250424133927.png]]
## Subgrafo Induzido
Um subgrafo induzido $G' = (V', E')$ de um grafo $G = (V, E)$ é um grafo tal que $V' \subset V$ e $E'$ contém todas as arestas em $E$ que tem as duas extremidades em $V'$.![[Pasted image 20250424134204.png]]
# Estrutura de Dados
A escolha da estrutura de dados certa para a representação de grafos tem um enorme impacto no desempenho do algoritmo. Para grafos temos duas representações básicas: matriz de adjacência e listas lineares de adjacência.
## Matriz de Adjacência
Dado um grafo $G = (V, E)$, a matriz de adjacência $M$ é uma matriz de ordem $n \times n$ tal que $n$ é o número de vértices e temos os valores:
- $M[i, j] = 1$ se existir aresta de $i$ a $j$
- $M[i,j] = 0$ se não existir aresta de $i$ a $j$
Veja o exemplo a seguir de um grafo e sua matriz de adjacência.
![[Pasted image 20250424135306.png]]
![[Pasted image 20250424135315.png]]
Se o grafo for direcionado. a matriz $M[i,j]$ indica uma aresta divergente de $i$ e convergente em $j$, ou seja, $i \longrightarrow j$.
Se um grafo for valorado, a matriz $M[i,j]$ deve conter o peso associado à aresta. Se não existir uma aresta entre $i$ e $j$, então é necessário utilizar um valor que não possa ser usado como peso (como o valor 0 ou -1, por exemplo).
Obs: uma matriz simétrica é aquela que considera a diagonal principal como o eixo de simetria e compara que o lado de cima e debaixo são simétricos.
Essa forma de representação é a mais simples. Ela possui algumas propriedades:
- representa um grafo sem ambiguidade
- é simétrica para um grafo não direcionado
- armazenamento: $O(n^2)$
- teste se aresta $(i, j)$ está no grafo: $O(1)$
- representação útil para grafos densos
- boa quando desejamos buscar arestas rapidamente: tempo constante
- ruim quando é preciso examinar a matriz toda: $O(n^2) = O(|V|^2)$
Uma matriz de adjacência caracteriza univocamente (unicamente) um grafo. Mas, um mesmo grafo pode corresponder a várias matrizes diferentes.
## Estrutura de Adjacências
Dado um grafo $G = (V, E)$, a estrutura de adjacências $A$ é um conjunto de $n$ listas $A(v)$, uma para cada vértice $v$, dado que $v \in V$. Cada lista $A(v)$ é denominada lista de adjacências do vértice v e contém os vértices $w$ adjacentes a $v$ em $G$.
Ou seja, a estrutura de adjacências é um vetor de n-elementos que são capazes de apontar, cada um, para uma lista linear. O i-ésimo elemento do vetor aponta para a lista linear das arestas que incidem no vértice i.
![[Pasted image 20250427192130.png]]
Essa representação é mais elaborada. Ela tem as seguintes propriedades:
- Armazenamento: $O(m + n)$
- Teste se aresta $(i, j)$ está no grafo: $O(d_{i})$, com $d_{i}$ sendo o grau do vértice $i$.
A maior parte dos problemas relacionados à teoria dos grafos pode ser resolvida com estruturas de adjacências. Entretanto, quanto maiores os grafos, menos eficiente essa estrutura se torna para as mesmas tarefas.
## Comparação
![[Pasted image 20250425113200.png]]
![[Pasted image 20250427192056.png]]
# TAD Grafo
Os operadores do TAD Grafo são:
- Criar um grafo vazio
- Inserir uma aresta no grafo
- Verificar que existe determinada aresta no grafo
- Obter a lista de vértices adjacentes a determinado vértice
- Retirar uma aresta do grafo
- Imprimir o grafo
- Obter o número de vértices do grafo
- Obter o transposto de um grafo direcionado
- Obter a aresta de menor peso de um grafo
# Busca
## Busca em Árvore
Problemas de busca são frequentemente descritos utilizando árvores, nas quais o nó inicial é a raiz, que é onde começa a busca, e ela termina no nó objetivo. O objetivo geralmente é encontrar um caminho que ligue o nó inicial a um nó objetivo.
Quando realizamos uma busca em árvores, temos uma entrada que tem: a descrição dos nós inicial e objetivo e o procedimento que produz os sucessores de um nó arbitrário. E como saída temos: uma sequência legal de nós iniciando com o nó inicial e terminando com o nó objetivo.
### Árvore de Busca
Uma busca pode ser definida graficamente como uma árvore. O objetivo em uma árvore de busca é atravessar a árvore partindo do estado inicial até o estado final.
![[Pasted image 20250425121402.png]]
### Tipos de Busca
#### Busca em Profundidade
A busca em profundidade envolve buscar o final de um caminho antes de tentar um caminho alternativo
![[Pasted image 20250425121509.png]]
#### Busca em Largura
A busca em largura envolve escolher um caminho e segui-lo até o próximo ponto de decisão ou até o objetivo ser atingido.
![[Pasted image 20250425121641.png]]
### Problemas da Busca
Com o aumento da árvore de decisão e do número possíveis de caminhos, o tempo de busca aumenta. Porém, existem várias formas de reduzir o tempo de busca (como com a busca heurística ou informada).
### Possíveis Situações
Quando formos realizar uma busca, podemos nos deparar com algumas situações especiais, como:
- Mais de um nó objetivo
- Mais de um nó inicial
Nessas situações podemos:
- Encontrar qualquer caminho de um nó inicial para um nó objetivo
- Encontrar o melhor caminho
### Definições Importantes
Profundidade é o número de ligações entre um dado nó e o nó inicial. Já largura é o número de sucessores (filhos) de um nó.
### Algoritmo Básico de Busca em Árvore
1. Definir um conjunto $L$ de nós iniciais
2. Se $L$ é vazio
	1. Então
		1. Busca não foi bem sucedida
	2. Senão
		1. Escolher um nó $n$ de $L$
3. Se $n$ é um nó objetivo
	1. Então
		1. Retornar o caminho do nó inicial até n
		2. Parar
	2. Senão
		1. Adicionar a $L$ todos os filhos de $n$, rotulando cada um com o seu caminho até o nó inicial
		2. Voltar ao passo 2
### Algoritmos de Busca
Existem diversos algoritmos de busca diferentes, o que os distingue é a maneira como o nó $n$ é escolhido no passo 2.
Alguns métodos de busca são:
- Busca cega: a escolha depende da posição do nó na árvore de busca
- Busca heurística: a escolha utiliza informações específicas do domínio para ajudar na decisão
### Busca Cega
Existem um grande número de métodos para realizar as técnicas de busca cega. Dois deles são:
- Busca em Profundidade (BP)
	- A árvore é examinada da raiz para as folhas
	- Aconselhável nos casos onde os caminhos improdutivos não são muito longos
- Busca em Largura (BL)
	- A árvore é examinada da esquerda para a direita
	- Aconselhável quando o número de ramos não é muito grande
#### Algoritmo BP
1. Definir um conjunto $L$ de nós iniciais
2. Seja $n$ o primeiro nó de $L$
3. Se $L$ é vazio
	1. Então
		1. Busca não foi bem sucedida
4. Se $n$ é um nó objetivo
	1. Então 
		1. Retornar caminho do nó inicial até $n$
		2. Parar
	2. Senão
		1. Remover $n$ de $L$
		2. Adicionar ao início de $L$ todos os filhos de $n$, rotulando cada um com o seu caminho até o nó inicial
		3. Voltar ao passo 2
#### Algoritmo BL
1. Definir um conjunto $L$ de nós iniciais
2. Seja $n$ o primeiro nó de $L$
3. Se $L$ é vazio
		1. Então
			1. Busca não foi bem sucedida
4. Se $n$ é um nó objetivo
	1. Então
		1. Retornar o caminho do nó inicial até $n$
		2. Parar
	2. Senão
		1. Remover $n$ de $L$
		2. Adicionar ao final de $L$ todos os filhos de $n$, rotulando cada um com o seu caminho até o nó inicial
		3. Voltar ao passo 2
#### Observações
- BP e BL não precisam ser realizadas em uma ordem específica
- Memória utilizada pelas duas técnicas
	- BP: precisa armazenar todos os filhos não visitados de cada nó entre nó atual e nó inicial
	- BL: antes de examinar nó a uma profundidade $d$, é necessário examinar e armazenar todos os nós a uma profundidade $d - 1$
	- BP utiliza menos memória
- Quanto ao tempo
	- BP é geralmente mais rápida
	- Métodos de busca cega não examinam a árvore de forma ótima, o que poderia minimizar o tempo gasto para resolver o problema
### Técnicas Exaustivas de Busca
- Completude: a solução sempre será encontrada?
- "Optimalidade": o caminho mais curto será encontrado antes dos caminhos mais longos?
- Eficiência: quais são os requisitos de memória e tempo de execução?
## Busca em Grafo
Para realizar uma busca em um grafo temos que percorre-lo, logo, isso é um problema fundamental. Deve-se ter uma forma sistemática de visitar as arestas e os vértices. O algoritmo deve ser suficientemente flexível para ajustar-se à diversidade de grafos.
Ao percorrer um grafo temos que pensar em alguns fatores:
- Eficiência: não deve haver repetições (desnecessárias) de visitas a um vértice e/ou aresta
- Correção: todos os vértices e/ou arestas devem ser visitados
Para solucionar esses problemas, devemos marcar os vértices com:
- não visitados
- visitados
- processados
Então, devemos manter uma lista de vértices no estado "visitados". Para isso, há duas possibilidades:
- Fila (First in first out) via append e remove firts ou insert e remove last
- Pilha (last in first out) via push e pop (insert e remove firts)
### Breadth-first Search (BFS)
Também conhecida como busca em largura, percorre-se um grafo $G$ a partir de um vértice inicial $s$ informado. Pode realizar processamento à medida que visita vértices e arestas. O passo a passo dele é:
1. Descobre todos os vértices alcançáveis a partir de $s$
2. Calcula a distância de $s$ a cada vértice alcançável
3. Gera uma árvore em largura com raiz em $s$ com todos os vértices alcançáveis $v$, tal que o caminho na árvore corresponde ao menor caminho entre $s$ e $v$
A complexidade do BFS é $O(|V| + |E|)$, ou seja, é linear em relação ao tamanho da representação de $G$ por lista de adjacência:
- Todos os vértices são empilhados/desempilhados no máximo uma vez. O custo de cada uma dessas operações é $O(1)$, e elas são executadas $O(|V|)$ vezes
- A lista de adjacências de cada vértice é percorrida no máximo uma vez (quando o vértice é desempilhado). O tempo total é $O(|E|)$ (soma dos comprimentos de todas as listas, igual ao número de arestas).
- Inicialização é $O(|V|)$
```
BFS (G,s)
	for each vertex u  V[G] – {s} do
		color[u] = “WHITE”
		d[u] = INF
		p[u] = NIL
	end-for
	color[s]= GRAY, d[s] = 0, p[s] = NIL
	initialize(Q)
	enqueue(Q,s)
	while (not empty(Q)) do
		u = dequeue[Q]
		processe o vértice u conforme desejado
		for each v  Adj[u] do
			processe a aresta (u,v) conforme desejado
			if color[v] = “WHITE” then
				color[v] = “GRAY”
				d[v] = d[u] + 1
				p[v] = u
				enqueue(Q,v)
			end-if
		end-for
		color[u] = “BLACK”
	end-while
```
### Depth First Search (DFS)
Também conhecida como busca em profundidade. Ela é recursiva, eliminando assim a necessidade de uma estrutura de lista, fila ou pilha. Ela percorre um grafo $G$, podendo realizar processamento à medida que visita vértices e arestas.
A complexidade do DFS é $O(|V| + |E|)$. No algoritmo principal, cada for é $O(|V|)$. O DFS-visit é chamado exatamente uma vez para cada vértice de $|V|$ (na pior das hipóteses). No DFS-visit, o laço é executado $|adj[v]|$ vezes, ou seja, $O(|E|)$ no total.
Uma aplicação clássica do DFS consiste em decompor um grafo direcionado (dígrafo) em componentes fortemente conexos. Um grafo direcionado é fortemente conexo se quaisquer dois vértices são mutuamente alcançáveis entre si. Um componente fortemente conexo de um grafo é um subconjunto maximal $C$ de vértices de $V$ tal que qualquer par de vértices de $C$ é mutuamente alcançável.
```
DFS-graph (G)
	for each vertex u  V[G] do
		color[u] = “WHITE”
		p[u] = NIL
		end-for
		time = 0
		for each vertex u  V[G] do
			if color[u] = “WHITE” then
				DFS-visit(u)
			end-if
	end-for

DFS-visit(u)
	color[u] = “GRAY”
	time = time + 1
	d[u] = time
	for each v  Adj[u] do
		if color[v] = “WHITE” then
			p[v] = u
			DFS-visit(v)
		end-if
	end-for
	color[u] = “BLACK”
	f[u] = time = time + 1
```
### Caminhos mais curtos
Em grafos não-orientados e não-valorados o algoritmo $BFS(u)$ produz uma árvore de caminhos mais curtos entre $u$ (origem) e todos os demais vértices do grafo alcançáveis a partir dele. Assim, o vetor antecessor $p[u]$ é capaz de fornecer o caminho mais curto (menor número de arestas) entre $u$ e $v$, para qualquer $v$ em $V$, se ele existir.
Dado o vetor antecessor após BFS(v):
```
Imprimir_caminho_mais_curto(origem, v: tipoVértice) {
	se origem = v{
		escreve(origem)
	} senão {
		Imprimir_caminho_mais_curto(origem, antecessor(v))
		escreve(v)
	}
}
```
### Comparação
Em termos de memória, a busca em largura (BFS - Breadth-First Search) geralmente requer mais memória do que a busca em profundidade Depth-First Search. Isso ocorre porque a BFS mantém uma fila para armazenar todos os vértices que estão sendo visitados em cada nível da árvore de busca, enquanto a DFS geralmente mantém uma pilha de vértices que ainda não foram completamente explorados.
A memória máxima utilizada pelo BFS depende da profundidade máxima alcançada durante a travessia. O seja a quantidade de memória necessária pela BFS é proporcional ao número máximo de vértices em um nível da árvore de busca.
Tanto a busca em profundidade (DFS - Depth-First Search) quanto a busca em largura (BFS - Breadth-First Search) podem ser implementadas utilizando diferentes estruturas de dados para armazenar os vértices que precisam ser visitados.  O DFS usa uma pilha e segue o critério "último a entrar, primeiro a sair" (LIFO) . Isso significa que a DFS visita primeiro os vértices mais recentemente descobertos e continua explorando em profundidade até atingir um vértice sem vizinhos não visitados. Enquanto a BFS utiliza uma fila para armazenar os vértices a serem visitados. A fila segue a ordem "primeiro a entrar, primeiro a sair" (FIFO), o que garante que a BFS visite todos os vizinhos de um vértice antes de visitar os vizinhos dos vizinhos.
A busca em profundidade (DFS - Depth-First Search) não é um algoritmo ótimo porque não garante encontrar uma solução ótima para todos os problemas. Encontra uma solução porém não  garante que é de menor custo.
A busca em largura (BFS - Breadth-First Search) pode-se dizer que é ótima em encontrar a solução mais curta (em termos de número de arestas) em grafos não ponderados, onde todas as arestas têm o mesmo custo. Não garante ser ótima para todos os problemas, mas é ótima para encontrar a solução mais curta.
Em um grafo ponderado, onde as arestas têm pesos que representam custos, a DFS pode não encontrar o caminho mínimo entre dois vértices. Ela pode encontrar um caminho entre os vértices, mas não garante que seja o caminho com o menor custo.
# Ordenação Topológica
Define-se ordenação topológica para grafos orientados acíclicos. O objetivo da ordenação topológica é alinhar todos os vértices de um grafo em sequência, de forma que se a aresta $(u,v)$ pertence a $V$, então a aresta $u$ está antes de $v$ na sequência.