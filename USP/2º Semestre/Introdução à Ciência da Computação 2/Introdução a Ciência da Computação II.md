O livro de referência usado nesse estudo foi:
>Algoritmos Teoria e Prática Cormen, Thomas H.
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

Algumas fórmulas úteis são:
- Para uma soma de PA: $\displaystyle S_{n} = \frac{n(a_{1} + a_{n})}{2}$
- Para uma soma de PG: $\displaystyle S_{n} = \frac{a_{1}(q^{n}-1)}{q-1}$, onde $q$ é a razão
- Para uma soma infinita de PG: $\displaystyle S_{\infty} = \frac{a_{1}}{1-q}$, onde $q$ é a razão
#### Método mestre para resolver recorrências
Ele fornece uma receita para resolver recorrências no formato $\displaystyle T(n) = a T \left( \frac{n}{b} \right) + f(n)$, onde $a \geq 1$ e $b > 1$ são constantes e $f(n)$ é uma função assintoticamente positiva. Para usar esse método é preciso memorizar 3 casos, mas com eles poderá resolver diversas recorrências.

Da fórmula acima, temos que a recorrência divide o problema em $a$ subproblemas de tamanho $\displaystyle \frac{n}{b}$. Os $a$ subproblemas são resolvidos recursivamente no tempo $\displaystyle T \left( \frac{n}{b} \right)$. A função $f(n)$ abrange o custo de dividir o problema e combinar os resultados dos subproblemas.

Teorema: Seja $a \geq 1$ e $b > 1$, seja $f(n)$ uma função e seja $T(n)$ definida por $\displaystyle T(n) = a T \left( \frac{n}{b} \right) + f(n)$, então $T(n)$ pode ser limitado assintoticamente por:
-  Se $f(n) = O(n^{log_{b}a-x})$ para algum x > 0, então $T(n) = \Theta(n^{\log_ba})$
- Se $f(n) = \Theta(n^{\log_ba})$, então $T(n) = \Theta(n^{\log_ba}log{n})$ 
- Se $f(n) = \Omega(n^{\log_ba+x})$ para algum x > 0 e se $a\times f(\frac{n}{b}) \leq c \times f(n)$ para algum c < 1 e para todo n suficientemente grande, então $T(n) = \Theta(f(n))$

Além disso, é necessário mencionar que além da relação de maior e menor já estabelecidas, para a primeira e a última, é necessário que a função seja polinomialmente maior (tenha 1 grau a mais, maior por um fator n).
# Métodos de Ordenação
Ordenar é rearranjar elementos de um conjunto de modo a estabelecer uma relação de ordem entre eles (seja crescente ou decrescente), diz-se que os elementos $k_{1}, k_{2}, ..., k_{n}$ estarão dispostos de modo que $k_{1} \leq k_{2} \leq ... \leq k_{n}$. O principal objetivo da ordenação é facilitar a recuperação de itens do conjunto ordenado. Porém, às vezes da menos trabalho buscar um elemento em um conjunto desordenado do que em um ordenado. Basta então analisar se a busca é uma operação frequente, se for pode ser que valha a pena ordenar (isso só é feito uma vez), se não, pode ser que não valha.

Os algoritmos de ordenação trabalham sobre registros de um arquivo (eles que são trocados de posição), e deles somente uma parte importa: a chave, o resto dos dados dos arquivos não interferem na ordenação. Além disso, um algoritmo de ordenação é estável se a ordem relativa dos itens com a mesma chave se mantém inalterada após a ordenação.

Também é necessária fazer uma diferenciação entre ordenação interna e externa. Dizemos que é uma ordenação interna se todos os registros cabem na memória principal (formam um único array). Já se o arquivo a ser ordenado não cabe na memória principal e por isso precisam ser armazenados em uma fita ou disco, chamamos de ordenação externa. Na ordenação interna os arquivos podem ser acessados imediatamente, já na ordenação externa eles são acessados sequencialmente ou em grandes blocos.

Há também a ordenação por endereço, nela nós mantemos uma tabela de ponteiros para os registros e durante a ordenação os ponteiros que são alterados. Vale mencionar também que os registros a serem ordenados podem ser complexos ou não, mas os métodos de ordenação independem desse fator.

Existem vários métodos de implementar a ordenação. Dependendo do problema, um algoritmo pode ser mais vantajoso do que outro.
## Merge-Sort
O Merge-Sort é um algoritmo que segue a lógica de dividir-e-conquistar. Ele recursivamente divide o vetor de entrada em subvetores menores e ordena esses subvetores. Em seguida ele junta eles novamente para obter o vetor ordenado.

Ele basicamente divide o vetor ao meio até só ter 1 elemento em cada vetor, então ele ordena esses subvetores e junta eles novamente.

Algumas aplicações do merge-sort são:
- Ordenar longos datasets
- Ordenação Externa
- Contagem Inversa
- Ordenar linked lists
- Ele pode ser facilmente paralelizado já que podemos ordenar os subvetores independentemente e juntá-los
- Usar a função de juntar para resolver problemas do tipo "união e interseção de dois vetores ordenados"

O funcionamento do Merge-Sorte é:
1. Dividir o vetor recursivamente na metade até que não possa mais ser dividido (1 elemento em cada subvetor)
2. Cada subvetor é ordenado individualmente usando o algoritmo de juntar
3. Junta-se os subvetores ordenados formando um vetor ordenado. O processo continua até que todos os elementos dos subvetores tenham sido juntados

Análise de recorrência:

$T(n) = \left\{ \begin{matrix} O(1), & \text{se } n = 1 \\ 2T\left(\frac{n}{2}\right) + O(n), & \text{se } n > 1 \end{matrix} \right.$

Análise de complexidade:
- Melhor caso: $O(n \log{n})$, quando o vetor já está ordenado ou quase ordenado
- Caso médio: $O(n \log{n})$, quando o vetor está ordenado aleatoriamente
- Pior caso: $O(n \log{n})$, quando o vetor está ordenado na ordem inversa
- Espaço auxiliar: $O(n)$, o espaço adicional é preciso para o array temporário durante a junção.

As vantagens do merge-sort são:
- Ele é estável
- Ele performa bem com grandes entradas garantidamente
- Simples de implementar
- Naturalmente paralelizável

As desvantagens do merge-sort são:
- Complexidade de espaço, ou seja, ele requer memória adicional
- Mais lento que o quick-sort em geral
## Bubble-Sort
O bubble-sort é o algoritmo de ordenação mais simples. Ele consiste em repetidas trocas de elementos adjacentes caso estejam na ordem errada. Entretanto, ele não é recomendado para casos com grande quantidade de dados, visto que a complexidade dele para o pior tempo é muito alta (em um vetor de $n$ elementos ele precisa de $n-1$ iterações)

Nele, primeiro, começando da esquerda, comparamos os elementos adjacentes e os maiores são colocados a direita, desse jeito o maior elemento está no fim mais a direita. Esse processo então continua para o segundo maior e assim por diante.

Pode-se aprimorar o algoritmo, detectando quando o vetor já está ordenado. Isso ocorre quando em um determinado passo, nenhuma troca é realizada e também diminuindo o número de vezes que o vetor é percorrido, de modo que o vetor percorra $n-i$ iterações. O Bubble-Sort aprimorado tem complexidade de $O(n)$ para o melhor caso, complexidade de espaço de $O(n)$ e complexidade no pior caso de $O(n \log{n})$

O funcionamento dele é:
1. Imagina-se o seguinte vetor {6, 0, 4, 3}
2. O bubble-sort irá, começando da esquerda, comparar os elementos e colocá-los a direita quando forem maiores, até que o maior elemento esteja no final mais a direita do vetor. Exemplo: {6, 0, 3, 4} -> {0, 6, 4, 3} -> {0, 4, 6, 3} -> {0, 4, 3, 6}.
3. Agora que o maior elemento já está no lugar certo, iniciamos de novo da esquerda e repetimos o processo até que ele esteja no lugar certo e assim em diante até que ele esteja totalmente ordenado. Exemplo: {0, 4, 3, 6} -> {0, 3, 4, 6}.

O número total de passagens é $n - 1$ e o número total de comparações é $\displaystyle \frac{n \times (n-1)}{2}$.

Análise de complexidade:
- Complexidade de tempo: $O(n^{2})$
- Espaço auxiliar = $O(1)$

As vantagens do bubble-sort são:
- Ele é fácil de entender e implementar
- Não requer memória adicional
- É um algoritmo estável

As desvantagens do bubble-sort são:
- Tem uma complexidade de $O(n^{2})$ o que o torna lento para entradas grandes
- Ele faz o uso de um algoritmo de ordenação baseado em comparação, então ele usa um operador de comparação para determinar a ordem relativa dos dados de entrada, isso pode limitar a eficiência do algoritmo em alguns casos
## Quick-Sort
O Quick-Sort é um algoritmo de ordenação baseado na lógica de dividir-e-conquistar. Ele tem um tempo de execução no pior caso de $O(n^{2})$. Porém ele é a melhor opção prática para ordenação pois ele possui um tempo médio de execução de $O(n \, \log{n})$ e os fatores que ficam ocultos na representação anterior são pequenos. Vale ressaltar que o tempo de melhor caso é $O(n \log{n})$.

A lógica dele é: primeiro escolhe-se um elemento do vetor que será o pivô (pivot) e, a partir dele, dividirá o vetor. Essa divisão ocorre através da inserção do pivot na sua posição correta. Os vetores obtidos serão ordenados independentemente e combinados para produzir o resultado final.

O processo do Quick-Sort é:
1. Escolher um pivot
2. Particionar o arranjo $A[p ... r]$ ao redor do pivô ($A[q]$) em dois subarranjos $A[p ... q-1]$ e $A[q+1 ... r]$. De modo que os elementos em $A[p ... q-1]$ são menores ou iguais a $A[q]$ e que os elementos em $A[q+1 ... r]$ são maiores ou iguais a $A[q]$ (Divisão)
3. Ordenar os dois subarranjos $A[p ... q-1]$ e $A[q+1 ... r]$ por chamadas recursivas a quicksort. Para-se a recursão quando os vetores possuem somente 1 elemento (Conquista)
4. Como os subarranjos já estão ordenados, não é necessário nenhum trabalho para combiná-los: o arranjo $A[p ... r]$ está ordenado

Para escolher o pivô há algumas opções:
- Sempre pegar ou o primeiro ou o último elemento. O problema desse método é que sempre terá o pior caso quando o vetor já estiver ordenado
- Pegar um elemento aleatório como pivô. Esse método é bom pois ele não tem um padrão para o pior caso acontecer
- Pegar a mediana como pivô. Esse é o melhor método em termos de complexidade do algoritmo, pois pode-se achar a mediana num tempo linear e a partição sempre dividirá o vetor na metade. Porém ele tem a desvantagem de que achar a mediana tem altas constantes, então ele se torna baixo na média.

O processo da partição é a chave do Quick-sort. Há três algoritmos comuns para esse processo e todos tem complexidade de tempo $O(n)$:
- Partição "ingênua" (naive): cria-se uma cópia do vetor. Primeiro coloca-se todos os menores elementos e depois os maiores, em seguida atribui a cópia ao vetor original. Isso requer $O(n)$ de espaço a mais
- Partição de Lomuto: é um simples algoritmo que acompanha os índices dos menores elementos e mantém trocando
- Partição de Hoare: é a mais rápida de todas. Nesse algoritmo, atravessa-se o vetor dos dois lados e fica trocando o maior elemento da esquerda com o menor da direita enquanto o vetor não foi particionado

O funcionamento dele é:
- Considera-se o vetor $\{10, 80, 30, 90, 40\}$, o último elemento como pivô e a partição de Lomuto
- Primeiramente é comparado 10 com o pivô. Como ele é menor que o pivô, troca-se ele com ele mesmo.
- Em seguida compara-se 80 com o pivô. Como ele maior do que o pivô, não há troca e move-se para o próximo elemento
- Compara-se 30 com o pivô. Como é menor que ele, troca-se ele de lugar com o 80.
- Compara-se 90 com o pivô. Como é maior que ele, não há troca e termina-se a travessia.
- Em seguida coloca-se o pivô no lugar certo. A partição fica colocando o pivô no posição correta em relação ao vetor ordenado esperado. Essa repetição ordena o vetor.
- Agora com o pivô no lugar correto, divide-se o vetor em dois subarranjos.
- Repete o processo para os subarranjos.

### Análise de complexidade
Melhor caso: $\Omega (n \log{n})$
- O melhor caso para o quick-sort ocorre quando o pivô escolhido divide os vetores de cada passo praticamente na metade. Nesse caso o algoritmo vai fazer partições balanceadas, o que leva a uma ordenação eficiente
- O vetor de tamanho $n$ é dividido $m$ vezes, logo $m \approx \log_{2}{n}$
- Cada parte do vetor realiza $n$ comparações
	- Assim, $T(n) = 2 T(\frac{n}{2}) + n$
- Pelo método da árvore de recorrência, tem-se que $T(n) = O(n \log_{2}{n})$

Caso médio: $\Theta (n \log{n})$
- O caso médio do quick-sort performa bem na prática, fazendo dele um dos algoritmos de ordenação mais rápidos
- $T(n) \approx 1,386 n \log_{2}{n} - 0,846n = O(n \log_{2}{n})$ 

Pior caso: 
- Se o vetor já for ordenado e escolher o pivô como um dos extremos
- Se o pivô é o maior ou menor elemento
	- O que leva a subvetores desiguais, com $n$ chamadas recursivas da função partição, eliminando-se 1 elemento a cada chamada\
	- $T(n) = T(n-1) + O(n)$
		- $T(n) = \frac{1}{2} n(n+1) \longrightarrow T(n) = O(n^{2})$  
	- Árvore de recursão:
		- Nível 1: $O(n)$
		- Nível 2: $O(n-1)$
		- etc

Esse algoritmo é um dos mais rápidos para uma variedade de situações, sendo provavelmente mais utilizado do que qualquer outro algoritmo.

Para evitar o pior caso pode-se tanto escolher 3 elementos quaisquer do vetor e usar a mediana deles como pivô quanto escolher aleatoriamente o pivô.

As vantagens do Quick-Sort são:
- É um algoritmo de divisão-e-conquista o que o torna fácil para resolver problemas
- É eficiente para grandes quantidades de dados
- Requer uma pequena quantidade de memória para funcionar (baixo overhead)
- É cache friendly pois ele trabalha no mesmo array e não copia os dados para um array auxiliar
- É o algoritmo com propósito geral mais rápido para grandes quantidades de dados quando estabilidade não é necessária
- Ele tem recursividade de cauda, então todas as otimizações de recursividade de cauda podem ser aplicadas

As desvantagens do Quick-Sort são:
- Ele tem uma complexidade de tempo no pior caso de $O(n^{2})$, que ocorre quando o pivô é mal escolhido
- Não é uma boa escolha para sets de dados pequenos
- Não é um algoritmo estável, ou seja, dois elementos com a mesma chave não terão a sua ordem preservada na saída, pois trocamos elementos de acordo com a posição do pivô e não com relação a posição original
## Ordenação por inserção
Os algoritmos de ordenação por inserção consistem em inserir um dado elemento em sua posição correta em um subconjunto já ordenado.
### Inserção simples
Também chamado de inserção direta, é um algoritmo de ordenação simples que iterativamente insere cada elemento de um conjunto não ordenado na posição correta dele em uma porção ordenada da lista. Ele é um algoritmo estável. A complexidade de tempo dele é $O(n^{2})$ e a quantidade de espaço auxiliar é $O(1)$.

A lógica dele é construir um array ordenado, elemento por elemento. Ele é considerado um algoritmo de ordenação interna.

O funcionamento dele é:
1. Começa com o segundo elemento do array como o primeiro elemento do vetor ordenado (o primeiro elemento do array já pertence ao vetor ordenado)
2. Compara o segundo elemento com o primeiro elemento e checa se o segundo elemento é menor e então troca eles
3. Move-se para o terceiro elemento e compara com o segundo elemento e depois com o primeiro e então troca ele conforme o necessário para colocá-lo na posição correta
4. Continue o processo, comparando com os elementos anteriores até o array estar ordenado

Análise de complexidade:
- Melhor caso: $O(n)$, se a lista já está ordenada, onde $n$ é o número de elementos na lista
- Caso médio: $O(n^{2})$, se a lista é ordenada aleatoriamente
- Pior caso: $O(n^{2})$, se a lista está na ordem contrária
- Complexidade de espaço: $O(n)$

Inserção simples é eficiente em arquivos "quase ordenados" e um dos métodos mais intuitivos.

As vantagens da inserção simples são:
- Simples e fácil de implementar
- Algoritmo de ordenação estável
- Eficiente para listas pequenas e listas quase ordenadas
- Espacialmente eficiente
- O número de inversões é diretamente proporcional ao número de trocas

As desvantagens da inserção simples são:
- Ineficiente para listas longas
- Não tão eficiente como outros algoritmos de ordenação para a maioria dos casos

### Shell-Sort
O Shell-Sort é uma variação da inserção simples. Enquanto a inserção simples compara elementos adjacentes e move uma posição a frente, a Shell-Sort permite a troca de elementos distantes. 

Elementos separados por h posições são ordenados de tal forma que todo h-ésimo elemento está em uma sequência ordenada. Essa sequência é dita estar h-ordenada.

A ideia básica é dividir a entrada em sub-conjuntos de elementos de distância h e aplicar a inserção simples a cada um, sendo que h é reduzido sucessivamente. A cada iteração o vetor está mais ordenado.

O funcionamento do Shell-Sort é:
1. Inicializa o valor do intervalo, por exemplo h
2. Divide-se a lista em pequenas subpartes, cada uma deve ter intervalos igual para h
3. Ordena-se essas sublistas usando inserção simples
4. Repita o processo 2 até a lista estar ordenada

Os índices h são os incrementos que são adicionados a cada posição do vetor para se ter o próximo elemento do sub-conjunto. A cada iteração h decresce, daí o nome "incrementos decrescentes" do método. O último incremento deve sempre ser 1.

Análise de complexidade:
- Foi demonstrado que, com uma sequência adequada de incrementos de h, shell-sort é aproximadamente $O(n(\log{n})^{2})$.
- Além disso, Knuth (1973) sugere que com uma função recursiva, tal que $h(1) = 1$ e $h(i+1) = 3 \times h(i) + 1$, tem-se uma complexidade de $O(n^{\frac{3}{2}})$
- De acordo com o site geek for geeks:
	- Pior caso $O(n^{2})$
	- Melhor caso $\Omega(n \log{n})$: quando o array já é ordenado, o número total de comparações é igual ao tamanho dado do array
	- Caso médio $O(n \log{n}) \approx O(n^{1,25})$
	- Complexidade de espaço: $O(1)$

## Ordenação por Seleção
Nesses algoritmos, os elementos são selecionados e dispostos em suas posições corretas finais.
### Seleção Direta
Também chamado de seleção simples ou classificação de deslocamento descendente, esse algoritmo de ordenação é simples e eficiente.

A ideia dele é selecionar repetidamente o menor (ou maior) elemento da porção não ordenada da lista e movê-lo para a parte ordenada da lista (trocá-lo com o primeiro elemento da parte não ordenada). Esse processo é repetido para o resto da parte não ordenada até que a lista toda esteja ordenada.

O funcionamento da Seleção direta é:
1. Selecionar o elemento que apresenta o menor valor
2. Trocar o elemento de lugar com o primeiro elemento da sequência, $x[0]$
3. Repetir as operações 1 e 2, envolvendo agora apenas os $n-1$ elementos restantes, depois os $n-2$ elementos, e assim em diante, até restar somente um elemento, o maior deles (ou se começar com o maior, irá restar o menor)

No i-ésimo passo, o elemento com o menor valor entre $x[i], ..., x[n-1]$ é selecionado e trocado com $x[i]$. Como resultado, após $i$ passos, os elementos $x[0], ..., x[i-1]$ estão ordenados.

Não existe melhora se a entrada está completamente ordenada ou desordenada. Esse algoritmo exige também pouco espaço. Ele é útil quando n é pequeno.

Análise de complexidade:
- A complexidade de tempo é $O(n^{2})$, pois tem dois loops aninhados:
	- Um loop para selecionar o elemento do vetor, um por um: $O(n)$
	- Outro loop para comparar esse elemento com todos os outros elementos do array: $O(n)$
	- Logo, a complexidade temporal é $O(n) \times O(n) = O(n \times n) = O(n^{2})$
- Complexidade de espaço auxiliar é $O(1)$ dado que a única memória extra usada é para variáveis temporais enquanto troca dois valores do vetor. A seleção direta nunca faz mais que $O(n)$ trocas e pode ser útil quando escrever na memória é custoso

As vantagens da seleção direta são:
- Simples e fácil de entender
- Trabalha bem com pequenos data sets

As desvantagens da seleção direta são:
- Tem uma complexidade de tempo de $O(n^{2})$ no pior cenário e no caso médio
- Não trabalha bem com grandes data sets
- Não é estável, ou seja, não preserva a ordem relativa entre itens com as mesmas chaves
### Heap-Sort
O Heap-Sort é uma técnica de ordenação baseada em comparação que utiliza a estrutura de dados heap como base. Ela pode ser vista como uma otimização da seleção simples. No Heap sort usamos a estrutura heap binária para poder rapidamente achar e mover o elemento máximo em $O(\log{n})$ ao invés de $O(n)$ e então atingir a complexidade de tempo de $O(n \log{n})$. Vale mencionar que ao dizer heap, não está sendo referido o espaço de armazenamento de variáveis dinâmicas, mas sim a estrutura de dados.

Um heap é uma estrutura de dados em que há uma ordenação entre elementos. Ele pode ser representado por uma árvore binária. Ele observa conceitos de ordem e de forma:
- Ordem: o item de qualquer nó deve satisfazer uma relação de ordem com os itens dos nós filhos.
	- Heap máximo (ou descendente): pai $\geq$ filhos, sendo que a raiz é o maior elemento (propriedade de heap máximo)
	- Heap mínimo (ou heap ascendente): pai $\leq$ filhos, sendo que a raiz é o menor elemento (propriedade de heap mínimo)
- Forma: a árvore binária do heap deve estar completa até pelo menos seu penúltimo nível e, se o seu último nível não estiver completo, todos os nós do último nível deverão estar agrupados à esquerda

Um heap pode ser representado por um vetor. Seguindo a ordem de indexação de cima para baixo e da esquerda para direita, além de indexar por nível (linha).

Para acessar os elementos (pais e filhos) de cada nó usamos as seguintes expressões:
- Filho esquerdo do nó k: $2k + 1$
- Filho direito do nó k: $2k+2$
- Pai do nó k: $\frac{k-1}{2}$

Assume-se algumas propriedades também:
- A raíz sempre está na posição $0$ do vetor
- O comprimento(vetor) indica o número de elementos do vetor
- O tamanho_do_heap(vetor) indica o número de elementos no heap armazenado dentro do vetor. Ou seja, embora $A[0, ..., comprimento(A)-1]$ contenha números válidos, nenhum elemento além de $A[tamanho\_do\_heap(A) - 1]$ é um elemento do heap, sendo que $tamanho\_do\_heap(A) \leq comprimento(A)$. 

O funcionamento do heap-sort é:
1. Construir um heap máximo
2. Trocar a raíz, o maior elemento, com o elemento da última posição do vetor
3. Remova o último elemento, que agora já está na posição correta
4. Diminuir o tamanho da heap em 1
5. Rearranjar o heap máximo (agora menor), se necessário
6. Repetir o processo $n-1$ vezes

O processo continua até todos os elementos terem sido incluídos no vetor de forma ordenada. É necessário:
- Saber construir um heap a partir de um vetor qualquer (procedimento construir_heap)
- Saber rearranjar o heap e manter a propriedade de heap máximo (procedimento rearranjar_heap)

O procedimento de rearranjar_heap faz a manutenção da propriedade de heap máximo. Recebe como entrada um vetor A e um índice i. Assume que as árvores binárias com raízes nos filhos esquerdo e direito de i são heap máximos mas que a $A[i]$ pode ser menor que seus filhos, violando a propriedade de heap máximo. A função do procedimento rearranjar_heap é deixar $A[i]$ escorregar para a posição correta, de tal forma que a subárvore com raiz em i torne-se um heap máximo.

Lembre-se que as folhas da heap (elementos da última linha) começam na posição $\frac{n}{2}$.

A complexidade do procedimento construir_heap, considerando uma árvore binária de n elementos é:
- O nível mais baixo tem aproximadamente $\frac{n}{2}$ nós e não precisam ser analisados
- O próximo nível tem aproximadamente $\frac{n}{4}$ nós e cada um pode exigir até 1 reorganização
- O nível acima tem aproximadamente $\frac{n}{8}$ nós e cada um pode exigir até 2 reorganizações
- Altura da árvore: $\log_{2}{n}$
- Somando os custos de cada nível:
$$custo\_total = \frac{n}{2} \times 0 + \frac{n}{4} \times 1 + \frac{n}{8} \times 2 + ... + 1 \times \log_{2}{n}$$

$$custo\_total = n \times \sum_{i = 0}^{log_{2}{n-1}} \frac{i}{2^{i+1}}$$

$$custo\_total = \frac{n}{2} \sum_{i = 0}^{\log_{2}{n-1}} \frac{i}{2^{i}}$$
- Soma geométrica ponderada: $\displaystyle \sum_{i = 0}^{\infty} i \times x^{i} = \frac{x}{(1-x)^{2}}$. Portanto:
$$custo\_total = \frac{n}{2} \sum_{i = 0}^{\infty} i \times \left( \frac{1}{2} \right)^{i} = \frac{n}{2} \times \frac{\frac{1}{2}}{\left( 1 - \frac{1}{2} \right)^{2}} = O(n)$$

O custo do heap-sort é $O(n \log{n})$, sendo eficiente mesmo quando o vetor já está ordenado. 

Análise de complexidade do Heap-Sort:
- Complexidade de tempo é $O(n \log{n})$
- Espaço auxiliar: $O(\log{n})$ devido a chamada recursiva, porém o espaço auxiliar pode ser $O(1)$ para uma implementação iterativa

Considerações:
- O heap-sort é útil para arquivos com muitos registros (complexidade do anel interno do algoritmo)
- É um algoritmo de ordenação interna
- A implementação típica dele não é estável, mas pode ser feita estável
- Quick-sort é cerca de 2x mais rápido (anel interno é mais simples)
- Heap-sort é melhor que o shell-sort para grandes arquivos
- Comportamento $O(n \log{n})$, qualquer que seja a entrada

As vantagens do Heap-Sort são:
- Complexidade de tempo eficiente: tem a complexidade de $O(n \log{n})$ para todos os casos. Isso o faz eficiente para ordenar grandes data sets. O fator $\log{n}$ vem da altura da árvore binária e garante que o algoritmo mantenha uma boa performance mesmo com uma grande quantidade de elementos
- Uso de memória: o uso de memória pode ser mínimo (se usar uma implementação iterativa, no lugar de uma recursiva). Então a parte do que é necessário para segurar a lista initial de itens a serem ordenados, ele não precisa de memória adicional para trabalhar
- Simplicidade: é mais simples de entender do que outro algoritmo de ordenação igualmente eficiente, porque ele não usa conceitos de computação avançada como recursão

As desvantagens do Heap-Sort são:
- Custoso: ele é custoso conforme as constantes são maiores, quando comparado ao merge-sort mesmo se o tempo de complexidade é $O(n \log{n})$ para os dois
- Instável: heap-sort não é estável
- Ineficiente: é pouco eficiente devido às altas constantes na complexidade de tempo
## Ordenação por contagem de menores
A ideia básica desse método é sabendo quantos são os elementos menores que um determinado valor, saberemos a posição que o mesmo deve ocupar no arranjo ordenado. Por exemplo, se há 5 valores menores que o elemento 7, sabemos que o elemento 7 será inserido na sexta posição do arranjo.

Esse método requer um arranjo auxiliar para manter a contagem de menores e um outro para montar o arranjo ordenado.

Complexidade:
- Complexidade de tempo: $O(n^2)$, pois é necessário percorrer o vetor 2 vezes.
- Complexidade de espaço: $O(3n)$

Vantagens:
- Estável*

Desvantagens:
- Necessita de 2 vetores adicionais
## Ordenação por Contagem de Tipos
Também chamado de Counting-Sort, a idea básica desse método é contar o número de vezes que cada elemento ocorre no arranjo, se há k elementos antes dele, ele será inserido na posição k+1 do arranjo ordenado. Esse método tem uma restrição: os elementos devem estar contido em um intervalo [min, max] do conjunto de números inteiros positivos.

Esse método requer um arranjo auxiliar para manter a contagem de tipos e de um outro para montar o arranjo ordenado.

Complexidade:
- Complexidade de tempo: $O(n)$, se max $\leq$ n, pois não é por comparação
- Complexidade de espaço: $O(3n)$

Vantagens:
- Ele é mais rápido que todos os algoritmos de ordenação baseados em comparação, se o intervalo de números da entrada é da ordem do número da entrada
- Estável

Desvantagens:
- Não funciona com valores decimais
- É ineficiente se o intervalo de números for muito grande
- Não é um método de ordenação interno.

Aplicações:
- É usado para casos que temos um intervalo limitado de itens
- É uma subrotina do radix sort
- A ideia de contagem é usado no bucket sort para dividir os elementos em diferentes buckets
## Radix-Sort
Também chamado de ordenação de raízes, a ideia de método é ordenar os números através dos seus dígitos, dos menos significativos aos mais significativos. Por exemplo, ordenar os números 236 e 235 implica em comparar os últimos dígitos e se não bastar, comparam-se os do meio e assim em diante até comparar os mais significativos. 

Para construir esse algoritmo, usam-se [[Algoritmos  e Estruturas de Dados I|filas]], uma fila para cada dígito (0, 1, 2, ..., 9). Nelas, os números vão sendo inseridos na fila de acordo com o dígito avaliado e a cada iteração, os números estão mais próximos da ordenação final.

Para os números do arranjo terem a mesma quantidade de dígitos, pode-se completar com 0 à esquerda do dígito mais significativo.

Para ordenar um arranjo cujo o maior número tem $m$ dígitos, são necessárias $m$ iterações no máximo.

Complexidade:
- Complexidade de tempo: $O(m \times n)$, se $m$ for pequeno então é $O(n)$ (m é o número de dígitos do maior número*)
- Complexidade de espaço: Além do vetor, deve-se contar os espaços para as filas

Vantagens:
- Tem uma complexidade de tempo linear, o que o torna mais rápido que algoritmos a base de comparações
- É estável
- É eficiente para grandes números inteiros ou de strings
- Pode ser facilmente paralelizado

Desvantagens:
- Não é eficiente para decimais (floats) ou outros tipos dedados que não podem ser mapeados para um pequeno número de dígitos
- Requer uma quantidade considerável de memória para armazenar a contagem de número de vezes que cada valor aparece
- Não é eficiente para base dados pequenos e com um pequeno número de chaves únicas
- Ele precisa que o dado ordenado possa ser representado em um número fixo de dígitos
## Comparação entre os algoritmos de ordenação
Considerando uma ordem aleatória dos elementos, foi dado 1 ao mais rápido e o restante é calculado a partir disso:
![[Pasted image 20241110154007.png]]
Considerando uma ordem ascendente (já ordenado):
![[Pasted image 20241110154144.png]]
Considerando uma ordem descendente dos elementos (do maior para o menor):
![[Pasted image 20241110154222.png]]
Agora fazendo uma análise desses dados, sabemos que:
- O quick-sort é o mais rápido para todos os arranjos com elementos aleatórios
- O heap-sort e o quick-sort tem uma diferença constante, sendo o heap-sort mais lento
- Apenas para arranjos grandes e com elementos aleatórios que o heap-sort é melhor do que o shell-sort
- O método da inserção direta é mais rápido para arranjos ordenados
- O método da inserção direta é melhor que o método da seleção direta para arranjos aleatórios
- O shell-sort e o quick-sort são sensíveis em relação às ordenações ascendentes e descendentes

Inserção direta:
- Interessante para arquivos com menos de 20 elementos (pode ser mais eficiente do que algoritmos com menor comportamento assintótico)
- Método estável
- Melhor que o bubble-sort
- Arranjo já ordenado: $O(n)0$

Seleção:
- Somente é vantajoso quanto ao número de movimentos de registros: $O(n)$
- Pode ser usado para arquivos com registros grandes, desde que o tamanho não exceda 1000 elementos

Shell-sort:
- Eficiente para arquivos de tamanho moderado
- Mesmo para arquivos grandes, é apenas 2 vezes mais lento que o quick-sort
- Não possui pior caso
- Trabalha menos com arquivos parcialmente ordenados

Heap-Sort:
- Anel interno é complexo, tornando-o cerca de 2x mais lento que o quick-sort
- Não necessita de memória adicional
- Executa sempre em $O(n\log{n})$

 Merge-sort:
 - Também executa sempre em $O(n \log{n})$
 - Precisa de memória adicional
 - Tanto ele quanto o heap-sort são úteis para aplicações que não podem tolerar variações no tempo esperado para ordenação

Quick-sort:
- Algoritmo mais eficiente que existe para uma grande variedade de situações
- Método frágil para erros simples de implementação
- Recursividade exige um pouco de memória adicional
- No pior caso, seu comportamento é de ordem quadrática (necessário cuidado para escolha do pivô)

Uma boa estratégia é:
- Usar quick-sort com a mediana de três elementos para a escolha do pivô
- Usar ordenação simples (ex: inserção) para subvetores com poucos registros (menos de 25 elementos) (o que vai reduzir o número de chamadas recursivas)
## Cota inferior para Ordenação
A cota ou limite inferior do problema é o tempo máximo em que um algoritmo considerado ótimo resolve o problema. Sabemos que é impossível resolver o problema em menos que $C(n)$ passos para uma entrada de tamanho $n$, então o algoritmo ótimo será aquele que resolve o problema em tempo igual à cota inferior. 

Por exemplo, considerando a ordenação por comparação, pode-se achar a cota inferior por meio de uma árvore de decisão para representar o problema:
![[Pasted image 20241110160048.png]]Dada a árvore, vemos, no mínimo, existem nessa árvore, assumindo um arranjo de tamanho $n$, $n!$ folhas. Para ordenar $n$ elementos, precisa-se de um número de comparações equivalente à altura máxima da árvore de decisão, aproximadamente. Ou seja, disso tudo temos:
- Número máximo de folhas em uma árvore binária de altura h: $2^{h}$
- Número de folhas de uma árvore de decisão para ordenação por comparação: $n!$

Portanto:
- $2^{h} \geq n! \longrightarrow h \geq \log{(n!)}$, usando a aproximação de Stirling, obtém-se $\log{(n!)} = O(n \log{n})$
- Então, tem-se: $h = \Omega(n \log{n})$ 

O resultado da conclusão anterior é que métodos de ordenação por comparação de elementos não podem ser melhores do que $O(n \log{n})$.
# Métodos de Busca
É importante estudar busca pois ela é uma tarefa muito comum. Tanto que vários métodos e estruturas de dados podem ser empregados para se fazer busca. Certos métodos de organização/ordenação de dados podem tornar o processo de busca mais eficiente.

O problema da busca (ou pesquisa) é que dado um conjunto de elementos, onde cada um é identificado por uma chave, o objetivo da busca é localizar, nesse conjunto, o elemento que corresponde a uma chave específica.
## Termos relacionados
Alguns termos importante de saber para iniciar os estudos sobre busca são:
- Tabela: termo genérico, pode ser qualquer estrutura de dados usada para armazenamento interno e organização dos dados
- Registros: conjunto de elementos que formam a tabela
- Chave: ela é associada a cada registro e é usada para diferenciar os registros entre si. Existem alguns tipos de chave:
	- Chave interna: a chave está contida dentro do registro, em uma localização específica
	- Chave externa: a chave está contida em uma tabela de chaves separada que inclui ponteiros para os registros
	- Chave primária: para todo arquivo existe pelo menos um conjunto exclusivo de chaves (dois registros não podem  ter o mesmo valor de chave)
	- Chave secundária: são as chaves não primárias (chaves que não precisam ter seus valores exclusivos)
- Algoritmo de busca: é o algoritmo que aceita um argumento $a$ e tenta encontrar o registro cuja chave seja $a$
- Operações na tabela:
	- Inserção: adiciona um novo elemento à tabela
	- Algoritmo de busca e inserção: se não encontra o registro, insere um novo
	- Remoção: retirar um elemento da tabela
	- Recuperação: procurar um elemento na tabela e, se achá-lo, torná-lo disponível
## Tipos de Busca
A tabela pode ser:
- Um vetor de registros
- Uma lista encadeada
- Uma árvore
- Entre outros

A tabela pode ficar:
- Totalmente na memória (busca interna)
- Totalmente no armazenamento auxiliar (busca externa)
- Dividida entre ambos

Algumas técnicas de busca em memória interna são:
- Busca sequencial
- Busca binária
- Busca por interpolação
- Busca em árvores
- Hashing

O objetivo é encontrar um dado registro com o menor custo, por isso, ressalta-se que cada técnica tem vantagens e desvantagens.
## Busca Sequencial
A busca sequencial é a forma mais simples de busca. Ela é aplicável a uma tabela organizada como um vetor ou como uma lista encadeada.

A idea dela é percorrer registro por registro em busca da chave.

Uma maneira de tornar o algoritmo mais eficiente é usando um sentinela. Esse sentinela é adicionado no final da tabela e tem o mesmo valor da chave. Ele garante que o elemento sempre será encontrado, o que elimina um teste, melhorando a performance do algoritmo. Vale ressaltar que para usar o sentinela, é necessário que o arranjo seja declarado com uma posição a mais.

O método acima é usado para implementações com vetores. Esse tipo de implementação tem como limitação o tamanho fixo do vetor, o que resulta ou em desperdício ou em falta de espaço. Uma alternativa para essa implementação é através do uso de uma lista encadeada.

Complexidade:
- Se o registro for o primeiro: 1 comparação
- Se o registro for o último: N comparações
- Se for igualmente provável que o argumento apareça em qualquer posição da tabela, em média: $\displaystyle \frac{(n+1)}{2}$ comparações
- Se a busca for mal sucedida: N comparações
- Logo, no pior caso é $O(n)$
### Arranjo não ordenado
É um tipo de busca sequencial em que os registros não estão ordenados. Nesse tipo de arranjo, a inserção é feita no final do arranjo. Já a remoção possui dois casos:
- Se for vetor: é necessário realocar os registros acima do registro removido
- Se for lista encadeada: é necessário atualizar ponteiros

Para aumentar a eficiência desse tipo de busca, pode-se reordenar continuamente a tabela de modo que os registros mais acessados sejam deslocados para o início. Para isso, há duas formas de fazer:
- Método mover-para-frente: sempre que uma pesquisa obtiver êxito, o registro recuperado é colocado no início da lista
	- Vantagens: Possui resultados melhores para quantidades pequenas e médias
	- Desvantagens: uma única recuperação não implica que o registro será frequentemente recuperado, o que gera uma perda de eficiência para os outros registros
- Método da transposição: um registro recuperado com sucesso é trocado com o registro imediatamente anterior

Ambos os métodos se baseiam no fenômeno da recuperação recorrente de registros.
### Tabela Ordenada
É um tipo de busca sequencial em que os registros estão ordenados. Esse tipo de busca é interessante pois a eficiência da operação de busca melhora se as chaves dos registros estão ordenadas. 

No pior caso (caso em que a chave não é encontrada), são necessárias N comparações. Já no caso médio, são necessárias $\displaystyle \frac{N}{2}$ comparações se as chaves estiverem ordenadas, pois a busca é interrompida assim que uma chave maior do que a procurada é encontrada.
### Busca Sequencial Indexada
É um tipo de busca sequencial que usa uma tabela auxiliar chamada de tabela de índices, além do próprio arquivo ordenado.

Cada elemento na tabela de índices contém uma chave (kindex) e um indicador do registro no arquivo que corresponde a kindex. Faz-se a busca a partir do ponto indicado na tabela, sendo que a busca não precisa ser feita desde o começo.

Ela pode ser implementada como um vetor ou como uma lista encadeada. O indicador da posição na tabela pode ser um ponteiro ou uma variável inteira.

Se a tabela for muito grande, pode-se ainda usar a tabela de índices secundária. O índice secundário é um índice para o índice primário.

Vantagens:
- Os itens na tabela poderão ser examinados sequencialmente sem que todos os registros precisem ser acessados.
- Com isso, o tempo de busca diminui consideravelmente

Desvantagens:
- A tabela tem que estar ordenada
- Exige espaço adicional para armazenar a(s) tabela(s) de índices
- É preciso ter cuidado com a inserção e remoção
	- Remoção tem duas opções:
		- Remove-se o elemento e rearranja-se a tabela inteira e o(s) índice(s)
		- Marca-se a posição do elemento removido, indicando que ela pode ser ocupada por um outro elemento futuramente (a tabela pode ficar vazia)
	- Inserção:
		- Se houver espaço vago na tabela, rearranjam-se os elementos localmente
		- Se não houver espaço vago, rearranja-se a tabela a partir do ponto apropriado e reconstrói o(s) índice(s)

Como montar o índice primário:
1. Se a tabela não estiver ordenada, ordene-a
2. Divide-se o número de elementos da tabela pelo tamanho do índice desejado: $\displaystyle \frac{n}{tamanho \, do \, índice}$
3. Para montar o índice, recuperam-se os elementos $\displaystyle 0, \, \frac{0 + n}{tamanho \, do \, índice}, \, \frac{0 + 2 \times n}{tamanho \, do \, índice}, ...$
4. Cada elemento do índice representa $\displaystyle \frac{n}{tamanho \, do \, índice}$ elementos da tabela

Para montar um índice secundário aplica-se um raciocínio similar sobre o índice primário. Em geral, não são necessários mais que 2 índices.
## Busca Binária
É um método de busca recursivo com base no método de dividir-e-conquistar,  que requer que os dados estejam ordenados em no arranjo, seja em ordem crescente ou decrescente. Se for em ordem crescente, tem-se $A[i]  <= A[i + 1]$, já se for em ordem decrescente tem-se $A[i] >= A[i+1]$.

A ideia desse método é comparar a chave com o elemento do meio do arranjo. Se for igual, a busca é bem-sucedida e retorna o elemento. Se for menor, acessa-se recursivamente a metade inferior do arranjo e verifica se o elemento dele do meio é a chave e assim por diante. Já se for maior, acessa-se recursivamente a metade superior do arranjo e verifica se o elemento dele do meio é a chave e assim por diante.

Complexidade:
- A complexidade é de $O(\log{n})$, pois cada comparação reduz o número de possíveis candidatos por um fator de 2

Vantagens:
- Eficiência da busca
- Simplicidade da implementação

Desvantagens:
- Nem todo arranjo está ordenado
- Exige o uso de um arranjo para armazenar os dados (faz uso do fato de que os índices do vetor são inteiros consecutivos)
- Inserção e remoção de elementos são ineficientes, pois requer realocação de elementos

A busca binária pode ser usada com a organização de tabela sequencial indexada, assim, em vez de pesquisar o índice sequencialmente, pode-se usar uma busca binária.
## Busca por Interpolação
É um tipo de busca que requer que as chaves estejam uniformemente distribuídas. Se elas estiverem, esse método pode ser ainda mais eficiente que a busca binária.

A ideia é que com as chaves distribuídas, pode-se esperar que a chave x esteja aproximadamente na posição: $\displaystyle meio = inf + (sup-inf) \times \frac{(x - A[inf])}{(A[sup] - A[inf])}$, sendo que $inf$ e $sup$ são redefinidos iterativamente como na busca binária.

Se as chaves estiverem uniformemente distribuídas, raramente precisará de mais comparações. Se as chaves não estiverem uniformemente distribuídas, a busca por interpolação pode ser tão ruim quanto uma busca sequencial

Complexidade:
- A complexidade de tempo é $O(\log{(\log{n})})$, se as chaves estiverem uniformemente distribuídas

Desvantangem:
- Em situações práticas, as chaves tendem a se aglomerar em torno de determinados valores e não são uniformemente distribuídas. Por exemplo, há uma quantidade maior de nomes começando com "S" do que com "Q".
## Hashing
### Acesso em tempo constante
Tradicionalmente, é feito endereçamento direto em um arranjo. Ou seja, cada chave $k$ é mapeada na posição $k$ do arranjo. Logo, há uma função de mapeamento: $f(k) = k$.

As vantagens do endereçamento direto são:
- Acesso direto e, por isso, rápido via indexação do arranjo

As desvantagens do endereçamento direto são:
- Uso ineficiente do espaço armazenado
	- Se declarar um arranjo do tamanho da maior chave?
	- Se as chaves não forem contínuas?
	- Pode sobrar espaço? Pode faltar?

Assim, temos como alternativa o Hashing
### O Hashing
O hashing faz acesso direto ao vetor mas o endereçamento é indireto. Ou seja, temos uma função de mapeamento tal que, em geral, $h(k) \neq k$. Isso resolve o uso ineficiente do espaço de armazenamento. 

A complexidade é, em média, $O(c)$ e independe do tamanho do arranjo. Idealmente temos que $c = 1$.

O significado da palavra hash é fazer picadinho de carne/vegetais para cozinhar ou então fazer bagunça 
### Conceitos e Definição
O Hashing, também conhecido como tabela de espalhamento ou de dispersão, é uma técnica que utiliza uma função $h$ para transformar uma chave $k$ em endereço, que é usado para armazenar e recuperar registros.

A ideia é particionar um conjunto de elementos (possivelmente infinito) em um número finito de classes. Temos $B$ classes, que vão do $0$ a $B - 1$. Essas classes são chamadas de Buckets.

A função $h$ é chamada de função hash. Essa função retorna o valor hash de $k$, que é usado como o endereço para armazenar a informação cuja a chave é $k$. Dizemos também que $k$ pertence ao bucket $h(k)$. Por exemplo, se temos que a chave é $k = luis$, ao usar k na função hash temos $h(k) = 10$, logo a chave $luis$ será armazenada no endereço 10 da memória e chamamos o endereço de bucket, no caso bucket de $h(k)$.

A função hash é utilizada para inserir, remover ou buscar um elemento. Ela deve ser determinística, ou seja, resultar sempre no mesmo valor para uma determinada chave.

Dizemos que ocorre uma **colisão** quando a função hash produz o mesmo endereço para chaves diferentes. Essas chaves com mesmo endereço são ditas "sinônimos". O melhor caso é quando cada chave resulta em um endereço, o pior caso é quando todas as chaves resultam no mesmo endereço, mas é aceitável algumas chaves, apenas, resultarem no mesmo endereço.

Uma distribuição uniforme, ou seja, cada chave resulta um endereço, é muito difícil, pois depende de cálculos matemáticos e estatísticos complexos. Poderíamos tomar uma solução que aparentemente gera endereços aleatórios, mas existe a chance de alguns endereços serem gerados mais de uma vez e de alguns nunca serem gerados. Então, existem alternativas melhores que a puramente aleatória.

Os segredos para um bom hashing são:
- Escolher uma boa função hash (em função dos dados)
	- Uma que distribua uniformemente os dados, na medida do possível (Hash Uniforme)
	- Uma que evita colisões
	- Uma que é fácil e rápida de computar
- Estabelecer uma boa estratégia para tratamento de colisões

Uma técnica simples e muito utilizada, que produz bons resultados é:
- Para chaves inteiras, calcular o resto da divisão $\displaystyle \frac{k}{B}$ ou então $k \, \% \, B$, sendo que o resto indica a posição de armazenamento. Nesse caso $k$ é o valor da chave e $B$ é o tamanho do espaço do endereçamento
- Para chaves do tipo string, tratar cada caractere como um valor inteiro (ASCII), somá-los e pegar o resto da divisão por $B$
- Vale ressaltar que $B$ deve ser primo, preferencialmente

A ideia por trás de usar uma função hash que utiliza do resto é que os elementos sempre caem no intervalo entre $0$ e $n-1$, que coincidem com os valores que usamos como índices para acessar a memória.

Entretanto, existem diversas outras funções hash:
- Examinar as chaves em busca de um certo padrão
- Extrair dígitos de uma parte da chave e somar
- Elevar a chave ao quadrado e considerar os dígitos intermediários do resultado
- Extrair a raiz e considerar apenas as casas decimais
- Entre outras

Chamamos de fator de carga, $\displaystyle \alpha = \frac{n}{m}$, o número esperado de elementos por posição na tabela, dado que $n$ é o número de elementos em uma tabela de $m$ posições.

### Tipos de Hashing
#### Estático
Nesse tipo de hashing o espaço de endereçamento não muda. Ele pode ser de dois tipos:
- Fechado
	- Permite armazenar um conjunto de informações de tamanho limitado
	- Usa-se técnicas de rehash como tratamento de colisões, entre elas:
		- Overflow progressivo
		- 2ª função hash
- Aberto
	- Permite armazenar um conjunto de informações de tamanho potencialmente ilimitado
	- Usa o encadeamento de elementos para tratamento de colisões
##### Hashing Fechado
Esse tipo de hashing utiliza uma tabela de buckets para armazenar informações e os elementos são armazenados na própria tabela.

Para colisões, aplica-se técnicas de rehash. Isso significa que se a posição $h(k)$ está ocupada (lembre-se de que h(k) é um índice da tabela), aplicar a técnica de rehash sobre $h(k)$ que deve retornar o próximo bucket livre. Algumas características de uma boa técnica de rehash são: cobrir o máximo de índices entre $0$ e $B-1$, e evitar agrupamento de dados. Além de utilizar o índice resultante de $h(k)$ na técnica de rehash, pode-se usar a própria chave k e outras funções de hash.

Uma das técnicas rehash é o **Overflow Progressivo**, que pode utilizar a equação: $\displaystyle h(k) = (h(k) + i) \, \% \, B$ com $i$ variando de $1$ a $B-1$ ($i$ é incrementado a cada tentativa). Uma dificuldade nessa técnica é como saber que a informação procurada não está armazenada, pois, por exemplo, se houver uma remoção na tabela e a chave estiver depois dela, pode resultar em algum problema; mas para resolver isso, podemos não eliminar o elemento, mas indicar que a posição foi esvaziada e que a busca deve continuar. O uso da equação mostrada acima, é conhecido como **sondagem linear**, pois todas as posições da tabela são checadas no pior caso. Outra equação que pode ser usada é $h(k) = (h(k) + c_1 \times i + c_2 \times i^2) \, \% \, B$, com $i = 1, ..., B-1$ e constantes $c_1$ e $c_2$, essa é chamada de **sondagem quadrática**, considerada melhor que a linear pois evita "mais" o agrupamento de elementos, porém ela não garante encontrar um espaço vazio, mesmo que ele exista. A vantage, de usar um overflow progressivo é a simplicidade. Já as desvantagens são:
- Agrupamento de dados (causado por colisões (característica do overflow progressivo))
- Com estrutura cheia, a busca fica lenta (característica do hashing fechado)
- Dificulta inserções e remoções (característica do hashing fechado)

A outra técnica de rehash é a **2ª função hash**, ou **hash duplo**. Essa técnica faz o uso de duas funções:
- h(k): função hash primária
- haux(k): função hash secundária

O rehash com uma segunda função fica, por exemplo: $h(k) = ( h(k) + i \times haux(k) ) \, \% \, B$. Algumas boas funções são:
- $h(k) = k \, \% \, B$
- $haux(k) = 1 + k \, \% \, (B - 1)$

A vantagem dessa técnica é evitar o agrupamento de dados em geral. Já as desvantagens são:
- Difícil de achar funções hash que, ao mesmo tempo, satisfaçam os critérios de cobrir o máximo de índices da tabela e evitem agrupamento de dados
- Operações de busca, inserção e remoção são mais difíceis

Uma alternativa para fazer o hashing com uma função hash e uma técnica de rehash é representar tudo isso em uma única função dependente do número da tentativa (i). Por exemplo: $h(k, i) = (k + i) \, \% \, B$, com $i = 0, ..., B-1$. Agora a função $h$ depende de dois fatores: a chave $k$ e a iteração $i$. Note que $i = 0$ na primeira execução, resulta na função hash tradicional de divisão que já conhecíamos. Quando $i = 1, ..., B-1$, já estamos aplicando a técnica de rehash de sondagem linear.
##### Hashing Aberto
Nesse tipo de hashing, a tabela de buckets, indo de $0$ a $B-1$, contém apenas ponteiros para uma lista de elementos. Quando há colisão, o sinônimo é inserido no bucket como um novo nó da lista. A busca deve percorrer a lista, com isso, nota-se que se as listas estiverem ordenadas, reduz-se o tempo de busca.

As vantagens do hashing aberto são:
- A tabela pode receber mais itens mesmo quando um bucket já foi ocupado
- Permite percorrer a tabela por ordem de valor hash

As desvantagens do hashing aberto são:
- Espaço extra para as listas
- Listas longas implicam em muito tempo gasto na busca
	- Se as listas estiverem ordenadas, reduz-se o tempo de busca
	- Custo extra com a ordenação
##### Eficiência
Para o hashing fechado:
- Depende da técnica de rehash:
	- Com overflow progressivo, após várias inserções e remoções, o número de acessos aumenta
- A tabela pode ficar cheia
- Pode haver mais espaço para a tabela, pois não são necessários ponteiros e campos extras como no hashing aberto

Para o hashing aberto:
- Depende do tamanho das listas e da função hash:
	- Listas longas degradam desempenho
	- Poucas colisões implicam em listas pequenas
#### Dinâmico
Nesse tipo de hashing o espaço de endereçamento pode aumentar (fora do escopo da disciplina).

### Funções Hash
Algumas funções boas para hash são:
- Divisão
	- $h(k) = k \, \% \, m$, com um $m$ (tamanho da tabela) tendo um tamanho primo de preferência.
- Multiplicação
	- $h(k) = (k \times A \, \% \, 1) \times m$, com $A$ sendo uma constante entre $0$ e $1$
	- $(k \times A \, \% \, 1)$ recupera a parte fracionária de $k \times A$
	- Knuth sugere $\displaystyle A = \frac{(\sqrt{5} - 1)}{2} = 0,6180...$
- Hash Universal
	- A função hash é escolhida aleatoriamente no início de cada execução, de forma que minimize/evite tendências de chave
		- Por exemplo, $h(k) = ((A \times k + B) \, \% \, P) \, \% \, m$
		- P é um número primo maior do que a chave k
		- A é uma constante escolhida aleatoriamente de um conjunto de constantes $\{0, ..., P-1\}$ no início da execução
		- B é uma constante escolhida aleatoriamente de um conjunto de constantes $\{0, ..., P-1\}$ no início da execução
	- Diz-se que $h$ representa uma coleção universal de funções
### Desvantagem
A desvantagem de usar hashing é que os elementos da tabela não são armazenados sequencialmente e nem sequer existe um método prático de percorrê-los em sequência.
### Complexidade de modo geral
De modo geral pode-se dizer que a complexidade de tempo é de $O(1)$, mas colisões podem aumentar o tempo para $O(n)$.
## Critérios para se eleger um método de busca
- Eficiência da busca
- Eficiência de outras operações
	- Inserção e remoção
	- Listagem e ordenação de elementos
	- Etc.
- Frequência das operações realizadas
- Dificuldade de implementação
- Consumo de memória (interna)
