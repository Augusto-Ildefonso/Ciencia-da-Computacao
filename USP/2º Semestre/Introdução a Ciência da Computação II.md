# Análise de Algoritmos
Quando pensamos em análise de algoritmos podemos pensar em medir diversos recursos, como memória, largura da banda de comunicação, hardware, entre outros. Porém o foco principal é medir o tempo de computação de um algoritmo.

Antes de analisar algoritmos, devemos criar um modelo de computador para basear a análise. Esse modelo será baseado nos computadores reais do tipo RAM (random access memory), ele executa uma instrução por vez, sem operações concorrentes, e com um único processador. Geralmente, não é preciso descrever precisamente o modelo de RAM e processador pois isso tiraria a visão do projeto e da análise. As instruções presentes nesse modelo de RAM são: aritméticas (soma, subtração, multiplicação, divisão, resto, piso, teto), movimentação de dados e de controle. Cada uma dessas instruções demora um tempo constante.

É comum o tempo de execução de um algoritmo crescer conforme o número de elementos da entrada cresce também. Desse modo, expressa-se o tempo de execução em função do tamanho de sua entrada.

A melhor descrição para tamanho de entrada depende do problema que está trabalhando. Em casos de ordenação o mais natural é o número de elementos da entrada, em casos de dois inteiros o tamanho da entrada é melhor ser expresso pela quantidade de bits necessários para representar a entrada em binário, para grafos o tamanho da entrada são dois números (mostrando a quantidade de arestas e de vértices).

O tempo de execução é o número de operações primitivas/passos executados. Cada linha do pseudo código requer um tempo constate para ser executado, essa ideia está de acordo com o modelo RAM.

O foco da análise será o tempo do pior caso, mas é possível também calcular o tempo do melhor caso. Alguns motivos para escolher o tempo do pior caso é que ele oferece um limite superior para o tempo, ou seja, garantimos que para qualquer entrada, independentemente do número de elementos dela, o tempo nunca será superior ao determinado; para alguns algoritmos o pior caso é bem frequente (como busca de informações, que não estão presentes, em bancos de dados); por último, muitas vezes o tempo médio é tão ruim quanto o tempo do pior caso. Porém para análises probabilísticas, o tempo do caso médio é interessante, só que pode ser confuso por causa da definição do que seria uma entrada média.
## Ordem de crescimento
Agora, tendo estabelecido as regras anteriores, vamos realizar mais uma simplificação, pois o que nos interessa é a taxa de crescimento, ou ordem de crescimento, da função. Para fazer a análise da taxa de crescimento consideramos somente a variável de maior expoente, ignorando as constantes (que são pouco significativas) e também os termos de menor grau (que quando comparados ao de maior são pouco significativos também, para grandes valores de n).

Definimos um algoritmo como mais eficiente do que outro quando a sua taxa de crescimento é menor do que o outro. Vale ressaltar que como ignoramos as constantes e termos de ordem mais baixa, pode ser que para valores baixos de n, o algoritmo mais eficiente demore mais tempo do que o menos eficiente.
## Divisão e Conquista
É um tipo de algoritmo, recursivo, que divide o problema em subproblemas, semelhantes ao original mas de menor tamanho, e ao resolver os subproblemas, retornam ele recursivamente, juntando os resultados, para assim resolver o problema original.

O método de divisão e conquista é divido em 3 partes em cada recursão:
- Divisão: divide-se o problema em determinado número de subproblemas que são instâncias menores do problema original
- Conquista: resolve os subproblemas recursivamente, a não ser os subproblemas muito pequenos, que são resolvidos diretamente
- Combinação: combina-se as soluções dadas pelos subproblemas ao problema original
# Crescimento de funções
Apesar de poder calcular precisamente a eficiência de cada algoritmo, geralmente, como as entradas são muito grandes, só é necessário calcular a ordem de crescimento do algoritmo, ou seja, estudamos a eficiência assintótica. Em geral, um algoritmo assintoticamente eficiente será melhor para todas as entradas, exceto as muito pequenas.
## Notações Assintóticas
As funções que usamos para definir a análise assintótica estão no domínio dos naturais. A notação assintótica pode caracterizar qualquer aspecto do algoritmo, mas nesse caso será usada para determinar o tempo. Também vale ressaltar que podemos especificar a qual tempo que se refere a notação assintótica, pior caso por exemplo, mas essa notação também serve para caracterizar tempos de execução em geral, sem depender da entrada.

Assumimos que todas funções usadas nas notações são assintoticamente não negativas ($T(n)$ não negativo sempre que $n$ for suficientemente grande). Uma função assintoticamente positiva é uma função positiva para todo $n$ suficientemente grande
1. Theta ($\Theta$)
	
	$T(n) = \Theta (f(n))$ significa que $\Theta(f(n))$ = {$T(n)$: existem constantes positivas $c_{1}$, $c_{2}$ e $n_{0}$ tais que $0 \leq c_{1} f(n) \leq T(n) \leq c_{2} f(n)$ para todo $n \geq n_{0}$}. Ou seja, é preciso existirem constantes $c_{1}$ e $c_{2}$ tais que $T(n)$ fique entre $c_{1} f(n)$ e $c_{2} f(n)$, em outras palavras, ela estabelece limites superiores e inferiores à $T(n)$. Vale ressaltar que $T(n)$ é um subconjunto de $\Theta (f(n))$, ou seja, $T(n) \in \Theta (f(n))$, mas ao invés de representarmos com o $\in$ usamos o $=$, logo a notação fica $T(n) = \Theta (f(n))$.
	
	A definição de $\Theta (f(n))$ exige que todo membro de $T(n) \in \Theta (f(n))$ seja assintoticamente não negativo. Por consequência a própria $f(n)$ deve ser não negativa, se não o conjunto $\Theta (f(n))$ é vazio. Dizemos também que $f(n)$ é um limite assintoticamente restrito para $T(n)$.
	
	Para verificar se a "igualdade" $T(n) = \Theta (f(n))$ é verdadeira, temos que, a partir da desigualdade da definição, achar um valor qualquer/arbitrário, para $c_{1}$, $c_{2}$ e $n_{0}$ que satisfaça a desigualdade. O valor de $c_{1}$ e $c_{2}$ podem ser diferentes, mas devem se referir para o mesmo valor de $n_{0}$. Podem existir mais de um par de constantes que verificam a desigualdade, mas o importante é que exista pelo menos uma opção.
	 
	Qualquer polinômio $\displaystyle p(n) = \sum_{i = 0}^{d} a_{i} n^{i}$ onde $a_{i}$ são constantes e $a_{d} > 0$, temos $p(n) = \Theta (n^{d})$. Além disso, tendo em vista que qualquer constante é um polinômio de grau 0, podemos expressar qualquer função constante como $\Theta(n_{0})$ ou $\Theta (1)$, essa última é um abuso pois não mostramos qual variável está tendendo ao infinito. Porém usaremos ela com frequência para indicar uma constante ou uma função constante em relação a alguma variável.
2. Big-Oh ($O$)
	
	A notação $O$ estabelece um limite superior a função $T(n)$. Ela é lida como Big-Oh ou só O. Dizer $T(n) = O(f(n))$ significa que $O(f(n))$ = {$T(n)$: existem constantes positivas $c$ e $n_{0}$ tais que $0 \leq T(n) \leq c f(n)$ para todo $n \geq n_{0}$}.
	
	As notação $\Theta (n)$ contém $O(n)$ pois ela é uma noção mais forte. Logo, qualquer função quadrática que está em $\Theta (n^{2})$ também está em $O(n^{2})$. Além disso, qualquer função linear $an + b$ está em $O(n^{2})$, se tomarmos $c = a + |b|$ e $\displaystyle n_{0} = max \left(1, - \frac{b}{a} \right)$.
	
	Pode-se encontrar a notação $O$ sendo usada para descrever limites assintoticamente justos (o que definimos usando a notação $\Theta$), mas aqui usaremos ele para descrever o limite assintótico superior de $T(n)$, sem menção de precisão.
	
	Essa notação permite, muitas vezes, descrever o tempo de execução de um algoritmo apenas inspecionando a estrutura global do algoritmo. O uso da notação $O$ para descrever o limite de tempo para o pior caso, induz também um limite de tempo de execução para cada, e toda, entrada do algoritmo, diferente de outras notações, como o $\Theta$.
	
	Quando dizemos que o tempo de execução é $O(n^{2})$ estamos dizendo que existe uma função $T(n)$ que é $O(n^{2})$ tal que, para qualquer valor de n, não importando qual entrada específica de tamanho n seja escolhida, o tempo de execução para essa entrada tem um limite superior determinado pelo valor $T(n)$.