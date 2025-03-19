# História
## Leonhard Paul Euler (1707-1783)
Considerado o pai da teoria dos grafos, ele foi um matemático e físico que viveu na Rússia e na Alemanha. Ficou parcialmente cego aos 28 anos e totalmente cego nas últimas 2 décadas de vida. Ele resolveu o problema das 7 pontes na cidade de Konigsberg na Alemanha em 1735.
O problema era: na antiga cidade prussiana de Konigsberg (atual Kaliningrado na Rússia) havia 7 pontes que conectavam 2 ilhas. Hoje somente três pontes daquela época ainda existem no local (duas da época de Euler e uma que foi reconstruída). Duas foram destruídas durante a segunda guerra, outras duas foram destruídas para formar juntas uma só via moderna.
A solução: considerando vértices de partida, de chegada e intermediários. Vértices intermediários devem ter número par de arestas, pois é preciso chegar e sair do vértice sem passar pela mesma aresta. Vértices de partida e de chegada não fazem diferença. Todos os vértice tem número ímpar de arestas.
# Conceitos Básicos (ver slides para completar)
## Definição Básica
Um grafo é uma abstração matemática constituída de um conjunto de vértices V e um conjunto de arestas A conectando pares de vértices. $G = (V, A)$, na nomenclatura usual temos vértices ou nó e aresta (ou arco, link, ligação). Grau é o número de arestas de um vértice.
Grafos podem ser direcionados ou não. Grafos podem ter ciclos. Arestas podem ter peso. Grau pode ser de entrada ou de saída.
## Multigrafo
Quando um grafo possui mais de uma aresta interligando os mesmos dois vértices diz-se que este grafo possui arestas múltiplas (ou arestas paralelas). Ele é chamado de multigrafo ou grafo múltiplo. Por exemplo:
(print dos slides)
Um grafo simples é um grafo que não possui arestas múltiplas.
## Grafo Trivial e Grafo vazio
Um grafo é dito trivial se for de ordem 0 ou 1. Por exemplo:
(colocar print do slide)
Um grafo vazio $G = (\emptyset, \emptyset)$ pode ser representado somente por $G = \emptyset$. 
## Laço
Se houver uma aresta $e$ do grafo $G$ que possui o mesmo vértice como extremos, ou seja, $e=(x,x)$, então é dito que este grafo possui um laço. Exemplo:
(print do slide)
## Arestas Adjacentes
Diz-se que duas arestas são adjacentes (ou vizinhas) quando possuírem um mesmo extremo ou vértice. Assim:
(foto do slide)
A aresta $e = (v_3, v_4)$ é dita incidente a $v_3$ e a $v_4$. Ou, duas arestas adjacentes são incidentes a um vértice comum.
## Grafo Completo
Um grafo é completo se todos os seus vértices forem adjacentes. Um grafo completo $K_n$ possui $\frac{n(n-1)}{2}$ arestas.
(foto dos slides)
## Aplicações
- Cada vértice é uma tarefa de um grande projeto. Há uma aresta de x a y se x é pré-requisito de y, ou seja, se x deve estar pronta antes que y possa começar.
- Cada vértice é uma página na teia WWW. Cada aresta é um link que leva de uma página a outra (Há cerca de 2 milhões de vértices e 5 milhões de arcos).
- Outros: rede de computadores, rotas de voos, redes de telefonia, etc
## Grafos Orientados
Um grafo orientado (ou dígrafo) $D = (V, E)$ consiste de um conjunto $V$ (vértices) e de um conjunto de $E$ (arestas) de pares ordenados...
## Grau
O grau $d(v)$ de um vértice $v$ corresponde ao número de vértices adjacentes a v (ou ao número de arestas incidentes a $v$).
Em um grafo orientado
- O grau de saída ($d_{out}) de um vértice v corresponde ao número de arestas divergentes (que saem) de v
- O grau de entrada de um vértice v corres