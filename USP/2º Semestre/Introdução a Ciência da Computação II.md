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
## Crescimento de funções
Apesar de poder calcular precisamente a eficiência de cada algoritmo, geralmente, como as entradas são muito grandes, só é necessário calcular a ordem de crescimento do algoritmo, ou seja, estudamos a eficiência assintótica. Em geral, um algoritmo assintoticamente eficiente será melhor para todas as entradas, exceto as muito pequenas.
### Notações Assintóticas
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
3. Ômega ($\Omega$)
	
	Essa notação fornece o limite assintótico inferior da função $T(n)$. Ela é lida como "ômega grande" ou "ômega" somente. Dizer que $T(n) = \Omega(f(n))$ significa que $\Omega(f(n))$ = {$T(n)$: existem constantes positivas $c$ e $n_{0}$ tais que $0 \leq c f(n) \leq  T(n)$ para todo $n \geq n_{0}$}.
	
	Essa notação significa que o tempo de execução para uma entrada qualquer, desde que $n$ seja suficientemente grande, é no mínimo uma constante vezes $f(n)$. Além disso, com essa notação damos um limite inferior para o melhor tempo de execução de um algoritmo.

Com isso, tiramos o seguinte teorema:  dizer que uma função $T(n) = \Theta(f(n))$, é válido se e somente se $T(n) = O(f(n))$ e $T(n) = \Omega(f(n))$.

É necessário mencionar agora a diferença entre os usos dos sinais. Quando a notação assintótica está sozinha, como em $n = O(n^{2})$, o igual significa pertinência. Já quando a notação assintótica aparece em uma fórmula, como $2n^{2} + 3 n + 1 = 2 n^{2} + \Theta(n)$ significa que ela representa alguma função anônima que não nos preocupamos em nomear.

4. Little-Oh ($o$)
	
	Ela é usada para expressar um limite superior que, diferente do big-oh, não é assintoticamente justo. Ela é chamada de "o pequeno". Dizer que $T(n) = o(f(n))$ significa que $o(f(n))$ = {$T(n)$: para qualquer constante positiva $c > 0$, existe uma constante $n_{0} > 0$ tal que $0 \leq T(n) < c f(n)$ para todo $n \geq n_{0}$}.
	
5. Ômega pequeno ($\omega$)
	
	A notação $\omega$ está para $\Omega$ assim como $o$ está para $O$. Logo, a notação $\omega$ fornece um limite inferior que não é assintoticamente justo/preciso. Definimos a notação como $\omega (f(n))$ = {$T(n)$: para qualquer constante positiva $c > 0$ existe uma constante $n_{0} > 0$ tal que $0 \leq c f(n) < T(n)$ para todo $n \geq n_{0}$}. Ela também pode ser definida como $T(n) \in \omega (f(n))$ se e somente se $f(n) \in o(T(n))$.
	
Muitas das propriedades de números reais se aplicam às notações, entre elas: transitividade, reflexividade, simetria e simetria de transposição. Mas vale ressaltar que dadas duas funções, nem sempre elas são comparáveis.
### Taxas de crescimento
#### Regras
Se $T_1 (n) = O(f(n))$ e $T_2 (n) = O(g(n))$:
- $T_1 (n) + T_2 (n) = max(O(f(n)), O(g(n)))$, ou seja, pegamos para o valor de O(n) a função cuja a taxa de crescimento é maior
- $T_1 \times T_2 = O(f(n) \times g(n))$ 
Se T(x) é um polinômio de grau n, então $T(x) = \Theta(x^n)$ 
Se $log_{k}n = O(n)$ para qualquer constante k, pois logaritmos crescem muito vagarosamente. 
#### Funções e taxas de crescimento
A tabela está em ordem de eficiência, no topo o mais eficiente (menor crescimento) para o menos eficiente.
![Tabela](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-22%2008-59-03.png)
![Gráfico](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-22%2009-01-08.png)
### Regras para o cálculo
#### Repetições
O tempo de execução de uma repetição é pelo menos o tempo dos comandos dentro da repetição (incluindo testes) vezes o número de vezes que é executada.
#### Repetições aninhadas
A análise é feito de dentro para fora. O tempo total de comandos dentro de um grupo de repetições aninhadas é o tempo de execução dos comandos multiplicado pelo produto do tamanho de todas as repetições.
#### Comandos consecutivos
É a soma dos tempos de cada um, o que pode significar o máximo entre eles.
#### Se, senão, então
Para a cláusula condicional, o tempo de execução nunca é maior do que o tempo do teste mais o tempo do maior entre os comandos relativos ao então e os comandos relativos ao senão.
#### Chamadas à sub-rotinas
Uma sub-rotina deve ser analisada primeiro e depois ter suas unidades de tempo incorporadas ao programa/sub-rotina que a chamou.

Já para sub-rotinas recursivas fazemos análise das recorrências.
## Divisão e Conquista
É um tipo de algoritmo, recursivo, que divide o problema em subproblemas, semelhantes ao original mas de menor tamanho, e ao resolver os subproblemas, retornam ele recursivamente, juntando os resultados, para assim resolver o problema original.

O método de divisão e conquista é divido em 3 partes em cada recursão:
- Divisão: divide-se o problema em determinado número de subproblemas que são instâncias menores do problema original
- Conquista: resolve os subproblemas recursivamente, a não ser os subproblemas muito pequenos, que são resolvidos diretamente
- Combinação: combina-se as soluções dadas pelos subproblemas ao problema original
### Recorrências
Uma recorrência é uma equação ou desigualdade que descreve uma função em termos de seu valor para entradas menores. Por exemplo: 
$$T(n) = \left\{ \begin{matrix} \Theta(1) \text{, se n =1} \\ 2T \left(\frac{n}{2} \right)+\Theta(n) \text{, se n > 1}\end{matrix} \right.$$

Veremos 3 métodos para resolver recorrências (obter limites assintóticos):
- Método da substituição: arriscamos um palpite para um limite e usamos indução matemática para provar que ele estava correto
- Método da árvore de recursão: convertemos a recorrência em uma árvore cujos nós representam os custos envolvidos nos níveis de recursão. Usamos técnicas para limitar somatórios para resolver a recorrência.
- Método mestre: nos dá limites para recorrências da forma $\displaystyle T(n) = aT \left(\frac{n}{b} \right) + f(n)$, onde $a \geq 1$, $b > 1$ e f(n) é uma função dada. Essa equação caracteriza um algoritmo de divisão e conquista que cria $a$ subproblemas, cada um com $\displaystyle \frac{1}{b}$ do tamanho original e no qual as etapas de divisão e conquista levam, juntas, o tempo de $f(n)$.
#### Método de substituição para resolver recorrências
Ele consiste em duas etapas:
1. Arriscar um palpite para a forma da solução
2. Usar indução para determinar as constantes e mostrar que a solução funciona.
Após tomar um palpite, testamos primeiro se ele é válido para o caso base. Se for, substituímos a função $T(n)$ pelo palpite na recorrência. Em seguida, usaremos a definição da notação para comparar o valor de $T(n)$ com a definição da notação e então tentaremos achar a constante. 
#### Método da árvore de recursão para resolver recorrências
Em uma árvore de recursão, cada nó representa o custo de um único subproblema em algum lugar no conjunto de invocações de função recursiva. Somamos os custos em cada nível da árvore para obter o custo por nível e depois somamos todos os custos para determinar o custo total de todos os níveis da recursão.

Geralmente usa-se a árvore de recursão para gerar um palpite e então confirmá-lo com o método da substituição. Se for cuidadoso ao montar a árvore, ela pode ser uma prova direta de uma solução para a recorrência.
#### Método mestre para resolver recorrências
Ele fornece uma receita para resolver recorrências no formato $\displaystyle T(n) = a T \left( \frac{n}{b} \right) + f(n)$, onde $a \geq 1$ e $b > 1$ são constantes e $f(n)$ é uma função assintoticamente positiva. Para usar esse método é preciso memorizar 3 casos, mas com eles poderá resolver diversas recorrências.

Da fórmula acima, temos que a recorrência divide o problema em $a$ subproblemas de tamanho $\displaystyle \frac{n}{b}$. Os $a$ subproblemas são resolvidos recursivamente no tempo $\displaystyle T \left( \frac{n}{b} \right)$. A função $f(n)$ abrange o custo de dividir o problema e combinar os resultados dos subproblemas.

Teorema: Seja $a \geq 1$ e $b > 1$, seja $f(n)$ uma função e seja $T(n)$ definida por $\displaystyle T(n) = a T \left( \frac{n}{b} \right) + f(n)$, então $T(n)$ pode ser limitado assintoticamente por:
-  Se $f(n) = O(n^{log_{b}a-x})$ para algum x > 0, então $T(n) = \Theta(n^{\log_ba})$
- Se $f(n) = \Theta(n^{\log_ba})$, então $T(n) = \Theta(n^{\log_ba}log{n})$ 
- Se $f(n) = \Omega(n^{\log_ba+x})$ para algum x > 0 e se $a\times f(\frac{n}{b}) \leq c \times f(n)$ para algum c < 1 e para todo n suficientemente grande, então $T(n) = \Theta(f(n))$

Além disso, é necessário mencionar que além da relação de maior e menor já estabelecidas, para a primeira e a última, é necessário que a função seja polinomialmente maior (tenha 1 grau a mais, maior por um fator n).
# Problemas de Ordenação
Ordenar é rearranjar elementos de um conjunto de modo a estabelecer uma relação de ordem entre eles (seja crescente ou decrescente), diz-se que os elementos $k_{1}, k_{2}, ..., k_{n}$ estarão dispostos de modo que $k_{1} \leq k_{2} \leq ... \leq k_{n}$. O principal objetivo da ordenação é facilitar a recuperação de itens do conjunto ordenado. Porém, às vezes da menos trabalho buscar um elemento em um conjunto desordenado do que em um ordenado. Basta então analisar se a busca é uma operação frequente, se for pode ser que valha a pena ordenar (isso só é feito uma vez), se não, pode ser que não valha.

Os algoritmos de ordenação trabalham sobre registros de um arquivo, e deles somente uma parte importa: a chave, o resto dos dados dos arquivos não interferem na ordenação. Além disso, um algoritmo de ordenação é estável se a ordem relativa dos itens com a mesma chave se mantém inalterada após a ordenação.

Também é necessária fazer uma diferenciação entre ordenação interna e externa. Dizemos que é uma ordenação interna se todos os registros cabem na memória principal (formam um único array). Já se o arquivo a ser ordenado não cabe na memória principal e por isso precisam ser armazenados em uma fita ou disco, chamamos de ordenação externa. Na ordenação interna os arquivos podem ser acessados imediatamente, já na ordenação externa eles são acessados sequencia