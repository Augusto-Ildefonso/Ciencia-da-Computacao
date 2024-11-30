# Grafos
Dado um conjunto $V$, denotamos por $P_{2}(V) := \{S \subset V / |S| = 2\}$ o conjunto dos subconjuntos de pares de elementos de V. Note que se $|V| \leq 1$, então $P_{2}(V) = \emptyset$. É claro que $\displaystyle |P_{2}| = \left( \begin{matrix} |V| \\ 2 \end{matrix} \right)$, com a seguinte convenção: o coeficiente binomial é nulo se ele não fizer "sentido".

Um grafo (finito) $G$ é um par $G = (V, E)$, onde $V$ é um conjunto finito e $E \subset P_{2}(V)$. O conjunto $V$ é chamado de conjunto dos vértices de $G$ e o conjunto $E$ é chamado de conjunto das arestas (*edges*) de $G$. Uma aresta $\{v,u\} \in E$ também é representada simplesmente por $vu$. Na prática, não fazemos distinção entre um grafo e a sua representação gráfica com pontos (vértices) e traços ligando esses pontos (arestas).

Seja $G = (V, E)$ um grafo. Dizemos que dois vértices $v \neq u \in V$ são vizinhos ou adjacentes se $vu \in E$. Também dizemos que a aresta $vu$ incide nos vértices $v$ e $u$. Dado $v \in V$, a quantidade  $d_{G}(v) := \{u \in V / \{v\} \, | \, u \,\, é \,\, vizinho \,\, de \,\, v\}$ é chamada de grau (*degree*) do vértice $v$. Se $G$ estiver subentendido, denotamos $d_{G}(v)$ por $d(v)$. O grau representa o número de vizinhos que um vértice tem.

Seja $G = (V, E)$ um grafo finito, então existem pelo menos dois vértices de $G$ com o mesmo grau. Pode-se verificar essa proposição considerando um $n := |V|$. Primeiramente, note que, qualquer que seja $v \in V$, temos que $0 \leq d(v) \leq n - 1$. De duas, uma:
- ou $G$ possui um vértice de grau $n- 1$
- ou $G$ não possui nenhum vértice de grau $n-1$

No primeiro caso, o grau de qualquer vértice $u \in V$ satisfaz $1 \leq d(u) \leq n-1$. Como são $n$ os vértices, e como seus graus podem assumir $n-1$ valores, o princípio da casa dos pombos ("se tivermos $n+1$ pombos para serem colocados em $n$ casas, então pelo menos uma casa deverá ter, pelo menos, dois pombos") garante que dois vértices terão o mesmo grau. No segundo caso, o grau de qualquer vértice $u \in V$ satisfaz $0 \leq d(u) \leq n-2$. Como o grau ainda pode assumir $n-1$ valores apenas, e continuam sendo $n$ os vértices, novamente dois vértices necessariamente compartilharão um mesmo grau.

Seja $G = (V, E)$ um grafo, temos que um caminho em $G$ é uma sequência $(v_{1}, v_{2}, ..., v_{N})$ de vértices tais que:
- $v_{i}$ e $v_{i+1}$ são adjacentes, qualquer que seja $1 \leq i \leq N-1$
- as arestas $v_{i}v_{i+1}$ e $v_{j}v_{j+1}$ são distintas se $1 \leq i \neq j \leq N - 1$

Se $v_{N} = v_{1}$ (o que só pode acontecer se $|V| \geq 3$ e $N \geq 4$), dizemos que o caminho é fechado, ou também que é um ciclo. Finalmente, dizemos que o caminho $(v_{1}, v_{2}, ..., v_{N})$ liga $v_{1}$ a $v_{N}$.

Dizemos que um grafo $G = (V, E)$ é conexo se para qualquer par de vértices $w \neq u \in V$ existe um caminho que liga $w$ a $u$. Em outras palavras: $G$ é conexo se for possível conectar quaisquer dois vértices distintos através de um caminho em $G$.

Seja $G = (V, E)$ um grafo com $n$ vértices. Se $\begin{align} d(v) \geq \left\lfloor {\frac{n}{2}} \right\rfloor  \end{align}$, $\forall \, v \in V$, então $G$ é conexo. Para demonstrar, considere $v \neq u \in V$. Se $v$ e $u$ forem adjacentes, ($v$, $u$) é um caminho ligando $v$ a $u$. Se  $v$ e $u$ não forem adjacentes, vamos mostrar que $v$ e $u$ possuem um vizinho $w$ em comum, de modo que ($v$, $w$, $u$) é um caminho que liga $v$ a $u$. Pela hipótese acima, a quantidade de vizinhos de $v$ e de $u$ é pelo menos $2 \times \left\lfloor {\frac{n}{2}} \right\rfloor$. Como $2 \times \left\lfloor {\frac{n}{2}} \right\rfloor$ é igual a $n$ ou $n - 1$ (a depender da paridade de $n$), e como a quantidade de vértices de $G$ distintos de $v$ e de $u$ é $n-2$, o princípio da casa dos pombos garante que algum dos $n-2$ vértices distintos de $v$ e de $u$ é vizinho tanto de $v$ quanto de $u$. Essa condição é suficiente para verificar a conexidade, mas não é necessária para garantir a conexidade. Ou seja, um grafo pode ser conexo e não cumprir essa condição.
## Teorema de Euler
Seja $G = (V,E)$ um grafo, temos: 
$\begin{align} 2 \times |E| = \sum_{v \in V} d(v) \end{align}.$
Primeiramente, note que, qualquer que seja $v \in V$, $d(v)$ também é a quantidade de arestas que incide em $v$. Seja $\epsilon = vu \in E$ uma aresta, então, $\epsilon$ é contada exatamente duas vezes na soma do lado direito da igualdade: uma vez na parcela $d(v)$ e outra vez na parcela $d(u)$, afinal $\epsilon$  incide apenas em $v$ e $u$. Mas $\epsilon$ também é contada duas vezes no termo do lado esquerdo. Logo, a igualdade acima é válida.

## Corolário de Euler
Seja $G =(V, E)$ um grafo, então a quantidade de vértices de $G$ de grau ímpar é par. Isso pode ser verificado se separarmos o conjunto dos vértices em dois subconjuntos disjuntos: o conjunto $V_{p}$ dos vértices de grau par e o conjunto $V_{i}$ dos vértices de grau ímpar. Daí, pelo teorema anterior temos que:
$\begin{align} 2 \times |E| = \sum_{v \in V_{p}} d(v) + \sum_{v \in V_{i}} d(v) \Longrightarrow \sum_{v \in V_{i}} d(v) = 2 \times |E| - \sum_{v \in V_{p}} d(v) \end{align}$ 
Então, como $\sum_{v \in V_{p}} d(v)$ é par, segue que $\sum_{v \in V_{i}} d(v)$ também é par, o que por sua vez, implica que $|V_{i}|$ é par, pois uma soma de uma quantidade ímpar de parcelas ímpares é sempre ímpar.
# Árvores
Uma árvore (*tree*) é um grafo sem ciclos. Então, seja $T = (V, E)$ uma árvore, um vértice $v$ de $T$ é chamado de folha se $d_{T}(v) \leq 1$. Pela conexidade de $T$, se $|V| \geq 2$ então $d(v) \geq 1$ qualquer que seja $v \in V$. Logo, $d(v) = 0$ só quando $|V| = 1$.

Toda árvore finita possui pelo menos uma folha. Se ela tiver pelo menos dois vértices, então ela tem pelo menos duas folhas. Para demonstrar suponha uma árvore de um único vértice tem exatamente uma folha. Suponha agora que a árvore $T$ possua pelo menos dois vértices. Como $T$ é finita, a quantidade de caminhos nela também é finita. Seja ($v_1, . . . , v_N$) um caminho em $T$ com a maior quantidade possível de arestas. Afirmo que $v_1$ e $v_N$ são folhas. De fato, suponha que $v_1$ não é uma folha, ou seja: $d(v_1) ⩾ 2$. Daí, $v_1$ possui um vizinho $v_0$ distinto de $v_2$. Esse $v_0$ não é nenhum dos vértices do caminho ($v_1, . . . , v_N$), pois se assim não fosse, $T$ teria um ciclo, o que é impossível e acontecer uma vez que árvores não possuem ciclos. Mas daí, ($v_0, v_1, . . . , v_N$) é um caminho em $T$
com uma aresta a mais que ($v_1, . . . , v_N$), o que também é impossível de acontecer pois o caminho ($v_1, . . . , v_N$) já possui a maior quantidade possível de arestas que um caminho em $T$ pode ter. O mesmíssimo argumento mostra, mutatis mutandis, que $v_N$ também é uma folha.

Uma árvore infinita não pode possuir folhas.

A quantidade de arestas numa árvore finita está unicamente determinada pela sua correspondente quantidade de vértices. Assim, uma árvore com $n$ vértices possui $n-1$ arestas. Para demonstrar procedemos por indução na quantidade $n$ de vértices da árvore $T$. Se $n = 1$, $T$ certamente possui $1 - 1 = 0$ arestas. Suponha que qualquer árvore com $n$ vértices possua $n - 1$ arestas. Considere uma árvore $T$ com $n + 1$ vértices. Já sabemos que $T$ possui pelo menos uma folha, digamos $v$. Seja $T^*$ o grafo obtido de $T$ através da excisão da folha $v$ e sua correspondente aresta. Note que $T^*$ ainda é conexo (pois qualquer caminho em $T$ que passa por $v$ deve ou começar ou terminar em $v$) e não possui ciclos (se possuísse, $T$ também possuiria). Em outras palavras: $T^*$ é uma árvore, e além disso possui $n$ vértices. Pela hipótese de indução, $T^*$ possui $n - 1$ arestas. Mas daí é claro que $T$ possui $n = (n + 1) - 1$ arestas.

Qualquer grafo conexo com $n$ vértices e $n-1$ arestas é uma árvore. Ou seja, ser uma árvore (finita) é uma condição indispensável para que um grafo (finito) conexo com $n$ vértices não possua $n-1$ arestas.

Uma consequência dos dois últimos resultados diz essencialmente que as árvores (finitas) são os grafos conexos que possuem a menor quantidade possível de arestas. Logo, se um grafo com $n$ vértices é conexo, então ele possui no mínimo $n-1$ arestas. Para demonstração temos de duas uma:
- ou o grafo não possui ciclo, em cujo caso ele é uma árvore e possui $n-1$ arestas
- ou o grafo possui ciclo, em cujo caso a quantidade de arestas é maior ou igual a $n$
# Aritmética Modular
## Algoritmo de Euclides e Congruência Modular
### Divisão Euclidiana
Sejam $a, b \in \mathbb{Z}$, com $b \neq 0$. Então existem, e são únicos, $q, r \in \mathbb{Z}$ tais que $a = q \cdot b + r$, com $0 \leq r < |b|$.  Os inteiros $q$ e $r$ da igualdade acima são chamados de *quociente* e *resto*, respectivamente, que resultam da divisão de $a$ por $b$.

Para demonstrar a afirmação acima, considere o conjunto $S_{a, b} := \{ a + qb \, / \, q \in \mathbb{Z} \}$ possui um menor elemento positivo $r$, pelo princípio da boa ordenação. Se fosse $r \geq |b|$, teríamos que $r = |b| + s$ para algum $0 \leq s < r$ (pois $|b| > 0$). Daí, $a = qb + r = qb \pm b + s = (q \pm 1)b + s$ de modo que $s \in S_{a,b}$ também. Mas $s < r$ é uma contradição à minimalidade de $r$.

Na situação do teorema anterior, escrevemos $a \equiv r \mod b$, e lemos "a é congruente a r módulo b". Em geral escrevemos $x \equiv y \mod b$, se $x - y$ (ou $y - x$) for múltiplo de $b$, ou, equivalentemente, se $x$ e $y$ deixam o mesmo resto quando dividido por b.
## Algoritmo de Euclides
Se $a = q \cdot b + r$ então $mdc{(a, b)} = mdc{(b, r)}$. Basta observar que o conjunto de divisores comuns de $a$ e $b$ é igual ao conjunto de divisores comuns de $b$ e $r$.
## Relações de Equivalência e Partições
Seja $\mathcal{C}$ um conjunto. Uma relação binária ~ em $\mathcal{C}$ é um subconjunto $R_{\sim}$ de $\mathcal{C} \times \mathcal{C}$. Se $(x, y) \in R_{\sim}$ escrevemos $x \sim y$. Dizemos que $\sim$ é uma relação de equivalência em $\mathcal{C}$ se
- $x \sim y$ qualquer que seja $x \in \mathcal{C}$ ($\sim$ é reflexiva)