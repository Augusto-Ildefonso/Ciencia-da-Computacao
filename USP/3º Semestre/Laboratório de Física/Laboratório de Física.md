# Medidas de Grandezas Físicas
Nas ciências exatas, o resultado de uma medida de grandeza física deve ser dado a partir do seu valor e da sua incerteza, expressos no sistema apropriado. Esses valores devem refletir com maior fidelidade possível o processo de medida completo.
## Medidas Diretas e Indiretas
Nas medidas diretas, o valor numérico da medida é lido diretamente da escala do instrumento. Exemplos: comprimento (medido pela régua), tempo (medido pelo cronômetro) ou corrente elétrica (medida por um amperímetro).
Nas medidas indiretas, o valor numérico da medida é obtido através de um cálculo realizado com valores de medidas diretas. A maioria das medidas físicas são medidas indiretamente. Exemplo: volume (que pode ser obtido através das medidas diretas com régua ou paquímetro), velocidade (medida através da distância percorrida e do tempo). Porém, para o caso da velocidade, ainda sim é possível construir um aparelho que meça ela, como o velocímetro.
## Precisão dos Instrumentos
Todos os instrumentos de medida direta tem uma precisão $D$ associada a eles. Por exemplo, uma trena tem precisão $D = 1 \, mm$, já alguns instrumentos tem precisão entre dois intervalos da trena, ou seja, tem precisão $D = 0,5 \, mm$. Quando o instrumento tem um mostrador eletrônico, a precisão é a última casa decimal. Entretanto, é preciso ressaltar que a precisão dos instrumentos não é garantida para toda medida, mas sim para aquelas que fazem um uso correto do instrumento.
## Erros de Medida
Uma grandeza física, a ser determinada pelo processo de medida, possui um valor que poderíamos chamar de valor verdadeiro. As vezes esse valor já é conhecido antes da medição, mas na maioria dos casos ele é desconhecido. A medição fornece o valor medido e quanto mais próximo ele é do valor verdadeiro maior é a exatidão da medida. Porém, todo experimento possui uma incerteza intrínseca, chamada de erro, por isso nunca saberemos dizer se o valor medido é exatamente o valor verdadeiro. Para avaliar de que ordem é o erro, devemos notar que existem três fontes fundamentais de erro.
### Erros Grosseiros
Os erros grosseiros são aqueles cometidos por imperícia (falta de habilidade ou conhecimento) do operador, como erros de leitura ou de cálculo, desconhecimento do método experimental ou do uso dos instrumentos. Porém, ela não será estudada e fica como responsabilidade do operador conhecer o método de medida e operar os instrumentos.
### Erros Sistemáticos
Os erros sistemáticos são cometidos de forma autêntica durante o experimento, tipicamente por uma limitação do método de medida ou uma falha do instrumento. Esses erros atuam sempre no mesmo sentido sobre o valor numérico, causando resultados por excesso ou defeito, com relação ao valor verdadeiro. A repetição do experimento nas mesmas condições não elimina esses erros. Por isso, deve-se revisar cuidadosamente o método de medida e conferir a calibração dos instrumentos, para determinar se há a possibilidade de estar cometendo erros sistemáticos.
### Erros Aleatórios ou Estatísticos
Os erros aleatórios são causados por mudanças aleatórias, não controladas, nas condições do processo de medida, incluindo o operador, os instrumentos, o ambiente e o próprio sistema físico. Esses erros são os mais importantes de analisar. Esse tipo de erro é inevitável, mas pela sua natureza aleatória é possível definir estratégias experimentais para minimizá-los e para estimar o quanto influenciam na confiabilidade do resultado numérico.
## Incerteza em Medidas Diretas
Devido a existência de erros aleatórios, não é possível garantir que o resultado numérico $x_i$ obtido na medida de uma grandeza física $X$ será reprodutível caso repita o experimento. Desse modo, uma série de $N$ medidas pode mostrar uma dispersão dos valores e quando a dispersão é aleatória, aparecem valores acima e abaixo do valor verdadeiro com a mesma probabilidade. Por causa disso, ao calcular a média aritmética dos $x_i$, dada pela equação abaixo, os erros aleatórios tendem a se cancelar mutuamente.
$$\bar{x} = \frac{\sum^{N}_{i = 1}x_{i}}{N}$$
Para um $N$ suficientemente grande de medidas, podemos esperar que $\bar{x}$ se aproxime do valor verdadeiro e o resultado do experimento seja cada vez mais exato.
Para mensurar a incerteza provável associada à dispersão dos resultados do experimento, existem duas formas comuns que permitem avaliar o grau de dispersão: o desvio médio e o desvio padrão.
O desvio médio $\Delta$ é simplesmente a média aritmética dos desvios de cada dado experimental com relação ao valor médio, em módulo. Veja a fórmula abaixo.
$$\Delta = \frac{ \sum^{N}_{i = 1} | x_{i} - \bar{x}|}{N}$$
O desvio padrão $\sigma$ tem um significado semelhante, utilizando a função quadrado, que também é sempre positiva, em lugar do módulo dos desvios. A raiz quadrada garante que o desvio padrão terá mesma unidade de grandeza que $X$. Veja abaixo a fórmula.
$$\sigma = \sqrt{ \frac{ \sum^{N}_{i = 1} \left( x_{i} - \bar{x} \right)^{2} } {N - 1} }$$
Tanto o desvio médio quanto o desvio padrão indicam a ordem de grandeza da dispersão dos dados ao redor de $\bar{x}$. Logo, o resultado do processo de medida pode ser informado por um intervalo $( \bar{x} - \sigma, \bar{x} + \sigma )$. Com um tratamento estatístico rigoroso mostra-se que se o experimento for repetido, tem-se uma probabilidade de 68% de que o valor medido se encontre dentro desse intervalo. Portanto, o resultado do experimento com a sua incerteza deve ser representado da seguinte forma:
$$\bar{x} \pm \sigma$$
Ou de forma menos rigorosa:
$$\bar{x} \pm \Delta$$
A conclusão mais importante a se tirar disso é que o resultado do experimento não é simplesmente um valor mais provável, mas sim um intervalo de confiança que dá uma ideia de magnitude dos erros aleatórios afetando o experimento. Os experimentos de maior precisão são aqueles cujo desvio padrão é menor.  É importante ressaltar que um experimento preciso é diferente de um experimento exato, isso porque a presença de erros sistemáticos podem afastar todos os valores $x_{i}$ do valor verdadeiro.
Apesar das fórmulas dos desvios mostrarem que os desvios tendem a reduzir quando o $N$ aumenta (visto que são inversamente proporcionais) e, assim, poderíamos aumentar a precisão simplesmente repetindo as medidas, isso é falso. Isso porque a precisão da medida está limitada pela precisão dos próprios instrumentos, logo quando os valores calculados para os desvios são menores que a precisão $D$ do instrumento, a incerteza será dada pelo próprio valor $D$:
$$\bar{x} \pm D$$
### Dados sem dispersão
Em algumas medidas diretas, pode ocorrer de todos os valores $x_{i}$ medidos serem idênticos ou difiram no máximo no valor da mínima divisão da escala do instrumento $D$. Nesse caso a dispersão é nula e não há necessidade de calcular a média, pois o resultado do experimento é único. Isso significa que os erros aleatórios são pequenos, menores que a precisão $D$ do instrumento. Nesse caso, a incerteza do experimento pode ser atribuída à D e o resultado da medida é:
$$x_{i} \pm D$$
### Forma correta de expressar o resultado de uma medida
![[Pasted image 20250317220255.png]]
## Incerteza em medidas indiretas: propagação de erros
Quando uma grandeza $z$, medida de forma indireta, é uma função de várias grandezas medidas de forma direta, junto das suas incertezas ($x \pm \Delta x, y \pm \Delta y, ...$), sua incerteza será determinada a partir das incertezas das grandezas medidas.
Existe uma forma de calcular a propagação das incertezas para qualquer operação matemática elementar ou função. Supondo $z = f(x, y, ...)$ com as incertezas ($x \pm \Delta x, y \pm \Delta y, ...$), a incerteza propagada pode ser calculada como:
$$\Delta z = \left| \frac{ \partial f}{\partial x} \right| \Delta x \, + \left| \frac{ \partial f }{ \partial y } \right| \Delta y \, + \, ...$$
Aplicando essa equação para funções simples, obtém-se os resultados de $z \pm \Delta z$ para várias funções elementares. Veja abaixo na tabela abaixo a propagação de incertezas para funções elementares.
![[Pasted image 20250318185333.png]]
No cálculo de propagação de erros, constantes físicas bem conhecidas como $g$, ou números irracionais como $\pi$ ou $e$ são considerados sem erro.
## Algarismos significativos e arredondamento
Quando obtemos os valores $\bar{x}, \sigma$ ou $\Delta$ através de cálculos, são originados números com vários dígitos. Considerando a precisão e os erros aleatórios, percebe-se que muitas das casas decimais obtidas são irrelevantes.
O parâmetro chave é a própria incerteza, seja $\sigma$, $\Delta$ ou D. Vimos que a incerteza é o tamanho de um intervalo probabilístico. Portanto, a extensão desse intervalo fica essencialmente definida quando especificamos a primeira casa significativa (primeira casa diferente de 0). Consequentemente, como o resultado $\bar{x}$ do experimento já está afetado pelo erro nessa casa, seu valor pode ser truncado e arredondado nessa mesma ordem de grandeza.
## Comparação de grandezas físicas com incertezas
Suponhamos que se deseje comparar dois resultados com incerteza $x_{1} \pm \sigma_{1}$ e $x_{2} \pm \sigma_{2}$, relativos a diferentes medidas da mesma grandeza física. Para poder comparar os dois devemos comparar a diferença entre os valores mais prováveis com relação aos erros. Assim, consideramos que os resultados $x_{1}$ e $x_{2}$ são equivalentes quando:
$$|x_{1} - x_{2}| < 2 (\sigma_{1} + \sigma_{2})$$
Essa relação indica que a separação entre os valores é, no máximo, duas vezes a combinação das incertezas. Por outro lado, os resultados serão considerados como não equivalentes quando
$$|x_{1} - x_{2}| > 3 (\sigma_{1} + \sigma_{2})$$
Quando o valor da diferença $|x_{1} - x_{2}|$ fica entre as condições expressas entre as equações acima, o resultado desses experimentos não é suficientemente conclusivo para afirmar se há equivalência ou não entre as medidas.
# Tabela de Dados e Gráficos
## Tabelas
Muitas vezes os experimentos tem resultados que vinculam duas grandezas físicas, ou dois parâmetros, formando o par $(x, y)$. Esse par pode ser representado diretamente em uma tabela de duas colunas. Cada grandeza tabelada deve ser identificada no cabeçalho de sua respectiva coluna junto com suas unidades. Se a incerteza dos valores for a mesma para todos, ela pode ser expressa no cabeçalho também, se não, deve ser expressa junto de cada valor.
Cada tabela deve ter um número de identificação que deve ser usado no texto para referenciá-la. Além disso também deve ter uma legenda acima, explicando brevemente o conteúdo. Se necessário usa-se notação científica para simplificar os números.
Veja abaixo um exemplo.
![[Pasted image 20250402080618.png]]
### Dicas para criar boas tabelas
- Identifique a tabela com um número (ex.: Tabela 1), que será usado para citá-la no texto, e coloque no topo uma breve legenda explicativa do conteúdo.
- Indique, no topo de cada coluna, a grandeza física e suas unidades.
- Use notação científica para reduzir a quantidade de dígitos. Se a potência de 10 é a mesma para todos os valores, coloque-a no topo da tabela junto às unidades.
- Indique a incerteza dos dados. Se for a mesma para todos, indique no topo da coluna.
## Gráficos
A representação dos dados através de gráficos tem a vantagem de permitir visualizar a relação entre as grandezas analisadas. Existem algumas regras gerais para elaboração de gráficos, que são aceitas pela comunidade científica:
- O gráfico sempre deve estar numerado e ter uma legenda explicativa, de maneira que o leitor compreenda essencialmente o que se representa sem ter de ler o texto do relatório.
- Os eixos do gráfico devem conter legendas que indiquem claramente a grandeza, as unidades e, se houver, o fator exponencial dos dados representados.
- As escalas de cada eixo devem ser escolhidas para visualizar claramente o comportamento extremo dos dados. Dependendo da situação, não é obrigatório que a escala abranja a origem $(0,0)$ dos eixos de coordenadas.
- A numeração das escalas deve ser equilibrada, correspondendo a números redondos. Nunca se colocam os valores dos dados experimentais sobre os eixos; para isso existe a tabela.
- O tamanho dos símbolos deve ser suficientemente claro para identificar o dado experimental. Quando a incerteza 𝜎 (ou ∆) do dado é maior que o tamanho do símbolo sobre o gráfico, é conveniente traçar as barras de incerteza de comprimento $\pm$𝜎 (ou $\pm$∆). Na figura 2.1, são mostradas as barras de incerteza na variação dos comprimentos. A incerteza na temperatura é menor que o tamanho do círculo e, portanto, não se encontra representada no gráfico.
-  A grandeza representada no eixo horizontal usualmente é escolhida como aquela que é melhor controlada durante o experimento; o aparelho experimental permite variá-la independentemente e tem menor incerteza relativa que a outra grandeza.
- Se o gráfico evidencia uma relação linear entre as grandezas físicas representadas, é possível traçar a reta que mais perfeitamente represente essa relação. Ela deve ser a melhor aproximação aos dados experimentais em média e pode ser traçada graficamente de acordo com o critério do observador. Alternativamente, existem métodos quantitativos para determinar univocamente os coeficientes angular e linear.
Veja um exemplo abaixo.
![[Pasted image 20250402081338.png]]
### Dicas para criar bons gráficos
- A variável independente deve ser representada, sempre que possível, no eixo horizontal.
- Linearize os dados quando for possível, operando sobre as colunas ou usando escalas logarítmicas.
- Escolha as escalas de forma a aproveitar a maior área possível do gráfico com os dados. Porém, você deve encontrar um compromisso para que isso não resulte em escalas esdrúxulas (por exemplo com divisões fracionárias).
- Identifique as grandezas sobre os eixos e suas unidades.
- Numere as escalas com poucos números redondos. Use notação científica para reduzir os dígitos.
- Desenhe claramente os dados experimentais e, caso haja mais de um conjunto, use símbolos (círculos, quadrados, cruzes etc.) ou cores diferentes.
- Quando a incerteza dos dados for maior que o tamanho do símbolo, coloque bandas de erro.
- Identifique o gráfico com um número (ex.: Figura 1), que será usado para citá-lo no texto. Coloque uma breve legenda no gráfico.
## Linearização e escalas logarítmicas
As escalas lineares são aquelas em que as divisões mantêm sempre a mesma relação de escala. Existem outras escalas possíveis, cuja relação não se mantém fixa, que podem ser convenientes para evidenciar certos comportamentos dos dados representados.  Como a reta é o único traço que pode ser facilmente visualizado sem ambiguidades sobre um gráfico, as transformações de escala mais úteis são aquelas que tendem a linearizar o gráfico dos dados experimentais.
### Linearização dos dados
Quando existe uma presunção sobre a relação matemática entre as duas grandezas y e x, representadas em um gráfico, é possível transformar os próprios dados para revelar se essa relação proposta é correta.
Por exemplo, temos um gráfico no qual é possível ver que a relação de x e y não é linear. Porém não há como saber se é quadrática, cúbica, etc. Então, cria-se uma nova variável a partir da suposição (exemplo $X = x^{3}$) e representa-se graficamente X e y. Supondo que na representação fique claro que a relação entre as quantidade é linear. Assim, comprovou-se a teoria de que $y = \alpha x^{3}$ e o valor do coeficiente angular $\alpha$ pode ser calculado diretamente pela inclinação da reta.
### Escalas Logarítmicas
Um outro método de linearização consiste em manter os valores $x$ e $y$ que estão nas tabelas e transformar as escalas do gráfico de maneira logarítmica. Para fazer isso existem duas formas: usar papéis especiais que já contém escalas transformadas em logarítmico ou usar programas de computadores que fazem essa transformação. Um gráfico em escala logarítmica também é chamado de "log-log" quando os dois eixos estão em escala logarítmica.
Veja abaixa os gráficos. O gráfico **a** tem uma escala linear e o **b** tem uma escala logarítmica. Vale ressaltar que ambos foram criados a partir da mesma tabela.
![[Pasted image 20250402074847.png]]
Para extrair informações do gráfico **b** deve-se lembrar que as coordenadas representam valores logarítmicos de grandeza. Por exemplo, o valor 10 no eixo representa $\log 10$.
Perceba também que a distância entre os valores $\log 1$ e $\log 10$, assim como $\log 10$ e $\log 100$, e também $\log 100$ e $\log 1000$, são as mesmas. Isso resulta de uma propriedade de logarítmicos. Se fizer a distância deles verá que é 1. Essa distância é chamada de ciclo ou década e corresponde a um incremento de 10 na grandeza representada.
Observe, ainda, que, diferentemente do que ocorre na escala linear, a escala logarítmica é progressivamente comprimida para valores mais altos dentro de uma mesma década.
#### Linearização de função potência
Uma aplicação muito importante das escalas logarítmicas é na linearização de dados. Suponha a seguinte relação entre grandezas: $$y = a x^{n}$$sendo $a$ e $n$ constantes. Aplicando o logarítmico dos dois lados da igualdade, temos: $\log y = \log a + n \log x$. Portanto, um gráfico das grandezas (x, y), em escalas logarítmicas, resultará em uma reta de inclinação n ($y = ax + b$). O valor de n é obtido tomando as coordenadas, de dois pontos ($x_1$ ; $y_1$) e ($x_2$; $y_2$) quaisquer, pertencentes à reta traçada, lembrando que as coordenadas lidas correspondem aos logarítmicos dos valores lidos: $$n = \frac{ \log{y_{2}} - \log{y_{1}}}{ \log{x_{2}} - \log{x_{1}} }$$.
#### Linearização da função exponencial
Outra aplicação de linearização importante é o caso de uma relação exponencial, como: $$y = a b^{cx}$$, sendo $a$, $b$ e $c$ constantes. Aplicando logaritmo em ambos os lados dessa equação, encontramos: $\log y = \log {(a)} - c \log {(b)} \, x$.
A equação acima mostra que existe uma relação linear entre $\log y$ e $x$. Portanto existe um gráfico "mono-log" (um eixo linear e outro logarítmico) com o eixo vertical em escala logarítmica e o
eixo horizontal em escala linear, que mostrará uma reta. A inclinação da reta é dada pelo coeficiente $B = c \log(b)$ que pode ser calculado por: $$B = \frac{  \log{y_{2}} - \log{y_{1}} }{ x_{2} - x_{1}}$$
# Relações Lineares entre Dados Experimentais
Muitas vezes a relação encontrada entre grandezas físicas é linear ou pode ser linearizada. Isso significa que ela pode ser escrita da seguinte forma: 
$$y = ax + b$$
Nesse caso, devemos determinar a melhor reta que representa os dados experimentais e calcular o valor dos parâmetros $a$ e $b$, também conhecidos como coeficiente angular (ou inclinação) e coeficiente linear (ou ordenada na origem), respectivamente. Existem duas formas de realizar essa determinação: do modo gráfico ou do modo analítico. Para o método analítico, uma das formas é o método dos mínimos quadrados.
## Método Gráfico
Esse método consiste em representar os dados experimentais $(x, y)$ em um gráfico e traçar a reta que mais se aproxima da maioria deles. Isto é válido para qualquer combinação de escalas nos eixos: lineares ou logarítmicas.
O defeito desse método é que a reta resultante depende do critério do observador.
Uma vez que temos a reta, podemos determinar os coeficientes de forma analítica, a partir das coordenadas de dois pontos arbitrários da reta, de coordenadas $(x_1, y_1)$ e $(x_2, y_2)$. Para minimizar os erros de cálculos, devemos escolher dois pontos bem separados entre si. Assim, temos que o coeficiente angular é: $$a = \frac{y_2 - y_1}{x_2 - x_1}$$
E o coeficiente linear é: $$b = \frac{y_1 x_2 - y_2 x_1}{x_2 - x_1}$$
De forma alternativa, se é possível visualizar um ponto que intersecta o eixo y, ou seja, um ponto de coordenada $(0, y_3)$ temos $b = y_3$.
Se um ou dois eixos forem logarítmicos, deve-se ter o cuidado de usar o logarítmico da grandeza correspondente. Por exemplo, para o cálculo da inclinação:
- Escala di-log: $$a = \frac{\log{y_2} - \log{y_1}}{\log{x_2} - \log{x_1}}$$
- Escala mono-log (eixo vertical): $$a = \frac{\log{y_2} - \log{y_1}}{x_2 - x_1}$$
## Método dos Mínimos Quadrados
Esse é um método analítico para encontrar a melhor reta que represente o conjunto de $N$ pares de dados experimentais $(x_i, y_i)$ com $i = 1, 2, ..., N$, independentemente de critérios do observador. A ideia desse método é definir a melhor reta como aquela que minimiza as distâncias verticais em relação aos dados experimentais.
O método dos mínimos quadrados, ou regressão linear, considera a soma dos quadrados das distâncias: $$S = \sum_{i = 1}^{N}(y_{ci} - y_{i})^{2}$$
Onde $y_{ci}$ é o valor calculado para o i-ésimo dado com a equação da melhor reta $y_{ci} = ax_{i} + b$. O processo de minimização de $S$, como função dos parâmetros da reta, fornece as seguintes expressões:
- Coeficiente angular: $$a = \frac{ \sum(x_{i} - \bar{x}) y_{i} }{ \sum(x_{i} - \bar{x})^{2} }$$
- Coeficiente linear: $$b = \bar{y} - a \bar{x}$$
Onde todos os somatórios correm com $i = 1, 2, ..., N$ e $\bar{x} = \frac{\sum x_{i}}{N}$ e $\bar{y} = \frac{\sum y_{i}}{N}$.
O método também fornece as incertezas destes parâmetros ($\Delta a$ e $\Delta b$) que estão diretamente relacionadas com a dispersão média $\Delta y$ dos dados experimentais em relação a reta:
- Dispersão média do ajuste $$\Delta y = \sqrt{\frac{\sum (ax_{i} + b - y_{i})^{2}} { N - 2 }}$$
- Incerteza do coeficiente angular: $$\Delta a = \frac{\Delta y}{\sqrt{\sum (x_{i} - \bar{x})^{2}}}$$
- Incerteza do coeficiente linear: $$\Delta b = \sqrt{ \frac{ \sum x_{i}^{2} }{ N \sum (x_{i} - \bar{x})^{2} } } \Delta y$$
# Estática
## Equilíbrio Estático
A estática é a área da física que estuda o equilíbrio de corpos rígidos. Equilíbrio significa ausência de aceleração e, portanto, velocidades de translação e rotação são constantes. Geralmente em problemas de equilíbrio estático consideramos elas nulas. As condições de equilíbrio de um sistema estão determinadas pelas Leis de Newton da Mecânica:
$$somatória \, das \, forças \, externas \, nula: \, \sum_{i}\vec{F_{i}} = 0$$
$$somatória \, dos \, torques \, externos \, nula: \, \sum_{i}\vec{r_{i}} \times \vec{F_{i}} = 0$$
Nessas equações, $\vec{F_{i}}$ são as forças externas atuando sobre o sistema e $\vec{r_{i}}$ os pontos de aplicação de cada uma, quando o sistema é extenso, como um corpo rígido, por exemplo. A primeira condição garante que o centro de massa do sistema tem aceleração nula, então se inicialmente está em repouso ele se manterá nesse estado e não haverá translação. Já a segunda condição é necessária para garantir que o sistema não vai se acelerar angularmente e, assim, não vai rotacionar. Além disso, a condição dois é imprescindível para determinar o equilíbrio de corpos rígidos. Em problemas mais simples de estática, para garantir o equilíbrio translacional do centro de massa do corpo, muitas vezes é suficiente que somente a primeira condição seja satisfeita.
É importante ressaltar que as equações acima são vetoriais, então para operar com elas é necessário decompô-las em três direções perpendiculares, resultando assim, em três equações escalares. Nos problemas que iremos trabalhar, as forças atuam em um plano, assim, basta decompor em duas direções perpendiculares, $x$ e $y$. Logo:
$$\sum_{i}\vec{F_{i\,x}} = 0$$
$$\sum_{i}\vec{F_{i\,y}} = 0$$
## Diagrama de Forças
Quando estamos analisando a condição de equilíbrio, as forças externas sobre o sistema podem ser representadas atuando sobre um ponto: a posição de uma massa pontual ou, no caso de um corpo extenso, o seu centro de massa. O diagrama vetorial das forças é conhecido como diagrama de forças de corpo isolado. Como a força resultado da soma das forças é nula, é possível representar o diagrama na forma do triângulo de forças. Veja abaixo na imagem o sistema real, o diagrama do corpo isolado no centro de massa e o triângulo de forças.
![[Pasted image 20250513215426.png]]
Com o triângulo de forças é possível obter a Lei dos Senos, vinculando a magnitude dos vetores com os ângulos. Veja abaixo.
$$\frac{F_A}{sen{(\theta)}} = \frac{P}{sen{(90º)}} = \frac{N}{sen{(\beta)}}$$
Onde $\beta = 90º - \theta$. Essa equação é equivalente àquelas obtidas anteriormente. Assim, fica a depender do problema e dos dados disponíveis para escolher qual equação usar.
## Forças de Atrito
Quando dois corpos são colocados em contato, forças em escala molecular são mutuamente exercidas sobre as superfícies. As forças de reação de contato que aparecem quando um objeto exerce pressão sobre outro são o exemplo mais direto desse fenômeno. Essas forças têm origem na repulsão entre os elétrons nas duas superfícies. Existem também forças atrativas na escala molecular, como as forças de van der Waals, que tendem a dificultar o deslizamento das superfícies e constituem a origem das forças de atrito. De acordo com a experiência cotidiana, duas superfícies aparentemente planas em escala macroscópica, mas rugosas, apresentam maior atrito que duas superfícies polidas dos mesmos materiais. No entanto, quando as superfícies
são extremamente planas, em escala nanométrica, observa-se que o atrito aumenta devido à ação das forças atrativas de origem molecular. Isso pode ser verificado com duas placas planas de vidro; quanto menos rugosas e mais limpas se encontrarem, mais difícil será deslizar uma sobre a outra. No modelo de atrito que analisaremos aqui, estaremos considerando sempre o limite de
superfícies planas e polidas.
Abaixo encontra-se uma figura em que é mostrado um bloco, apoiada sobre um plano horizontal, sujeito a uma força de tração horizontal $\vec{T}$. Como o bloco se mantém em repouso, deve existir uma força líquida de atrito estático $\vec{F_A}$ atuando na direção horizontal, compensando a tração.
![[Pasted image 20250513224104.png]]
Experimentalmente, observa-se que:
- A condição de repouso, quando $F_{A} = T$, satisfaz-se até certo limite máximo $F_{A_{máx}}$. Ou seja:
$$F_A \leq F_{A_{máx}}$$
- O limite máximo da força de atrito $F_{A_{máx}}$ depende da natureza das duas superfícies e é diretamente proporcional ao módulo da força normal. Ou seja:
$$F_{A_{máx}} = \micro_{e} N$$
Onde $\micro_{e}$ é o coeficiente de atrito estático, que depende das duas superfícies em contato. Veja abaixo um exemplo.
A resposta do atrito diante da força de tração $T$ está representada graficamente abaixo.
![[Pasted image 20250513224138.png]]
Acima do limite máximo, quando $T > F_{A_{máx}}$, as forças atrativas intermoleculares são vencidas e as superfícies começam a deslizar. Nessas condições, o atrito decai bruscamente e assume um valor aproximadamente constante $F_{c} = \micro_{c} N$: esse é o regime de atrito cinético, sendo que $\micro_{c}$ é o coeficiente de atrito cinético ou dinâmico entre as superfícies.
Quando temos um bloco de massa conhecida sobre um plano inclinado em um ângulo $\theta$, que pode ser variado gradualmente, se aumentarmos o ângulo, a força de atrito, necessária para manter o bloco em repouso, aumenta. Acima de certo valor crítico $\theta_M$, o bloco desliza, indicando que, para esse ângulo, foi atingida a máxima força de atrito que pode ocorrer nesse sistema. Analisando a condição de equilíbrio sobre o bloco, na iminência de deslizar, é possível calcular $F_{A_{máx}}$ e $N$ e, assim, determinar $\micro_e$. Na direção paralela ao plano, $F_{A_{máx}}$ deve ser igual à componente peso:
$$F_{A_{máx}} = m \, g \, sen(\theta_M)$$
Analogamente, na direção vertical, a reação do plano deve compensar a componente do peso:
$$N = m \, g \, cos(\theta_M)$$
Combinando essas equações, obtemos:
$$\micro_e = tan(\theta_M)$$
