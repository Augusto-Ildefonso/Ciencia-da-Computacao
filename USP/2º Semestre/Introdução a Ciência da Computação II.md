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
- 
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

Os algoritmos de ordenação trabalham sobre registros de um arquivo (eles que são trocados de posição), e deles somente uma parte importa: a chave, o resto dos dados dos arquivos não interferem na ordenação. Além disso, um algoritmo de ordenação é estável se a ordem relativa dos itens com a mesma chave se mantém inalterada após a ordenação.

Também é necessária fazer uma diferenciação entre ordenação interna e externa. Dizemos que é uma ordenação interna se todos os registros cabem na memória principal (formam um único array). Já se o arquivo a ser ordenado não cabe na memória principal e por isso precisam ser armazenados em uma fita ou disco, chamamos de ordenação externa. Na ordenação interna os arquivos podem ser acessados imediatamente, já na ordenação externa eles são acessados sequencialmente ou em grandes blocos.

Há também a ordenação por endereço, nela nós mantemos uma tabela de ponteiros para os registros e durante a ordenação os ponteiros que são alterados. Vale mencionar também que os registros a serem ordenados podem ser complexos ou não, mas os métodos de ordenação independem desse fator.

Existem vários métodos de implementar a ordenação. Dependendo do problema, um algoritmo pode ser mais vantajoso do que outro.
## Bubble-sort
O bubble-sort é o algoritmo de ordenação mais simples. Ele consiste em repetidas trocas de elementos adjacentes caso estejam na ordem errada. Entretanto, ele não é recomendado para casos com grande quantidade de dados, visto que a complexidade dele para o pior tempo é muito alta (em um vetor de $n$ elementos ele precisa de $n-1$ iterações)

Nele, primeiro, começando da esquerda, comparamos os elementos adjacentes e os maiores são colocados a direita, desse jeito o maior elemento está no fim mais a direita. Esse processo então continua para o segundo maior e assim por diante.

Pode-se aprimorar o algoritmo, detectando quando o vetor já está ordenado. Isso ocorre quando em um determinado passo, nenhuma troca é realizada e também diminuindo o número de vezes que o vetor é percorrido, de modo que o vetor percorra $n-i$ iterações.

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
O Quick-Sort é um algoritmo de ordenação baseado na lógica de dividir e conquistar. Ele tem um tempo de execução no pior caso de $O(n^{2})$. Porém ele é a melhor opção prática para ordenação pois ele possui um tempo médio de execução de $O(n \, \log{n})$ e os fatores que ficam ocultos na representação anterior são pequenos.

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
O Shell-Sort é uma variação da ordenação simples. Enquanto a inserção simples compara elementos adjacentes e move uma posição a frente, a Shell-Sort permite a troca de elementos distantes. 

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
- Complexidade de espaço auxiliar é $O(1)$ dado que a única memória extra usada é para variáveis temporais enquanto troca dois valores do vetor. A seleção direta nunca faz mais que $O(n)$ trocas e pode ser útil  quando escrever na memória é custoso

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