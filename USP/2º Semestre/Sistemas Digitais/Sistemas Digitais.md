O livro de referência usado nesse estudo foi: 
>Fundamentals of Digital Logic with Verilog Design
>Brown, Stephen D.
# Circuitos Sequenciais
O circuitos sequenciais são aqueles que o valor da saída depende da entrada e do valor do estado anterior do circuito. Geralmente, eles possuem um elemento de memória. Veja abaixo um simples elemento de memória, que não é utilizado para construção de circuitos reais.
![[Sem título4.jpg]]
# Basic Latch
O Basic Latch é um elemento de memória construído com portas *NOR*. Os inputs *Set* e *Reset* fornecem os meios de mudar o estado *Q* do circuito. Um outro jeito, mais comum, de fazer é quando as duas portas *NOR* estão conectadas de modo "cruzado".

Para circuitos sequenciais, ao invés de chamarmos de "tabela da verdade" chamamos de "tabela característica". Além disso, consideramos os delays entre as portas negligenciáveis mas em circuitos reais eles existem.

Veja abaixo o circuito do basic latch.
![[Sem título5.jpg]]
Veja também a imagem do basic latch com a conexão "cruzada".
![[Sem título6.jpg]]
Quando $S = R = 0$ o latch mantém seu estado atual. Já quando $R = 1$ e $S = 0$ o latch é resetado de modo que a saída $Q = 0$ e $\bar{Q} = 1$. Quando $S = 1$ e $R = 0$ o latch é setado, ou seja, a saída $Q = 1$ e $\bar{Q} = 0$. Por último, se $S = R = 1$, então a saída $Q = \bar{Q}= 0$. 

Para o último caso, se mudarmos *S* e *R* simultaneamente para $0$ o circuito irá oscilar entre $0$ e $1$ porque $Q$ e $\bar{Q}$ iguais a 1 força eles irem a $0$ e assim em diante. Mas em circuitos reais, onde há um delay, eles não mudarão simultaneamente para sempre e eventualmente irão se estabilizar em um dos dois estados, mas não sabemos qual. Isso é representado no diagrama de tempo pela linha tracejada.

A mudança ocorre quando o sinal de entrada mudar, mas não controlamos o tempo disso. Então, não controlamos quando o latch pode mudar de estado.
# Gated SR Latch
Nesse tipo de latch, quando o clock é $0$, o *S*'e o *R*' vão ser $0$. Quando o clock /enable for $1$, o *S*'e o *R'* terão os valores do *S* e *R* respectivamente.

Circuitos que usam um controle de sinal são chamados de *gated latches*. Como o circuito tem *set* e *reset*, ele é chamado de *Gated SR Latch*. Quando o clock é $0$, a saída *Q* se mantém a mesma. Já quando o clock é $1$, o circuito se comporta como um basic latch.

Segue abaixo a tabela característica do *Gated SR Latch*.

| CLK | S   | R   | Q($t+1$)             |
| --- | --- | --- | -------------------- |
| 0   | X   | X   | Q($t$) (sem mudança) |
| 1   | 0   | 0   | Q($t$) (sem mudança) |
| 1   | 0   | 1   | 0                    |
| 1   | 1   | 0   | 1                    |
| 1   | 1   | 1   | X                    |
O circuito dele, utilizando portas *NOR* pode ser visto abaixo.
![[Sem título7.jpg]]
O circuito dele, utilizando portas *NAND*, pode ser visto abaixo. Note que nele as portas *S* e *R* são trocadas em relação ao circuito anterior.
![[Sem título8.jpg]]
Por fim, o símbolo gráfico do *Gated SR Latch* pode ser visto abaixo.
![[Sem título9.jpg]]
# Gated D Latch 
Esse latch é caracterizado por uma única entrada de dados, chamada D nas representações, e ele guarda o valor dessa entrada, dentro do controle de um sinal de clock.

Para entender o funcionamento dele considere um somador. Ao finalizar a soma, é interessante guardar o valor do resultado e isso até poderia ser feito com um basic latch, conectando o resultado à entrada S e antes de iniciar a soma usar o reset para ficar tudo 0. Porém esse método tem uma falha, ele não leva em conta que antes de obter um resultado final, o valor da saída do somador pode mudar e caso ele mude para 1 (o latch guardaria esse valor) e dele para 0 de novo, o latch não mudaria de valor, sendo necessário usar o reset para voltar a 0, por isso ele não é usado. Já que o basic latch não funciona, poderia usar o Gated SR Latch? Ele até resolveria o problema causado pelo delay até formar o resultado final da soma, pois seria só ajustar o sinal do clock para ele ir para 1 somente depois do tempo máximo necessário para realizar a soma. Além disso seria necessário usar reset toda vez que finalizasse um ciclo de clock, para que ele operasse corretamente no próximo ciclo. Entretanto, isso é um jeito estranho de lidar com o problema do delay e por isso existe o Gated D Latch.

Ele é baseado no Gated SR Latch, porém, ao invés de ter entradas separadas para o Set e Reset, ele possui uma só entrada de dados. Para diferenciar as operações, usa-se uma porta NOT na entrada do Reset e isso também evita o problema que estava presente nos latchs anteriores, que era o do Set e Reset serem 1 e ir para 0, que causava um comportamento imprevisível no circuito, mas agora um sempre será o complemento do outro.

No Gated D Latch, o valor da saída Q acompanha o valor da entrada D enquanto o CLK está em 1. Assim que ele vai para 0, o último valor da entrada fica armazenado até que o CLK volte a ser 1. Por esse comportamento anterior, o Gated D latch é dito "sensível a nível", pois a saída do latch é controlado pelo nível da entrada do clock (os valores lógicos são implementados como nível de tensões baixos e altos).

Abaixo pode-ser ver o esquemático do Gated D Latch, assim como a tabela da verdade dele, o símbolo gráfico.
![[Sem título10.jpg]]
![[Ciencia-da-Computacao/Imagens/Sem título11.jpg]]

| CLK | D   | Q($t + 1$) |
| --- | --- | ---------- |
| 0   | X   | Q($t$)     |
| 1   | 0   | 0          |
| 1   | 1   | 1          |
# Efeitos dos delays de propagação
Anteriormente, foi desconsiderado os efeitos dos delays de propagação, porém em circuitos práticos é necessário considerar esses delays. Para entender o que são esses efeitos considere o Gated D Latch.

Quando se pensa no funcionamento do Gated D Latch, ele guarda o valor que está na entrada D no momento em que o CLK vai de 1 para 0. Ele trabalha como o esperado se o sinal D se manter estável (não mudar de nível lógico) durante a mudança do CLK. Porém não tem como garantir que isso acontece em circuitos reais, o que pode gera resultados imprevisíveis.

Por causa disso, ao projetar um Gated D Latch, visa-se garantir que o valor de D não se altera durante a mudança crítica do sinal de clock. Para isso, considera-se dois intervalos de tempos, conhecidos como: *tempo de setup* e *tempo de hold*. O *tempo de setup* é o tempo mínimo que a entrada D deve se manter estável antes de borda de descida do clock. Já o *tempo de hold* é o tempo mínimo que a entrada D deve se manter estável após a borda de descida do clock. Assim, garantindo que a entrada não muda durante o tempo de setup e durante o tempo de hold, o Gated D Latch funcionará como o esperado.
# Flip-Flops do Tipo D
Esses flip-flops mudam seu estado somente uma vez a cada ciclo de clock, diferente do Gated D Latch que muda enquanto o CLK for 1. Eles podem ser tanto de borda de subida ou de borda de descida. Eles são ditos sensíveis à borda.
## Flip-Flop Master-Slave do Tipo D
![[Sem título11 1.jpg]]
Nessa configuração o master muda quando o clock é 1 e o slave quando o clock é 0. Então quando o clock é 1, o master fica se alterando de acordo com a entrada D, mas o slave permanece com o valor que está e quando o clock vai para 0 o slave muda de valor, mas nesse caso será somente uma vez. Daí vem o comportamento do flip-flop que muda somente uma vez por ciclo de clock.

O flip-flop do Tipo D pode ser de borda de subida e de borda de descida. O que muda na configuração do circuito para que haja essa diferença é na forma como o clock é conectado. Quando o clock é ligado diretamente no master e é usado uma porta NOT para conectá-lo no slave, ele é de borda de descida. Já quando o clock é ligado através de uma NOT no master e ligado diretamente no slave, ele é de borda de subida.

Segue abaixo o símbolo dos flip-flops do tipo D.
![[Sem título12.jpg]]

## Outros Flip-Flops do Tipo D
Pode-se criar outros circuitos que vão fazer o mesmo papel do master-slave. Abaixo encontra-se o circuito de um Flip-Flop do Tipo D de borda de subida.
![[Sem título13.jpg]]
## Flip-Flop do Tipo D com Clear e Preset
É interessante ser capaz de setar o flip flop para 0 ou para 1 diretamente. Por isso, existe o flip-flop com clear e preset. Um uso dele é por exemplo em contadores. Vale mencionar que tanto o clear quanto o preset funcionam quando recebem 0.

Ele pode ser implementado através da configuração master-slave.
![[Sem título14.jpg]]

Ou então, diretamente, como pode ser visto na imagem a seguir.
![[Pasted image 20241124091616.png]]
E o símbolo dele é:
![[Sem título15.jpg]]

Para ambos os circuitos acima, diz-se que eles são assíncronos pois o clear independe do clock. Porém pode-se criar um circuito em que o clear funciona de acordo com o clock, para isso basta usar uma porta AND na entrada D.
![[Pasted image 20241124091642.png]]
# Flip-Flop do Tipo T
O flip-flop do tipo T tem um funcionamento diferente do que o tipo D. Seu nome (tipo T) vem da palavra em inglês "toggle" que significa trocar. A partir disso, entende-se que seu funcionamento consiste na troca dos valores da saída. Então quando a entrada T é 0 ele mantém o valor e quando é 1 ele muda para o complemento. Esse comportamento de troca é interessante para circuitos contadores.

| T   | Q($t+1$)     |
| --- | ------------ |
| 0   | Q($t$)       |
| 1   | $\bar{Q}(t)$ |

Ele é implementado usando um flip-flop do tipo D, junto de um outro pequeno conjunto de portas lógicas. Ele pode ser observado abaixo.
![[Pasted image 20241124091738.png]]

E seu símbolo é semelhante ao do tipo D, apenas com a mudança do nome da entrada. Observa-se ele abaixo.
![[Pasted image 20241124091949.png]]
Importante ressaltar que esse flip-flop é sensível a borda. O circuito acima, mais especificamente, é sensível a borda de subida.
# Flip-Flop JK
O flip-flop JK, diferente do tipo T que possui só uma entrada, tem duas entradas: J e K. O seu comportamento é uma junção do SR e do tipo T, para quaisquer entradas em J e K (exceto J = K = 1) ele funciona como um SR, onde J é o S e o K é o R. Já para o caso J = K = 1, ele se comporta como um flip-flop do tipo T, trocando o valor da saída para seu complemento.

| J   | K   | Q($t+1$)     |
| --- | --- | ------------ |
| 0   | 0   | Q($t$)       |
| 0   | 1   | 0            |
| 1   | 0   | 1            |
| 1   | 1   | $\bar{Q}(t)$ |

Abaixo podemos ver o circuito do Flip-Flop JK.
![[Pasted image 20241124092058.png]]
Abaixo podemos ver o símbolo desse flip-flop.
![[Pasted image 20241124092333.png]]
Ele é um circuito versátil pois pode ser usado como um elemento de memória, assim como o SR e o do tipo D. Mas ele também pode ser usado como um flip-flop do tipo T, se conectarmos as entradas J e K juntas.
# Diferença entre Latch e Flip-Flop
Ambos os termos são extremamente usados mas eles possuem uma diferença entre si. A primeira diferença é referente ao comportamento quanto ao clock. Enquanto os latch's são sensíveis ao nível do clock, ou seja, se alteram enquanto o nível do clock está 1 e somente o último valor é salvo, os flip-flop's são sensíveis à borda do clock, então o valor dele só se altera no momento que o clock muda de 0 para 1 ou de 1 para 0 (na borda), de modo que ele só se altera uma vez por nível de clock.

Uma outra mudança está na própria definição de cada um dos elementos. O latch é uma conexão de feedback de duas portas NOR ou de duas portas NAND, que pode armazenar 1 bit de informação. Já o flip-flop é um elemento de memória que só pode ter sua saída alterada na borda do clock.
# Registradores
Os registradores são um conjunto de flip-flop's, logo, enquanto um flip-flop armazena 1 bit, o registrador armazena n bits, dependendo somente dos n flip-flops que ele utilizar. O clock é comum para todos os flip-flops do registrador. Agora serão estudados alguns tipos de registradores.
## Registrador Shifter
Um elemento shifter desloca em 1 posições os bits, podendo ser tanto para esquerda (left shifter) quanto para a direita (right shifter). Além disso, um deslocamento para esquerda é equivalente a multiplicar por 2 e um deslocamento para direita é equivalente é dividir por 2.

Então, um registrador que possui essa característica de deslocar valores é conhecido como Registrador Shifter.
### Registrador Shifter Simples
Ele possui uma entrada serial de dados (entra um dado por vez e vai percorrendo os flip-flop's). O conteúdo de cada flip-flop passa para o próximo a cada borda de subida do clock. Abaixo encontra-se o circuito do registrador shifter simples.
![[Pasted image 20241124092515.png]]
### Registrador Shifter de Acesso Paralelo
Para alguns circuitos computacionais é interessante transferir n-bits de informações, isso pode ser feito transmitindo todos os bits de uma só vez usando n fios separados. Esse tipo de transferência é conhecida como paralela.

Um registrador shifter de acesso paralelo carrega todos os bits da informação em um só ciclo de clock. Diferente do serial que necessitaria de n ciclos de clock. Porém dependendo da forma que foi implementado, o registrador pode realizar os dois tipos de transferência.

Abaixo pode-se observar um circuito que faz tanto a transferência em paralelo quanto a em série. Por isso ele tem um *MUX* para escolher qual tipo de entrada irá usar.
![[Pasted image 20241124092859.png]]
# Contadores
Circuitos contadores podem ser feitos usando circuitos somadores/subtratores e registradores. Porém, como só queremos incrementar/decrementar o valor em 1, não é necessário utilizar um design tão complexo.
## Contadores Assíncrono
O circuito mais simples pode ser feito com flip-flop's do tipo T, porque a funcionalidade de troca é naturalmente boa para os contadores.
### Up-Counter com Flip-flop tipo T
Nesse tipo de contador entradas dos clocks são conectados na forma de cascatas (a saída $\bar{Q}$ de um é conectado no clock do outro). A entrada dos flip-flops são conectados à uma constante 1, o que significa que em todo clock eles irão mudar de sinal. 

Esse tipo de circuito tem um delay proveniente dessa conexão do clock. A característica desse delay é que a cada registrador, o ciclo do clock cresce exponencialmente, em potência de 2  (1, 2, 4, ...).

Veja abaixo o circuito e o diagrama de tempo desse contador.
![[Pasted image 20241124093537.png]]
![[Pasted image 20241124093549.png]]
Esses circuitos contam do 0 ao 7 (nesse caso, pois ele tem 3 flip-flops, mas o valor final depende do número de flip-flops).  E em seguida retorna ao 0 e repete a contagem.

O circuito, devido o seu delay, possui um comportamento semelhante ao ripple do somador ripple-carry. Por isso é dito que ele é um contador assíncrono ou ripple counter.
### Down-Counter com Flip-flop Tipo T
Ele possui o comportamento semelhante ao up-counter, incluindo o delay, porém ele conta de 7 até 0 (nesse caso, pois agora o valor de início que depende do número de flip-flops) e então volta ao 7 e repete e contagem.

A diferença do circuito está na conexão dos clocks, que agora o primeiro flip-flop está conectado diretamente ao clock e os outros estão conectados em cascada através da saída $Q$ do flip-flop anterior (no up-counter era a saída $\bar{Q}$). Veja abaixo o circuito e o diagrama de tempo
![[Pasted image 20241124094215.png]]
![[Pasted image 20241124094230.png]]
## Contadores Síncronos
Os contadores assíncronos são simples mas não são muito rápidos. É possível criar um contador muito mais rápido se ativarmos o clock em todos os flip-flops ao mesmo tempos. Por essa característica que eles são denominados síncronos.
### Contadores Síncronos com Flip-flops tipo T
Para um up-counter de n-bits, o estado do flip-flop muda somente quando todos os flip-flops anteriores tem saída $Q = 1$. Por isso usamos os flip-flops tipos T e conectamos as suas entradas de tal forma que para a entrada ser 1, é preciso que todas as outras sejam 1. Veja o circuito desse contador abaixo, assim como seu diagrama de tempo.
![[Pasted image 20241124094753.png]]
![[Pasted image 20241124094804.png]]
### Capacidade de Enable e Clear
É interessante poder impedir a contagem, de modo que mantenha o estado atual, para isso é preciso ter um controlador de sinal Enable. Esse enable controla diretamente a entrada T.

Além disso, muitas vezes é preciso começar a contagem igual a 0. Isso pode ser facilmente atingido se os flip-flops tiverem a opção de clear. O Clear de todos os flip-flops podem ser controlados pelo mesmo sinal de clear.

Veja abaixo o circuito do contador síncrono com Enable e Clear.
![[Pasted image 20241124095140.png]]
## Contador Síncrono com Flip-flops tipo D
Para montar tal circuito com o flip-flop do tipo D, precisamos que as entradas sigam o seguinte formato: $D_{i} = Q_{i} \oplus Q_{i-1}Q_{i-2}... Enable$. Abaixo temos o circuito para um contador de 4 bits.
![[Pasted image 20241124160414.png]]
## Contadores com Carregamento Paralelo
Muitas vezes é desejável poder começar a contagem de algum número específico. Para atingir isso, podemos usar o carregamento paralelo. Fazemos o uso de *MUX* para selecionar se a entrada dos flip-flops será proveniente da contagem feita pelo contador ou de alguma entrada direta. Veja abaixo o circuito
![[Pasted image 20241124160752.png]]
## Sincronização de Reset
As vezes queremos um contador que não seja de alguma potência de 2, por exemplo um contador de módulo 6 (conta de 0 a 5). O jeito mais fácil de obter isso é usando uma porta *AND* para detectar quando o número chega a 5 e nesse momento ele voltara a 0. Nós usamos um contador de carregamento paralelo para montar esse contador e usamos a entrada de *load* dele para resetar. Veja abaixo o circuito.
![[Pasted image 20241124161126.png]]
Uma outra opção, sem usar o carregamento paralelo, é limpar cada flip-flop individualmente através da sua entrada *clear*. Como essa entrada funciona com nível lógico 0, usamos um NAND para detectar quando a saída é 5 e aí limpar o flip-flop.
## BCD Counter
Binary-coded-decimal counters conta os números na base decimal. Ele consiste em dois contadores de módulo 10, um para cada dígito. Veja abaixo o circuito dele.
![[Pasted image 20241124161601.png]]
## Ring Counter
Esse tipo de contador não representa números binários e sim códigos. Nele cada flip-flop atinge o nível 1 para exatamente uma contagem e, enquanto isso, todos os outros são 0. Esse circuito pode ser implementado com um registrador shifter simples. A saída do último registrado realimenta o primeiro registrador, o que cria uma estrutura parecida com um anel. Como só a um único 1 e todo o resto do código é 0, dizemos que é um *one-hot code*.

Ele pode ser implementado diretamente com flip-flops como você pode ver a seguir.
![[Pasted image 20241124162100.png]]
Ou então usar um up-counter de 2 bits junto de um 2-to-4 decoder.
![[Pasted image 20241124162127.png]]
## Contador Johnson
Esse tipo de contador é construído a partir de um ring counter. A diferença dele é que, enquanto no ring counter alimentamos a saída *Q* ao primeiro registrador, no Johnson counter nós realimentamos a saída $\bar{Q}$ ao primeiro registrador. Ele gera uma sequência que tem apenas um bit diferente entre dois códigos consecutivos. Para iniciar o contador é preciso resetar todos os flip-flops. Veja abaixo o circuito desse contador.
![[Pasted image 20241124163359.png]]
# Máquina de Estados Finitos (FMS)
As máquinas de estados são usadas para representar o funcionamento de circuitos sequenciais, ou seja, existe uma sequência (uma saída) que vai ser ativada dependendo das entradas e dos estados, esse último é armazenado através de flip-flops.

Um circuito sequencial consiste de um circuito combinacional de uma rede de memória formadas por elementos de armazenamentos (usualmente Flip-Flops). A rede de memória é o que define o estado atual da máquina de estados.

O circuito sequencial se difere de um circuito combinacional puro na medida em que o próximo estado será definido não só a partir das entradas atuais, como também do estado atual, aumentando enormemente as possibilidades de projeto.
## Diagrama de Transição de Estados
O Diagrama de Transição de Estados é um gráfico orientado usado para representar as funções de transição e de saída de um sistema sequencial. Veja abaixo um exemplo simples de diagrama.![[Pasted image 20241119173546.png]]
Nele os estados são $S_k$ e $S_j$, mas eles podem receber qualquer nome que quisermos para identificar o estado. O que muda o estado é a entrada $X$ e o estado pode fornecer uma saída que é o $Z$.

Agora, vejamos um diagrama de estado completo.
![[Pasted image 20241119173951.png]]
Existem dois modelos que as máquinas de estado podem seguir. Em um deles a saída pode ser indicada dentro de cada estado, já no outro a saída pode ser indicada nos grafos (fora do estado). O comportamento de ambos os modelos é idêntico mas as suas implementações diferem.

É importante ressaltar que cada estado deve ter todas as possibilidades de entradas, caso contrário pode ocorrer algum comportamento imprevisto.
## Máquina de Estado de Mealy
O modelo de Mealy é caracterizado pelos valores de saída dependerem do estado e do valor das entradas. Veja abaixo o circuito de uma máquina de Mealy.
![[Pasted image 20241119180508.png]]
Como a última lógica combinatória pode mudar a qualquer momento, independente do flip-flop, visto que ela depende da entrada pode-se dizer que essa máquina representa um modelo assíncrono. Ou seja, uma alteração na entrada pode causar diretamente uma alteração nos valores da saída.

Na máquina de Mealy, nos arcos são representados os sinais causadores da transição de um 
estado para outro junto dos respectivos valores para a saída. O diagrama dessa máquina de estados é aquele em que as saídas são indicadas fora dos estados. 
![[Sem título0.jpg]]
## Máquina de Estado de Moore
O modelo de Moore é caracterizado pelos valores de saída dependerem apenas do estado do circuito. Veja abaixo o circuito de uma máquina de Moore.
![[Pasted image 20241119181020.png]]
Como a lógica da saída depende somente dos flip-flops, como pode ser observado acima, e eles dependem do sinal de clock (são síncronos), podemos dizer que a máquina de Moore é síncrona. Ou seja, como a saída é sincronizada com os estados, os quais são sincronizados com o clock, temos que as saídas só mudam quando o estado muda.

Na máquina de Moore, somente os sinais de entrada causadores da transição de um estado para outro são representados no arco (nas setas). O diagrama dessa máquina de estados é aquele em que as saídas estão indicadas dentro dos estados.
![[Sem título1.jpg]]
## Como projetar uma máquina de estados?
1. Elaborar o diagrama de estados que interprete fielmente o problema que deseja
2. Opcionalmente, pode-se minimizar o número de estados no diagrama de estados
3. Escrever a tabela de estados, com os estados atuais, próximos estados e saídas
4. Atribuir a cada estado uma combinação de variáveis de estado (flip-flops)
5. Construir a tabela de excitação do tipo de flip-flop utilizado
6. Montar o mapa de Karnaugh para cada uma das entradas dos flip-flops do circuito, com o auxílio da tabela de excitação
7. Obter a equação final de cada entrada para cada um dos flip-flops do circuito a partir da simplificação do mapa de Karnaugh
8. Fazer o mesmo procedimento para as equações das variáveis de saída
9. Elaborar o diagrama lógico do circuito, lembrando que todos os elementos de memória (flip-flops) recebem o mesmo sinal de clock
## Tabela de Transição de Estados
A tabela de transição de estados é uma tabela que possui o estado atual, a entrada, os próximos estados e a saída. A máquina de Mealy e Moore possuem uma diferença quanto a tabela, na parte da saída. A máquina de Moore só possui uma saída, já a máquina de Mealy possui cada possibilidade na parte de saída.

Veja abaixo uma tabela de transição de estados de uma máquina de Moore (os números abaixo de "Próximo Estado" são as possíveis entradas).
![[Sem título2.jpg]]
Agora, veja a tabela de transição de estados de uma máquina de Mealy.
![[Sem título3.jpg]]
O $RST$ ou $Reset$ é a indicação de reset, ou seja, onde será iniciada a máquina quando for utilizado o reset.
## Qual FF escolher?
No caso de FFs JK, a existência de **don't care**, como regra geral, facilita a obtenção de equações mais simplificadas em relação àquelas obtidas para FFs D.

No caso de FFs D, estes exigem metade das conexões entre a lógica combinacional e sua entrada em relação ao que seria exigido com as duas entradas do FFs JK.

Portanto, as vantagens relativas destes dois FFs precisam ser pesadas em cada situação particular, em termos de uma otimização global do circuito.