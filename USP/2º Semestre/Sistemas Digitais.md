# Gated D Latch 
Esse latch é caracterizado por uma única entrada de dados, chamada D nas representações, e ele guarda o valor dessa entrada, dentro do controle de um sinal de clock.

Para entender o funcionamento dele considere um somador. Ao finalizar a soma, é interessante guardar o valor do resultado e isso até poderia ser feito com um basic latch, conectando o resultado à entrada S e antes de iniciar a soma usar o reset para ficar tudo 0. Porém esse método tem uma falha, ele não leva em conta que antes de obter um resultado final, o valor da saída do somador pode mudar e caso ele mude para 1 (o latch guardaria esse valor) e dele para 0 de novo, o latch não mudaria de valor, sendo necessário usar o reset para voltar a 0, por isso ele não é usado. Já que o basic latch não funciona, poderia usar o Gated SR Latch? Ele até resolveria o problema causado pelo delay até formar o resultado final da soma, pois seria só ajustar o sinal do clock para ele ir para 1 somente depois do tempo máximo necessário para realizar a soma. Além disso seria necessário usar reset toda vez que finalizasse um ciclo de clock, para que ele operasse corretamente no próximo ciclo. Entretanto, isso é um jeito estranho de lidar com o problema do delay e por isso existe o Gated D Latch.

Ele é baseado no Gated SR Latch, porém, ao invés de ter entradas separadas para o Set e Reset, ele possui uma só entrada de dados. Para diferenciar as operações, usa-se uma porta NOT na entrada do Reset e isso também evita o problema que estava presente nos latchs anteriores, que era o do Set e Reset serem 1 e ir para 0, que causava um comportamento imprevisível no circuito, mas agora um sempre será o complemento do outro.

No Gated D Latch, o valor da saída Q acompanha o valor da entrada D enquanto o CLK está em 1. Assim que ele vai para 0, o último valor da entrada fica armazenado até que o CLK volte a ser 1. Por esse comportamento anterior, o Gated D latch é dito "sensível a nível", pois a saída do latch é controlado pelo nível da entrada do clock (os valores lógicos são implementados como nível de tensões baixos e altos).

Abaixo pode-ser ver o esquemático do Gated D Latch, assim como a tabela da verdade dele, o símbolo gráfico e o diagrama de tempo.

[Inserir aqui as imagens]
# Efeitos dos delays de propagação
Anteriormente, foi desconsiderado os efeitos dos delays de propagação, porém em circuitos práticos é necessário considerar esses delays. Para entender os que são esses efeitos considere o Gated D Latch.

Quando se pensa no funcionamento do Gated D Latch, ele guarda o valor que está na entrada D no momento em que o CLK vai de 1 para 0. Ele trabalha como o esperado se o sinal D se manter estável (não mudar de nível lógico) durante a mudança do CLK. Porém não tem como garantir que isso acontece em circuitos reais, o que pode gera resultados imprevisíveis.

Por causa disso, ao projetar um Gated D Latch, visa-se garantir que o valor de D não se altera durante a mudança crítica do sinal de clock. Para isso, considera-se dois intervalos de tempos, conhecidos como: tempo de setup e tempo de hold. O tempo de setup é o tempo mínimo que a entrada D deve se manter estável antes de borda de descida do clock. Já o tempo de hold é o tempo mínimo que a entrada D deve se manter estável após a borda de descida do clock. Assim, garantindo que a entrada não muda durante o tempo de setup e durante o tempo de hold, o Gated D Latch funcionará como o esperado.
# Flip-Flops do Tipo D
Esses flip-flops mudam seu estado somente uma vez a cada ciclo de clock, diferente do Gated D Latch que muda enquanto o CLK for 1. Eles podem ser tanto de borda de subida ou de borda de descida. Eles são ditos sensíveis à borda.
## Flip-Flop Master-Slave do Tipo D
[Imagem do flip-flop tipo D]
Nessa configuração o master muda quando o clock é 1 e o slave quando o clock é 0. Então quando o clock é 1, o master fica se alterando de acordo com a entrada D, mas o slave permanece com o valor que está e quando o clock vai para 0 o slave muda de valor, mas nesse caso será somente uma vez. Daí vem o comportamento do flip-flop que muda somente uma vez por ciclo de clock.

O flip-flop do Tipo D pode ser de borda de subida e de borda de descida. O que muda na configuração do circuito para que haja essa diferença é na forma como o clock é conectado. Quando o clock é ligado diretamente no master e é usado uma porta NOT para conectá-lo no slave, ele é de borda de descida. Já quando o clock é ligado através de uma NOT no master e ligado diretamente no slave, ele é de borda de subida.

Segue abaixo o símbolo dos flip-flops do tipo D.
[Imagem dos símbolos]

## Outros Flip-Flops do Tipo D
Pode-se criar outros circuitos que vão fazer o mesmo papel do master-slave. Abaixo encontra-se o circuito de um Flip-Flop do Tipo D de borda de subida.
[Imagem do flip-flop do Tipo D de borda de subida]
## Flip-Flop do Tipo D com Clear e Preset
É interessante ser capaz de setar o flip flop para 0 ou para 1 diretamente. Por isso, existe o flip-flop com clear e preset. Um uso dele é por exemplo em contadores. Vale mencionar que tanto o clear quanto o preset funcionam quando recebem 0.

Ele pode ser implementado através da configuração master-slave.
[Imagem do circuito]

Ou então, diretamente, como pode ser visto na imagem a seguir.

E o símbolo dele é:
[Imagem do símbolo]

Para ambos os circuitos acima, diz-se que eles são assíncronos pois o clear independe do clock. Porém pode-se criar um circuito em que o clear funciona de acordo com o clock, para isso basta usar uma porta AND na entrada D.
# Flip-Flop do Tipo T
O flip-flop do tipo T tem um funcionamento diferente do que o tipo D. Seu nome (tipo T) vem da palavra em inglês "toggle" que significa trocar. A partir disso, entende-se que seu funcionamento consiste na troca dos valores da saída. Então quando a entrada T é 0 ele mantém o valor e quando é 1 ele muda para o complemento. Esse comportamento de troca é interessante para circuitos contadores.

Ele é implementado usando um flip-flop do tipo D, junto de um outro pequeno conjunto de portas lógicas. Ele pode ser observado abaixo.
[Imagem do tipo T]

E seu símbolo é semelhante ao do tipo D, apenas com a mudança do nome da entrada. Observa-se ele abaixo.
[Imagem do símbolo]

Importante ressaltar que esse flip-flop é sensível a borda. O circuito acima, mais especificamente, é sensível a borda de subida.
# Flip-Flop JK
O flip-flop JK, diferente do tipo T que possui só uma entrada, tem duas entradas: J e K. O seu comportamento é uma junção do SR e do tipo T, para quaisquer entradas em J e K (exceto J = K = 1) ele funciona como um SR, onde J é o S e o K é o R. Já para o caso J = K = 1, ele se comporta como um flip-flop do tipo T, trocando o valor da saída para seu complemento.

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
Ele possui uma entrada serial de dados (entra um dados por vez e vai percorrendo os flip-flop's). O conteúdo de cada flip-flop passa para o próximo a cada borda de subida do clock. Abaixo encontra-se o circuito do registrado shifter simples.
[imagem do circuito]
### Registrador Shifter de Acesso Paralelo
Para alguns circuitos computacionais é interessante transferir n-bits de informações, isso pode ser feito transmitindo todos os bits de uma só vez usando n fios separados. Esse tipo de transferência é conhecida como paralela.

Um registrador shifter de acesso paralelo carrega todos os bits da informação em um só ciclo de clock. Diferente do serial que necessitaria de n ciclos de clock.
TERMINAR
# Contadores
## Contadores Assíncrono
O circuito mais simples pode ser feito com flip-flop's do tipo T, porque a funcionalidade de troca é naturalmente boa para os contadores.
