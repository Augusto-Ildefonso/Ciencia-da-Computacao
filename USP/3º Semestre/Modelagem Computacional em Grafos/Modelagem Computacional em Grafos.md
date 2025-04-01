# História
## Leonhard Paul Euler (1707-1783)
Considerado o pai da teoria dos grafos, ele foi um matemático e físico que viveu na Rússia e na Alemanha. Ficou parcialmente cego aos 28 anos e totalmente cego nas últimas 2 décadas de vida. Ele resolveu o problema das 7 pontes na cidade de Konigsberg na Alemanha em 1735.
O problema era: na antiga cidade prussiana de Konigsberg (atual Kaliningrado na Rússia) havia 7 pontes que conectavam 2 ilhas. Hoje somente três pontes daquela época ainda existem no local (duas da época de Euler e uma que foi reconstruída). Duas foram destruídas durante a segunda guerra, outras duas foram destruídas para formar juntas uma só via moderna.
A solução: considerando vértices de partida, de chegada e intermediários. Vértices intermediários devem ter número par de arestas, pois é preciso chegar e sair do vértice sem passar pela mesma aresta. Vértices de partida e de chegada não fazem diferença. Todos os vértice tem número ímpar de arestas.
# Conceitos Básicos
## Definição Básica
Um grafo é uma abstração matemática constituída de um conjunto de vértices V e um conjunto de arestas A conectando pares de vértices. $G = (V, A)$, na nomenclatura usual temos vértices ou nó e aresta (ou arco, link, ligação). Grau é o número de arestas de um vértice.
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
Um grafo é completo se todos os seus vértices forem adjacentes. Um grafo completo $K_n$ possui $\frac{n(n-1)}{2}$ arestas.
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
Um grafo é totalmente desconexo quando não possui arestas.
Todo grafo euleriano é conexo e todos os seus vértices possuem grau par.