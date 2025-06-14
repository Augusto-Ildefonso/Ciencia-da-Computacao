# Sistema Computacional
Um sistema computacional é o conjunto de Hardware e Software usado como ferramenta na solução de problemas. Veja abaixo algumas definições:
- Hardware são objetos tangíveis
- Software são objetos não tangíveis (instruções detalhadas -> algoritmos)
- Limites entre hardware e software não são claros: modificados conforme tendências atuais
- Hardware e software são logicamente equivalentes. O software pode ser construído diretamente no hardware
- "Hardware é o software petrificado" Karen P. Lentz
# Arquitetura e Organização
Arquitetura é o conjunto de atributos visíveis ao programador. São conjuntos de instruções, número de bits usados para representação de dados, mecanismos de E/S, modos de endereçamento, etc. Exemplo: há uma instrução para multiplicação?

Organização é como esses atributos estão implementados. São sinais de controle, interfaces, tecnologia de memória. Exemplo: há um hardware específico para a multiplicação ou ela é feita por somas repetidas.

Obs:
- $2^{10}$ -> K (kilo)
- $2^{20}$ -> M (mega)
- $2^{30}$ -> G (giga)
- $2^{40}$ -> T (tera)
- $2^{50}$ -> P (penta)
- $2^{3} \times 2^{30}$ -> 8 GB

Obs: x32 ou x64 é referente ao número de registradores da CPU, esses registradores são os responsáveis por endereçar as posições de memória.
O computador encontra-se no coração da computação. Sem ele as disciplinas da computação seriam um ramo da matemática teórica. Sendo assim, devemos estudar a arquitetura e organização pois:
- Devemos adquirir conhecimentos dos componentes funcionais, suas características, seus desempenhos e suas interações
- É preciso entender a arquitetura de computadores para estruturar programas, para execução eficiente em uma máquina real
- Deve-se entender o relacionamento entre componentes e as implicações desses relacionamentos
Ou seja, não podemos estudar o computador como uma caixa preta.
# Estrutura e Função
Estrutura é a maneira na qual componentes relacionam-se entre si. Já função é a operação de componentes individuais, como parte de uma estrutura.
# Evolução e Questões de Desempenho
## 1ª Geração -> Válvulas
### ENIAC
O ENIAC (Electronic Numerical Integrator And Computer) é o primeiro computador digital eletrônico de grande escala. Ele foi feito por John Presper Eckert e John Mauchly no laboratório de pesquisas balísticas do exército americano, ele ia ser usado num projeto para cálculo de alcance e trajetória de projéteis. Ele iniciou em 1943 e terminou em 1946, muito tarde para todo o esforço da guerra. Ele foi usado até 1955.

Ele foi programado manualmente por chaves (switches), por isso ele era complexo, demorado e suscetível à erros. Para resolver isso é preciso retirar a programação do hardware e inseri-la na memória. Assim a memória principal passou a armazenar programas e dados.
### von Neumann/Turing
O conceito de programa armazenado foi concebido por von Neumann e Turing simultaneamente, por volta de 1945. Ele foi proposto para o EDVAC (Eletronic Discrete Variable Computer). A ideia é o código e dados do programa ficarem armazenados na memória.

Essa nova proposta tem como base:
- A ALU (Arithmetic and Logic Unit) (ULA) trabalhando com dados binários
- Unidade de controle (UC) interpretando instruções vindas da memória e determinando execução
- Registradores armazenados na CPU, com diferentes finalidades e temporário de dados, endereçamento à memória, de instruções, etc
- Dispositivos de E/S, endereçamento à memória, de instruções, entre outros

Esses conceitos foram implementados no IAS em 1952, no Instituto de Estudos Avançados de Princeton.
### Estrutura de uma Máquina de von Neumann
![Imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Ciencia-da-Computacao/refs/heads/master/Imagens/Pasted%20image%2020250227090656.png)
### Estrutura do IAS
![Imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Ciencia-da-Computacao/refs/heads/master/Imagens/Pasted%20image%2020250227090736.png)
## 2ª Geração -> Transistores
Essa geração começou em 1947 com a invenção de transistores por William Shockley el al na Bell Laboratories. Outros pontos importantes dessa segunda geração são: ALU e UC mais complexas, presença de linguagens de programação de alto nível, software de sistema.
### Convertendo as linguagens
Quando temos uma linguagem de alto nível, para poder executar o código dela, o compilador transforma o código em um código em assembly e por fim o assembler converte o assembly para código binário de máquina.
![Imagem](https://github.com/Augusto-Ildefonso/Ciencia-da-Computacao/blob/master/Imagens/Pasted%20image%2020250227091750.png?raw=true)
### Compilador vs Interpretador
Um compilador traduz todo o código-fonte de um programa para linguagem de máquina de uma só vez, gerando um arquivo executável que pode ser executado posteriormente sem a necessidade do código original. Já um interpretador analisa e executa o código linha a linha, sem gerar um executável, o que facilita a depuração, mas pode tornar a execução mais lenta. Enquanto compiladores oferecem maior desempenho final, interpretadores trazem mais flexibilidade durante o desenvolvimento.
## 3ª Geração -> Diminui o tamanho dos transistores
Na terceira geração a série IBM360 (1964) substituiu a série 7000 e não havia compatibilidade entre elas. Com a IBM360 foi criada a 1ª família de computadores:
- Usavam arquitetura do conjunto de instruções similares ou idênticas
- Tinham sistemas operacionais similares ou idênticos
- Velocidade crescente
- Número crescente de portas de E/S e terminais
- Capacidade de memória variada
- Custo variado

Além disso essa geração introduziu o conceito de multiprogramação, ou seja, ter vários programas na memória ao mesmo tempo (time-sharing e troca de contexto).
### DEC PDP - 8
O DEC PDP - 8 foi o primeiro minicomputador, pequeno o suficiente para uso em uma bancada de laboratório. Eles eram mais baratos, custando mais ou menos 16 mil dólares, enquanto o IBM360 custava mais de 100 mil dólares. Eles tinham uma estrutura de barramento.
![Imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Ciencia-da-Computacao/refs/heads/master/Imagens/Pasted%20image%2020250227092545.png)

## 4ª Geração -> Microprocessadores
Em 1971 surgiu o 4004 que foi o 1º microprocessador. Ele tinha todos os componentes da CPU em um único chip e tinha palavras de 4 bits.

Em 1972 surgiu o 8008 que tinha palavras de 8 bits e foi projetado para aplicações específicas, assim como o 4004.

Por fim, em 1974 surgiu o 8080 que foi o primeiro processador de propósito geral da intel.
## 5ª Geração -> Baixa potência e invisível
Em 1981 o governo japonês planejava uma nova geração, baseada em IA. Isso causou um susto no mundo que também correu nessa direção mas fracassou. No fim, a revolução foi outra e silenciosa.

Em 1989, foi lançado o primeiro tablet, GridPad, que tinha tela sensível ao toque. Em 1993, teve o Newton da Apple. Disso eles evoluíram para PDAs (Personal Digital Assistants), que tinham problemas com a interface simples (palm pilot). Por fim, a IBM, em 1990, une o celular com o PDA e cria os smartphones.

Ou seja, houve uma mudança de paradigma, não de arquitetura específica. Em decorrência disso tivemos:
- Computação ubíqua ou pervasiva
- Encolhimento dos CIs e embarcando a computação
## Lei de Moore (1965)
Com o aumento da densidade dos componentes em um chip, Gordon Moore (co-fundador da intel) propôs uma lei que dizia:
- O número de transistores no chip dobrará a cada 18-24 meses
- Custo de um chip permaneceu quase o mesmo

Uma maior densidade de empacotamento implica em menores caminhos entre componentes e maior desempenho.

Além disso, os computadores menores são mais flexíveis, adaptando-se a diferentes serviços e ambientes.
## Projetos de Computadores e Desempenho
Mas como converter transistores em desempenho? A demanda e as organizações atuais requerem um fluxo de execução de instruções constantes. Para isso, são empregadas algumas soluções:
- Mudanças arquiteturais/organizacionais: inserção de pipelines nos processadores
- Mudanças na hierarquia de memória: caches L1 e L2 on board
- Mudanças na microprogramação: predição de desvios, análise do fluxo de dados, execução especulativa
## Balanço do desempenho
A velocidade do processador aumentou muito, assim como a capacidade da memória. Porém a velocidade no acesso à memória cresceu menos que a velocidade do processador, o que gera um grande gargalo no desempenho.
## Soluções para o desempenho de RAM
- Aumentar o número de bits recebidos por acesso
	- Tornar DRAM mais larga em vez de aumentar a capacidade, isso implica em uma mudança de barramentos
- Mudar interface da DRAM, incluindo cache na pastilha
- Reduzir frequência de acessos à memória, usando estruturas de caches mais complexas, tanto na DRAM quanto no processador
- Aumentar a largura de banda dos barramentos, tornando-os mais velozes e colocando uma hierarquia de barramentos
## Dispositivos de E/S
- Periféricos com demandas intensas de E/S
- Grandes demandas de vazão de dados
- Processadores podem tratar disso
- Problema de movimentar dados
- Soluções:
	- Caching
	- Buffering
	- Barramentos de interconexão de maior velocidade
	- Estruturas de barramentos mais elaboradas 
## A chave é o balanço
- Componentes do processador
- Memória Principal
- Dispositivos de E/S
- Estruturas de Interconexão
## Feedback
Evolução dos computadores foi marcada por:
- maior velocidade dos processadores
- diminuição do tamanho dos componentes
- maior capacidade (densidade) das memórias
- maior capacidade e velocidade de E/S
Velocidades maiores vêm da diminuição do tamanho:
- menores distâncias entre os componentes
- ganhos reais de desempenho vêm de mudanças na organização
	- pipeline, execução paralela, especulativa e predição de desvios
Balanceamento no desempenho dos componentes:
- Ex.: ganhos na velocidade do processador podem ser prejudicados por atrasos devido à
velocidade da memória 
	- possíveis soluções: cache, barramentos mais largos, entre outras
# Conceitos Gerais
## Arquitetura de von Neumann
A arquitetura proposta por Von Neumann é composta por um conjunto de componentes lógicos básicos mais programação.
Veja abaixo a visão hierárquica do hardware e das camadas de software.
![[Pasted image 20250402185625.png]]
Ela tem três pontos importantes:
- Dados e instruções estão armazenados na memória
- A memória é endereçada pela posição
- A execução das instruções é sequencial
## Hardware de propósito geral
Em um hardware de propósito geral, o programa determina uma sequência de passos, onde cada passo faz uma operação aritmética ou lógica e cada operação requer sinais de controle diferentes.
## Função da unidade de controle
Para cada operação, um código único é fornecido, por exemplo: ADD, MOVE, etc. A função da unidade de controle interpretar o código e gerar os sinais de controle que executarão a instrução requerida.
## Programa
O programa é uma sequencia de passos que tem operações:
- lógica/aritmética
- carregar/armazenar dados na memória
- controle (muda a sequencia de execução)

Cada operação requer um conjunto de sinais de controle.
![Imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Ciencia-da-Computacao/refs/heads/master/Imagens/Pasted%20image%2020250306084327.png)
Cada operação tem um só código. A unidade de controle gera todos os sinais de controle para que as instruções sejam executadas corretamente.
## Componentes
- CPU -> UC + ULA + Bloco de registradores
- Memória -> armazena dados e instruções (fornecer instruções e operandos para execução, armazenar resultados fora da CPU)
- Dispositivos de E/S -> fazem a comunicação com o usuário (mundo exterior) e permite inserir dados e instruções no computador, assim como enviar resultados para fora do computador
## Ciclo de instrução
O objetivo do ciclo de instrução é buscar a instrução que está na posição apontada por PC e executá-la. Ele é composto das seguintes etapas:
- Busca (busca implica memória) da instrução
- Execução da instrução (é dividida em)
	- Decodificação (UC)
	- Execução (ULA)
## Ciclo de busca
Esse ciclo busca a informação na memória. O PC aponta a próxima instrução a ser executada (ele não conta programa algum, apenas aponta para a próxima instrução). O MAR (é o registrador que faz a interface do PC com o barramento) recebe o que está no PC (MAR = PC). O MBR recebe o valor da posição de memória que o MAR estava apontando (MBR = memória(MAR)). O IR recebe o que está no MBR (IR = MBR). Por fim, PC recebe ele mesmo mais um valor que varia (por exemplo, PC = PC + 1, a não ser que a próxima instrução não esteja armazenada na posição seguinte, ou seja, há uma instrução de desvio). MBR significa memory buffer register (as imagens são da mesma arquitetura só que possuem algumas coisas q tem em uma e na outra não).
![Imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Ciencia-da-Computacao/refs/heads/master/Imagens/ciclo%20de%20busca.png)
![Imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Ciencia-da-Computacao/refs/heads/master/Imagens/aula_11_03_2025%201.png)
Opcode é entrada para unidade de controle.
$$PC \longrightarrow MAR \longrightarrow bar(endereço) \longrightarrow memória \longrightarrow bar(dados) \longrightarrow MBR \longrightarrow IR \longrightarrow PC + 1$$
Pode ter um acumulador que é conectado com o MBR.
## Ciclo de execução
A UC recebe o opcode (nem a UC nem o IR quebra em opcode e endereço/dado, ele já chega assim no IR) <span style="color:rgb(0, 132, 255)">decodifica</span> o opcode e determina quais ações são necessárias, ou seja, a UC configura (gera) os sinais de controle de acordo com a instrução. Em seguida, <span style="color:rgb(0, 132, 255)">executa</span> a instrução. A execução tem quatro possibilidades:
- Execução processador-memória: são aquelas que fazem transferência de dados entre o processador e a memória (load e store)
- Execução processador-E/S
- Execução de processamento de dados: qualquer operação aritmética
- Execução de controle: jumps por exemplo
O MBR em ciclo de execução (ou seja, quando ele vai receber dado) envia o valor para o IR e o IR envia para o MAR, ou então ele pode enviar para o próprio acumulador.
**Decodificação:**
$$IR \longrightarrow UC \longrightarrow sinais\,de\,controle$$
**Execução:** a execução tem vários sinais de controle, dependendo da instrução que ele tem que fazer. Por exemplo, sinal para habilitar o acumulador, para fazer operação na ULA, para a ULA escrever no AC (acumulador), etc.

# Arquitetura RISC-V
## CISC vs RISC
CISC significa *Complex Instruction Set Computer* e ela tem uma grande quantidade de instruções e elas são complexas, isso quer dizer que ela tem instruções de tamanhos variados e vários tipo de instruções. O CISC tem ISA (instruction set architecture) complexo, pois tem muitas instruções, muitos formatos e instruções de tamanhos diferentes.
Já RISC significa *Reduced Instruction Set Computer* e ela tem poucas instruções e elas são mais simples, isso quer dizer que tem poucos tipos de instruções, com todas do mesmo tamanho e só as instruções de carga e armazenamento acessam a memória. O RISC tem ISA simples, pois tem poucas instruções, poucos formatos e instruções de mesmo tamanho. Além disso, ela é uma arquitetura load/store.
## História da arquitetura RISC
Na década de 1980 tivemos os primeiros computadores RISC. Em 1980, foi desenvolvido o IBM 801, que é o antecessor do IBM PC/RT (RISC Technology). Entre 1980 e 1981, Patterson e Séquin desenvolveram o Berkeley RISC I e RISC II, que inspirou o projeto do processador SPARC, da SUN Microsystem. Por fim, em 1981 foi desenvolvido o Stanford MIPS, projetado por Hennessy, que originou a MIPS Computer Systems.
## RISC-V
A arquitetura RISC-V tem um conjunto de instrução universal e ela é uma arquitetura aberta e de propósito geral. Isso significa que ela é projetada para ser flexível e capaz de executar uma ampla variedade de tarefas computacionais, ao contrário de arquiteturas especializadas que são otimizadas para funções específicas. Ela tem vários requisitos:
- Atender todos os tamanhos de processadores
- Funcionar bem para uma grande quantidade de softwares e linguagens de programação
- Acomodar tecnologias de implementação
- Ser eficiente para todo tipo de microarquitetura (organização)
- Ser estável (ISA base não deve mudar)
Atualmente ela é mantida pela fundação RISC-V, que é uma fundação aberta e sem fins lucrativos.
## Características da arquitetura
A RISC-V tem uma arquitetura de 32 bits (atualmente existem arquiteturas mais recentes de 64 bits). Ela tem um banco de registradores inteiro de 32 bits e um banco de registradores de ponto flutuante de 32 bits.![Imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Ciencia-da-Computacao/refs/heads/master/Imagens/Pasted%20image%2020250313083736.png)
## Registradores
![Imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Ciencia-da-Computacao/refs/heads/master/Imagens/Pasted%20image%2020250313083850.png)
Os registradores que usaremos são:
- x0 -> zero
- x1 -.> ra: return address
- x2 -> sp: stack pointer
- x5/x6/x7 -> t0/t1/t2: temporário
- x8/x9 -> s0/s1: salvo
- x10/x11 -> a0/a1: argumento de função/retorno de função
- x12-x17 -> a2-a7: argumento de função
- x18-x27 ->s2-s11: salvo
- x28-x31 -> t3-t6: temporário
Por convenção, o valor dos registradores salvo, quando entrar em uma função e sair dela tem que ter o mesmo valor que tinha antes, ou seja, a convenção é que registrador salvo não deve ser alterado por funções, porém dependendo o caso, é possível alterar o valor dele usando pilhas e depois voltando ao valor inicial.
Na arquitetura RISC-V a memória é endereçada a byte, ou seja, a menor unidade endereçável é 1 byte (a outra opção sem ser a byte é a palavra, por exemplo palavras de 32 bits, ou 4 bytes, só é possível endereçar de 4 em 4).
![Imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Ciencia-da-Computacao/refs/heads/master/Imagens/Pasted%20image%2020250313090054.png)
Os outros tipos de dados são:
- Byte: 1 byte
- Halfword: 2 bytes
- Word (palavra): 4 bytes
- Float: 4 bytes (Ponto flutuante)
- Double: 8 bytes (Ponto flutuante)
- String: não tem um valor definido
## Conjunto de instruções
A arquitetura RISC-V possui diversos conjuntos de instruções:
- RV32I: conjunto base (32 bits) com instruções para operações em inteiro
- RV32M: instruções de multiplicação e divisão
- RV32F e RV32D:  instruções de ponto flutuante
- RV32A: Instruções atômicas
- RV32C: Instruções compactas, de 16 bits
- RV32V: Instruções vetoriais (SIMD)
## Arquitetura Load/Store
Os valores tem que ser carregados nos registradores antes de realizar as operações. Não há instruções que operam diretamente em valores na memória.
## Estrutura do Código
![Imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Ciencia-da-Computacao/refs/heads/master/Imagens/Pasted%20image%2020250313091306.png)
## Diretivas
Diretiva é tudo que é importante para a geração/carga do programa na memória, pois elas vão indicar em que parte da memória carregar as informações. Todas as diretivas começam com um . e não possuem correspondência no código binário gerado, elas servem só para direcionar o montador.
~~~assembly
.data
# dados estáticos do seu código
# O hashtag é comentário em assembly

.text
# código
~~~
As diretivas dos tipos de dados são:
- Byte -> .byte
- Halfword -> .half
- Word -> .word
- Float -> .float
- Double -> .double
- String -> .asciz
Outras diretivas são:
- .globl: ele diz qual é o ponto de entrada do código (onde é o main do programa), ou seja, onde ele quer começar o programa 
## Hello World em Assembly
~~~assembly
	.data
hello_msg: .asciz "Hello World!" # hello.msg é um label que referencia o primeiro byte da string
	.text
	.globl main
main: la a0, hello_msg
      li a7, 4 # imprimir string
      ecall
      li a7, 10
      ecall
~~~
Pseudo instrução: é uma instrução que não existe implementação na arquitetura, mas depois o montador vai converter ela para instruções que existem. Exemplos:
- la -> local address, ela carrega no registrador o endereço do 1º byte da string definida no label.
- li -> load immediate, ela carrega no registrador o valor imediato definido na instrução. Essa instrução é convertida para ``addi a7, zero, 4``.
O `ecall` é uma chamado ao sistema, essa instrução é usada para transferir o controle para o SO para ele realizar uma operação de entrada e saída. Veja abaixo os códigos do ecall:
![[Pasted image 20250313094053.png]]
Os registradores `a2-a7` vão armazenar os parâmetros. Nesse caso o `a7` tem o código da função a ser executada pela ecall. O `a7` é um parâmetro da função a ser executada pelo ecall e o código 4 pega o endereço `a0` do primeiro byte da string a ser impressa
## Acesso a Memória
A arquitetura RISC-V é endereçada a byte e com palavra de 32 bits. Dizer que ela é endereçada a byte significa que os endereços iniciais de cada palavra começam sempre em múltiplos de 4. Veja abaixo a imagem para entender melhor.
![[Pasted image 20250318105436.png]]
### Ordenação
A ordenação define como um valor grande (no caso uma palavra de 4 bytes) será quebrada em vários pedaços pequenos (no caso em bytes) para colocar na memória. Dessa forma, o conceito de ordenação só tem sentido quando se está falando de memória. A ordenação pode ser de dois tipos: big-endian e little-endian.
O big-endian armazena o byte mais significativo no menor endereço. Já o little-endian armazena o byte mais significativo no maior endereço. A RISC-V é little-endian. Em outras arquiteturas, como a MIPS, ela é bi-endian, ou seja, ela tem a capacidade de comutar entre as duas ordenações, de acordo com a máquina hospedeira.
![[Pasted image 20250318112103.png]]
### Diretiva .align
Essa diretiva enquadra os dados na memória de modo que ele se enquadre em $2^{n}$ bytes. Exemplos:
- .align 2: utilizado para alinhar valores inteiros de 32 bits ($2^2 = 4$ bytes)
- .align 0: utilizado para alinhar caracteres ($2^{0} = 1$ byte)
Devemos colocar o ``.align 2`` depois do `.text` e antes do `.globl` pois as instruções são words.
### Instruções para acessar a memória
A função `load` (carga) carrega dados da memória principal para o banco de registradores. As instruções começam com `l` e são seguidas por uma letra que especifica a quantidade de bytes que serão carregados:
- w: word (4 bytes)
- b: byte (1 byte)
- f: float (4 bytes)
O formato da instrução é `lw reg_destino, deslocamento (reg_base)`. Ela armazena em reg_destino o conteúdo da memória do endereço reg_base.
### Store (armazenamento na memória)
Essas instruções armazenam dados do banco de registradores na memória principal. As intruções começam com `s` e seguem a mesma regra das instruções de carga. Formato: `sw <reg_origem>, deslocamento (reg_base)`. Ela armazena o conteúdo do `reg_origem` no endereço de memória (`reg_base`) mais deslocamento.
### Str_cpy Estático
![[Pasted image 20250325103034.png]]
O `0` no fim é o terminador de strings, ou seja, o `\0`.
Parte do código:
~~~assembly
		.data
str_src: .asciz "Oi mãe!!"
str_dst: .space 11

loop:
		la s0, str_src
		la s1, str_dst
		lb t0, 0(s0)
		sb t0, 0(s1)
		addi s0, s0, 1
		addi s1, s1, 1
		bne t0, zero, loop
~~~
O `.space` reserva na memória o número de bytes que foi passado para ele.
### Alocação dinâmica
A alocação dinâmica é o serviço 9 (sbrk) da `ecall`. O parâmetro é:
- ``a0``: número de bytes a ser reservado na heap
O retorno é:
- ``a0``: endereço do 1º byte endereçado
### Str_cpy Dinâmico
![[Pasted image 20250325113014.png]]
~~~assembly
		.data
		.align 0
str_src:	.asciz "Oi mae!!"
		.align 2
	p:		.word # ponteiro
		.text
		.align 2
		.globl main
		
main:		# Contar o número de caracteres da string
		# t1: contador
		li t1, 0
		# s0: endereço
		la s0, str_src
		# t0: caracter lido
loop_tam:	lb t0, 0(s0)
		addi s0, s0, 1 # incrementa a posição de memória (avança para o próximo caracter)
		addi t1, t1, 1 # incrementa o contador
		bne t0, zero, loop_tam # branch para inicio do loop caso a posição não seja 0
		
		# Alocação dinâmica na heap
		li a7, 9
		# Tamanho em a0
		add a0, t1, zero
		ecall # a0 = endereço do 1º byte reservado na heap
		# Tudo acima foi para reservar a memória na heap, agora temos que colocar no ponteiro o endereço do primeiro byte (da heap) que tem o conteúdo alocado

		# Armeanar o endereço do 1º byte (a0) na posição de memória p
		la t2, p
		# Escrever em t2 o conteúdo de a0
		sw a0, 0(t2) # s -> store, w -> word
		
		# Preparar para copiar
		# s0 = endereço string origem
		la s0, str_src
		# s1 = endereço string destino
		la t2, p
		lw s1, 0(t2)
		
		# Fazer a cópia
loop_cpy:	lb t0, 0(s0)
		sb t0, 0(s1)
		# Avança na string
		addi s0, s0, 1
		addi s1, s1, 1
		bne t0, zero, loop_cpy
		
		# Imprimir a string copiada
		li a7, 4
		# a0 = endereço da string a ser impressa
		la t2, p
		lw a0, 0(t2)
		ecall
		# Encerramos
		li a7, 10
		ecall
~~~
## Função e Procedimento
A princípio procedimento não retorna nada, já função retorna algo. Será usada uma convenção em que os parâmetros das funções estarão sempre entre `a0` e `a7` e o retorno estará sempre em `a0` ou `a1`.
Para fazer funções precisamos de duas instruções: ``jal`` e `jr`. A `jal` significa jump and link. A sintaxe é: `jal <reg>, label`. Ela desvia para o label e salva PC + 4 (ou seja, salva o endereço da próxima instrução no `<reg>`). A `jal` é como se fosse a chamada pois ela que desvia. A `jal` faz um desvio incondicional, salvando o endereço de memória da próxima instrução no `ra` (convenção). Já a `jr` significa jump register e ela faz o PC = `<reg>`, ou seja, PC aponta para a próxima instrução (como se fosse o retorno). A sintaxe dela é: `jr <reg>`. A `jr` faz um desvio incondicional para o endereço armazenado em $ra$ (convenção).
O registrador ra é sempre utilizado para armazenar o endereço de retorno. Então, o que acontece quando se tem chamadas de procedimentos aninhadas? Deve-se utilizar a pilha para salvar o valor do registrador ra.
### Procedimentos
Para realizar procedimentos:
1. Colocar os parâmetros em um local onde o procedimento possa encontrá-lo
2. Transferir o controle para o procedimento
3. Adquirir os recursos de armazenamento necessários para o procedimento
4. Realizar a tarefa desejada
5. Colocar o valor de retorno em um local onde o programa que chamou possa acessá-lo
Temos a seguinte convenção para os registrados:
- `a0` e `a1`: argumento de funções e valores de retorno
- `a2` a `a7`: argumento de funções
- `ra`: endereço de retorno
### Fatorial com função
~~~assembly
		.data
		.align 0
str_entrada:	.asciz "Digite um número: "
str_saida:	.asciz "Fatorial calculado: "
		.text
		.align 2
		.globl main
main: 		# imprime a string de entrada
		li a7, 4
		la a0, str_entrada
		ecall
		# lê o valor digitado
		li a7, 5
		ecall
		# salva o valor em s0
		add s0, zero, a0
		# chamando função
		jal fatorial
		# Salva valor retornado em s1
		add s1, zero, a1
		# imprimir str_saida
		li a7, 4
		la a0, str_saida
		ecall
		# imprimir valor
		li a7, 1
		add a0, zero, s1
		ecall
		# encerrar
		li a7, 10
		ecall
		
		# Função fatorial
		# a0 -> nº a ser calculado
		# a1 -> valor calculado
		# retorno inicial
fatorial:	addi a1, zero, 1
		# contador
		add t0, zero, a0
loop_fat:	beq t0, zero, sai_loop_fat
		mul a1, a1, t0
		addi t0, t0, -1
		j loop_fat
sai_loop_fat:	jr ra

~~~
Obs: quando lemos uma string e definimos no a1 o tamanho de temos três possíveis opções:
- A string ocupa todo o espaço -> sem `\n` e sem `\0`
- A string não ocupa todo espaço e sobra só 1 caractere -> tem `\n` e não `\0`
- A string não ocupa todo espaço e sobra 2 ou mai caracteres -> tem `\n` e `\0`
# RISC-V: Conjunto de Instruções
O conjunto de instruções, também chamado de ISA (Instructions Set Architecture), define quais são as instruções implementadas na arquitetura. Ele também define a quantidade e função dos registradores, por exemplo, arquiteturas 32 bits (como é o caso da que estamos trabalhando: RV32I ou Risc-V 32 Bits Integer Architecture) tem 32 bits no bloco de registradores, podendo ser endereçado $2^5$ bits.
Veja abaixo uma visão geral das instruções.
![[Pasted image 20250516115149.png]]
Em todas as instruções, o opcode vai estar nos 7 primeiros bits (0 a 6). Como temos só 7 bits, estamos limitador a 128 instruções. Mas para contornar isso usamos além do campo do opcode, o campo F3 para especificar a operação, ampliando a capacidade de instruções.
O montador vai dividir os bits em grupos de 4 e converter para hexadecimal, ficando por exemplo `0x00012903` e assim em diante. Vale ressaltar que ele não respeita a divisão dos bits entre os registradores. Cada registrador tem um valor, exemplo o `s2` é `x18` e aí salvamos o 18 em binário nos registradores.
Uma das características das arquiteturas RISC é que a maioria das instruções possuem tamanhos
iguais. As vantagens disso são:
- Simplicidade no pipeline de execução:
    - Como todas as instruções têm o mesmo tamanho (por exemplo, 32 bits), a decodificação é mais simples.
    - Permite pipelining eficiente, pois cada estágio do pipeline sabe exatamente quantos bits esperar e como interpretar a instrução.
- Maior previsibilidade:
    - O fluxo de controle e os saltos (jumps/branches) são mais fáceis de prever e implementar, o que melhora a eficiência do hardware e reduz o risco de erros.
- Facilidade na busca e decodificação de instruções:
    - A unidade de busca de instruções (instruction fetch) pode buscar instruções de forma mais rápida e previsível, pois todas têm o mesmo tamanho.
- Paralelismo e escalabilidade:
    - Favorece técnicas como execução fora de ordem (out-of-order execution) e execução superescalar, já que o controle sobre múltiplas instruções simultaneamente é mais fácil com instruções uniformes.
- Facilidade de análise e otimização por compiladores:
    - Compiladores conseguem gerar código mais eficiente e otimizado, com melhor utilização do conjunto reduzido e uniforme de instruções.
Já as desvantagens são:
- Desperdício de espaço (ineficiência na codificação):
    - Nem todas as instruções precisam de 32 bits. Instruções simples (como `ADD R1, R2, R3`) poderiam ser representadas com menos bits.
    - Isso pode levar a código mais longo (em bytes) comparado a arquiteturas com instruções de tamanho variável (como CISC).
- Menor densidade de código:
    - O tamanho fixo pode significar que programas RISC ocupam mais memória que equivalentes CISC (ex: x86), especialmente em programas pequenos ou com muitas instruções simples.
    - Pode afetar a eficiência do uso de cache e a largura de banda de memória.
Primeiramente podemos dividir nossas instruções em classes, veja abaixo.
## Classes de Instruções
Temos 5 classes de instruções:
- Instruções Aritméticas e Simples
	- add, addi, sub
- Instruções de Operandos Lógicos
	- and, andi, or, ori
- Instruções de Uso da Memória
	- lw, lh, lb, sw, sh, sb
- Instruções de Controle de Fluxo
	- beq, bne, jal
- Instruções de comparação
	- slt
## Tipos de Instruções
A RISC-V tem 6 tipos de instruções:
- Tipo R - Register
- Tipo I - Immediate
- Tipo S - Store
- Tipo B - Branch
- Tipo U - Upper
- Tipo J - Jump
A imagem abaixo mostra a divisão dos bits de cada tipo de instrução.
![[Pasted image 20250510121733.png]]
Vamos agora aprofundar em cada tipo de instrução
### Tipo R (Register)
![[Pasted image 20250510121831.png]]
![[Pasted image 20250408103739.png]]
Elas são usadas para operações aritméticas e lógicas entre registradores
O campos dela são:
- opcode: código da operação
- rd: endereço do registrador destino
- funct3: auxílio para definição da operação
- rs1: endereço do primeiro registrador de origem
- rs2: endereço do segundo registrador de origem
- funct7: auxílio para definição da operação
Um exemplo de instrução do tipo R é `add <rd>, <rs1>, <rs2>`:
- `add s2, s1, s0`
- opcode: 0110011
- rd: s2 (10010)
- funct3: 000
- rs1: s1 (01001)
- rs2: s0 (01000)
- funct7: 0000000
![[Pasted image 20250510122153.png]]
Outros exemplos: `add`, `sub`, `sll`, `slt`, `xor`, `or`, `and`
### Tipo I (Immediate)
![[Pasted image 20250510122416.png]]
![[Pasted image 20250408104633.png]]
Elas são usadas para operações com constantes imediatas, carregando dados e com chamadas ao sistema.
Os campos dela são:
- opcode: código da operação
- rd: endereço do registrador destino
- funct3: auxílio para definição da operação
- rs1: endereço do primeiro registrador de origem
- imm: valor imediato
Um exemplo de instrução do tipo I é `lw <rd>, Imm(rs1)`:
- `lw s2, 0(sp)`
- opcode: 0000011
- rd: s2 (10010)
- funct3: 010
- rs1: sp(00010)
- imm: 000000000000
![[Pasted image 20250510122716.png]]
Outros exemplos: `addi <rd>, <rs1>, Imm`, `andi`, `ori`, `lb`, `lh`, `lw <rd>, imm(<rs1>)`, `jalr`, `ecall`.
A combinação de f3 + opcode que diz se é `lw` ou `lb`, etc. 
### Tipo S (Store)
![[Pasted image 20250510122739.png]]
![[Pasted image 20250408105810.png]]
Elas são usadas para instruções de armazenamento (store) na memória
Os campos dela são:
- opcode: código da operação
- imm\[4:0] e imm\[11:5]: valor imediato
- funct3: auxílio para definição de operação
- rs1: endereço do primeiro registrador de origem
- rs2: endereço do segundo registrador de origem
Um exemplo de instrução do tipo S é `sw <rs2>, imm(<rs1>)`:
- `sw s2, 0(sp)`
- opcode: 0100011
- imm\[4:0] e imm\[11:5]: 00000 0000000
- funct3: 010
- rs1: sp(00001)
- rs2: s2(10010)
![[Pasted image 20250510123426.png]]
Outros exemplos: `sb`, `sh`, `sw`.
É importante para a arquitetura que os registradores estejam sempre nas mesmas posições, então o `rs1` sempre vai estar entre 15 e 19, o `rs2` entre 20 e 24 e assim em diante. Por isso, o immediate é dividido em duas partes, de modo a não alterar as posições dos registradores.
A combinação de f3 + opcode que diz se é `sw` ou `sb`, etc.
### Tipo B (Branch)
![[Pasted image 20250510124618.png]]
![[Pasted image 20250408114559.png]]
Elas são usadas para instruções de desvio condicional (branches).
Os campos dela são:
- opcode: código da operação
- imm\[4:0], imm\[11], imm\[10:5] e imm\[12]: valor imediato
- funct3: auxílio para definição da operação
- rs1: endereço do primeiro registrador de origem
- rs2: endereço do segundo registrador de origem
Um exemplo de instrução do tipo B é `beq <rs1>, <rs2>, imm`:
- `beq s1, s0, 4`
- opcode: 1100011
- imm\[4:1], imm\[11], imm\[10:5] e imm\[12]: 000000000100
- funct3: 000
- rs1: s1 (01001)
- rs2: s0 (01000)
![[Pasted image 20250510124949.png]]
Outros exemplos: `beq`, `bne`, `blt`, `bge`.
O immediate é o número de meias-palavras que tem do branch até onde é para pular. Como trabalhamos com half-words, o próprio montador, quando gera o assembly, vai colocar o valor 0 no início do valor imediato para multiplicá-lo por 2 e então obter o número de bits. E trabalhamos com half-words pois isso dobra a capacidade de representação, quando comparado com bytes.
O 12 tem que estar no final pois o último bit tem que ser o de sinal. Por causa disso, não há espaço para o 11 e por isso colocamos ele no primeiro bit do immediate.
### Tipo U (Upper)
![[Pasted image 20250510125221.png]]
![[Pasted image 20250408114526.png]]
Elas são usadas para carregar constantes grandes nos registradores
Os campos dela são:
- opcode: código da operação
- rd: endereço do registrador destino
- imm\[31:12]: valor imediato
Um exemplo de instrução do tipo U é ``lui <rd>, imm``:
- `lui s0, 0x01234`
- opcode: 0110111
- rd: s0(01000)
- imm\[31:12]: 00000001001000110100
![[Pasted image 20250510125428.png]]
Outros exemplos: `lui`, `auipc`
### Tipo J (Jump)
![[Pasted image 20250510130037.png]]
Elas são usadas para instruções de salto incondicional com endereço absoluto relativo.
Os campos dela são:
- opcode: código da operação
- rd: endereço do registrador de destino
- imm\[20], imm\[10:1], imm\[11] e imm\[19:12]: valor imediato
Um exemplo de instrução J é `jal`:
- `jal s0, -4`
- opcode: 1101111
- rd: s0 (01000)
- imm\[20], imm\[10:1], imm\[11] e imm\[19:12]:1 1111111100 1 11111111
# RISC-V: Monociclo
A arquitetura RISC-V tem os seguintes componentes:
- Banco de registradores
![[Pasted image 20250514175359.png]]
- Unidade de controle
- ULA
![[Pasted image 20250514175446.png]]
- Memória
![[Pasted image 20250514175427.png]]
- Entrada/Saída
- Multiplexadores
- Entre outros...
![[Pasted image 20250514175524.png]]
Para interconectar todos esses componentes temos dois tipos de linha:
- Linha de dados: interconexões definidas pelo caminho de dados
- Linha de controle: definidas pela unidade de controle de acordo com a fase da instrução e o que a instrução tem que fazer (decodificação)
Temos múltiplas implementações para uma mesma arquitetura. São elas:
- Monociclo (single cycle): cada instrução (busca, decode e execução) é executada em um ciclo de clock. O tamanho do ciclo de clock é o tamanho da instrução mais longa
![[Pasted image 20250514175922.png]]
- Multiciclo (multicycle): a execução da instrução é dividida em uma série de passos menores
- Pipeline: a execução de cada instrução é dividida em uma série de passos menores e partes de múltiplas instruções são executadas ao mesmo tempo
## Caminho de Dados
### Metodologia do Clocking
Ela utiliza uma metodologia de sincronização acionada por transição. Ou seja, quaisquer valores armazenados em um elemento lógico sequencial são atualizados apenas em uma transição de clock.
![[Pasted image 20250514175717.png]]
### Conjunto de instruções básico
Temos as seguintes instruções:
- Instruções de memória: `lw` e `sw`
- Instruções aritméticas: `add` e `sub`
- Instruções lógicas: `or`, `and` e `slt`
- Instruções de desvio: `beq`
### Busca das instruções
![[Pasted image 20250514180122.png]]
### Execução das instruções do Tipo R
O passo-a-passo é:
- Leitura de dois registradores
- Realização da operação aritmética/lógica
- Escrita do resultado no registrador
- Uso dos componentes:
	- Banco de registradores
	- ULA
![[Pasted image 20250514180414.png]]
### Execução das instruções Load e Store
O passo-a-passo da Load é:
- Leitura do operando a partir dos registradores (registrador origem e valor imediato)
- Calcula o endereço usando um deslocamento de 12 bits (uso da ULA, com o componente de geração de valor imediato)
- Lê a memória e atualiza o registrador
O passo-a-passo da Store é:
- Leitura dos operandos a partir dos registradores (dois registradores origem e um valor imediato)
- Calcula o endereço usando um deslocamento de 12 bits (uso da ULA, com o componente de geração do valor imediato)
- Escreve o valor do registrador na memória
![[Pasted image 20250514182510.png]]
### Execução das instruções de desvio
Um exemplo de instrução de desvio é `beq t1, t2, offset`. O endereço destino é relativo a próxima instrução, logo, $endereço \, destino \, = PC  + byteoffset$. O offset já foi deslocado de 1 bit pela unidade de geração de valor imediato.
O passo-a-passo é:
- Leitura dos operandos a partir do banco de registradores
- Comparação dos dois através da ULA (subtração dos dois e caso sejam iguais, a saída Zero é setada)
- Cálculo do endereço destino (se houver desvio: PC + deslocamento)
![[Pasted image 20250514182951.png]]
### Implementação
![[Pasted image 20250514183022.png]]
## Unidade de Controle
![[Pasted image 20250514183321.png]]
### Imm Gen
Para a unidade de controle gerar os sinais de controle, a implementação pode ser feita de acordo com a tabela abaixo.

| Imm Src | Imm Ext                                                            | Tipo Instrução |
| ------- | ------------------------------------------------------------------ | -------------- |
| 00      | {{20 x {Inst{31}}}, inst{31:20}}                                   | Tipo I         |
| 01      | {{20 x {Inst{31}}}, inst{31:25}, inst{11:07}}                      | Tipo S         |
| 10      | {{19 x {Inst{31}}, inst{31}, inst{7}, inst{30:25}, inst{11:8}, 0}} | Tipo B         |
Veja abaixo como são divididos os bits em alguns tipos de instrução.
![[Pasted image 20250514183242.png]]
### Sinais de Controle
| Opcode | ALU Src | ALU Op | Imm Src | Branch | Mem Read | Mem Write | Mem to Reg | Reg Write |
| ------ | ------- | ------ | ------- | ------ | -------- | --------- | ---------- | --------- |
| Tipo R | 0       | 10     | XX      | 0      | 0        | 0         | 0          | 1         |
| lw     | 1       | 00     | 00      | 0      | 1        | 0         | 1          | 1         |
| sw     | 1       | 00     | 01      | 0      | 0        | 1         | X          | 0         |
| beq    | 0       | 01     | 10      | 1      | 0        | 0         | X          | 0         |
| addi   | 1       | 00     | 00      | 0      | 0        | 0         | 0          | 1         |
Para entender o que significa os códigos acima, verifique as informações abaixo.
- `ALU Src`:
	- 0 - Bloco Reg
	- 1 - Imm
- `ALU Op`:
	ALU Control
	- lw/sw/addi: 00
	- beq: 01
	- Tipo R: 10
- `Imm Src`: só verificar o Imm Gen
- `Branch`:
	- 0 - $\bar{beq}$
	- 1 - $beq$
- `Mem Read`:
	- 0 - Não lê da memória
	- 1 - Lê da memória
- `Mem Write`:
	- 0 - Não escreve na memória
	- 1 - Escreve na memória
- `Mem to Reg`:
	- 0 - é da ULA
	- 1 - é da memória de dados
- `Reg Write`:
	- 0 - Não escreve no banco de registradores
	- 1 - Escreve no banco de registradores
## Desvantagem de usar essa arquitetura
A desvantagem de usar uma arquitetura monociclo é que o ciclo de clock é o suficiente para executar a instrução mais lenta (lw).
![[Pasted image 20250424090442.png]]
A solução para essa desvantagem é fazer com que as instruções demorem mais do que um ciclo de clock para finalizar e dividir a execução da instrução em etapas, onde cada etapa é executada em 1 ciclo de clock. Importante ressaltar que nem todas as instruções demoram o mesmo números de ciclos de clock para finalizar. Veja abaixo.
![[Pasted image 20250424091058.png]]
# RISC-V: Pipeline
A implementação pipeline consiste em dividir a execução da instrução em etapas. Cada etapa consome 1 ciclo de clock. Além disso, temos a sobreposição das etapas de diferentes instruções no mesmo ciclo de clock. Ou seja, a ideia do pipeline é diversas instruções estarem sendo executadas no mesmo ciclo de clock (usando etapas diferentes) e usando componentes diferentes.
Nessa implementação, todas as instruções vão passar por todas as etapas (mesmo naquelas que elas não usam), pois se não teremos duas instruções diferentes na mesma etapa no mesmo ciclo de clock. Para evitar isso, fazemos as instruções passar por todas as etapas (gastando um ciclo de clock).
Algumas considerações sobre o pipeline:
- O pipeline não diminui o tempo de execução de cada tarefa, mas aumenta o throughput (instrução finalizada por segundo) de toda a carga de trabalho. 
- A taxa do pipeline é limitado pelo estágio mais lento
- Várias tarefas são realizadas simultaneamente utilizando diferentes recursos
- Um speedup potencial é o número de estágios do pipeline
- O tempo para encher o pipeline e para esvaziá-lo diminui o speedup
- O pipeline trava se houver dependências
- A instrução LOAD é a mais longa
As etapas são:
- IF (Instruction **Fetch**): Busca da instrução na memória de instruções
- ID (Reg/Dec ou Register Read): Busca de dados no banco de registradores (Reg) e decodificação (Dec)
- EX (Exec ou ALU Operation): Calcula o endereço de memória ou execução da operação na ULA
- MEM (Data Acess): Escrita na memória de dados (acesso à memória principal)
- WB (Register Write): Escrita do resultado calculado ou lido da memória no banco de registradores
![[Pasted image 20250515204202.png]]
![[Pasted image 20250424092353.png]]
Na imagem podemos ver um problema do pipeline, que é que temos duas instruções usando o mesmo componente. Mas temos um jeito de contornar isso, que é dividindo o ciclo de clock em duas partes, na primeira é realizada uma escrita e na segunda parte uma leitura.
Na implementação pipeline, tempo de execução da instrução não diminui, mas aumenta o throughput (também chamado a vazão, que instrução por segundo).
Nesse tipo de implementação, o ciclo de clock é limitado pelo estágio mais lento.
### Cálculo do tempo para executar instrução no Pipeline
Antes de mostrarmos o cálculo, precisamos ver quais fatores devemos levar em conta.
- nº de intruções (n)
- nº de estágios do pipeline (profundidade do pipeline)
Vejamos agora o cálculo.
$$nº \, de \, ciclos \, de \, clock = (nº \, de \, estágios) + (n-1) * 1 cc = (nº \, de \, estágios - 1) + (n) * 1 cc$$
Onde $1cc$ é 1 ciclo de clock.
Vejamos um exemplos agora. Para 100 instruções:
- Monociclo:
	- ciclo de clock = 45 ns
	- Tempo = 100 * 45 = 4500 ns
- Multiciclo:
	- ciclo de clock = 10 ns
	- nº médio de etapas = 4,2 (Tipo R tem 4 etapas, lw tem 5, sw tem 4 e beq tem 4, então fazemos uma média)
	- Tempo = 100 * 4,2 * 10 = 4200 ns
- Pipeline:
	- ciclo de clock: 10 ns
	- nº de ciclos de clock: (usando a fórmula anterior) 5 + 99 = 104
	- Tempo: 104 * 10ns = 1040 ns
	- 1 instrução finaliza em 10 ns, logo em 1 segundo temos $1 \times 10^8$ instruções sendo executadas
## Implementação Pipeline
![[Pasted image 20250429112524.png]]
Os blocos em azul são um conjunto de registradores (como se fosse um banco de registradores intermediários) para que as informações que eu busquei anteriormente estejam armazenadas neles e no próximo ciclo de clock eu possa buscar as informações nesse conjunto de registradores. Esses registradores são chamados de registradores intermediários do pipeline.
Os registradores desses conjuntos são:
- IF/ID.IR
- IF/ID.PC
- ID/EX.PC
- ID/EX.A
- ID/EX.B
- ID/EX.Imm
- ID/EX.rd
- EX/MEM.ALUOutput
- EX/MEM.rd
- EX/MEM.BranchTarget
- EX/MEM.B
- EX/MEM.zero
- MEM/WB.LMD
- MEM/WB.ALUOutput
- MEM/WB.rd
O que está sublinhado em vermelho é sinal de controle vindo da UC.
Os sinais de controle de cada etapa são:
 - ID/EX
	 - ALUOp
	 - ALUSrc
	 - MemRead
	 - MemWrite
	 - Branch
	 - RegWrite
	 - MemtoReg
 - EX/MEM
	 - MemRead
	 - MemWrite
	 - Branch
	 - RegWrite
	 - MemtoReg
 - MEM/WB
	 - RegWrite
	 - MemtoReg
## Dependências do Pipeline (Hazards)
O pipeline apresenta três problemas:
- Conflito estrutural
- Dependência de dados
- Dependência de controle
### Conflito Estrutural
O conflito estrutural ocorre devido o acesso instantâneo ao mesmo recurso (memória) por instruções em estágios diferentes (dois ou mais). Exemplo:
- Acesso Concorrente a memória
	- Uso de memórias multi-portas ou com múltiplos bancos de acessos independentes
- Leitura de instrução e leitura/escrita de dados simultâneos à memória
	- Uso da arquitetura "Harvard" com caches de dados e instruções separados
- Acesso simultâneo ao banco de registradores
	- Uso de banco de registradores com múltiplas portas
- Uso simultâneo da unidade funcional (ULA)
	- Replicação da unidade funcional ou implementação pipelined dessa unidade
Para resolver os problemas relacionados à memória, temos duas soluções:
![[Pasted image 20250515210214.png]]
- Separa dados e instruções
- Cache de dados e instruções
- Memória com múltiplos acessos independentes
Para resolver os problemas relacionados ao banco de registradores:
- Divide o ciclo de clock em 2 fases, onde na primeira (baixa) escreve no banco de registradores e na segunda (alta) lê
Para resolver o uso simultâneo da ULA:
- Acrescentamos mais unidades funcionais (no nosso caso acrescentamos dois somadores)
### Dependências de Dados
O problema da dependência de dados é quando uma instrução faz uso de um operando que vai ser produzido por outra instrução que ainda está no pipeline, ou seja, as instruções dependem de resultados de instruções anteriores ainda não completadas.
Temos dois tipos de dependência de dados:
- Dependência verdadeira/direta 
	Temos uma instrução que utiliza um operando que é produzido por uma instrução anterior.
	O tipo de dependência que temos aqui é chamada Read After Write (RAW)
	Exemplo:
	![[Pasted image 20250508085910.png]]
	De vermelho temos a dependência. Atenção, a representação da onde está a bolha está errado.
	Veja que o R1 é usado como operando na segunda instrução e ele é obtido na primeira. Analisando na estrutura, o R1 só será escrito no `WB`, ou seja, no 5º ciclo de clock, mas ele será lido da memória no `ID` da segunda instrução, que ocorrerá no 3º ciclo de clock.
	Quando temos ciclos de clock em que não tem nenhuma instrução finalizada, devido a prorrogação das instruções, chamamos esses ciclos de bolha
	Para resolver isso postergamos a instrução até ela chegar no `WB`, porque assim na primeira parte do clock será a escrita e na segunda será a leitura. Como consequência, todas as próximas instruções também terão que ser postergadas.
	Nessas dependências, o pipeline precisa ser parado durante certo número de ciclos (interlock).
	Há a inserção de instruções `nop` ou escalonamento adequado das instruções pelo compilador.
	O adiantamento (bypassing ou forwarding) dos dados pode resolver em alguns casos. Além dele, também pode ser usado o escalonamento para mitigar esses problemas.
- Dependência Falsa
	Só existe se a arquitetura suporta execução fora de ordem (out-of-order execution). Ela só existe em processadores e arquiteturas superescalares. A execução fora de ordem consiste em permitir colocar instruções que vem mais adiante, que não possuem uma dependência, antes de instruções que tem dependência.
	Elas não são um problema em pipelines onde a ordem de execução das instruções é mantida.
	A renomeação dos registradores é uma solução usual para este problema.
	Aqui temos dois tipos de dependências:
	- Write After Read (WAR) ou antidependência
		Nela temos uma instrução que lê um operando que é escrito por uma instrução sucessora.
		```
		add R1, R2, R3
		sub R2, R5, R6
		```
		Supondo que ainda não temos o R3, veja que a ``sub`` pode ser calculada mas não pode ser escrita ainda pois temos que realizar o ``add`` antes.
	- Write After Write (WAW) ou dependência de saída
		Temos uma instrução que escreve um operando que é também escrito por uma instrução sucessora.
		```
		add R1, R2, R3
		sub R1, R5, R6
		```
		Supondo que ainda não temos o R3, veja que a `sub` pode ser calculada antes mas também não pode ser escrita pois temos que fazer o `add` antes.
Para evitar as dependências verdadeiras, o compilador faz o que conhecemos como escalonamento das instruções.
#### Escalonamento das Instruções
Veja nas imagens a seguir como ocorre esse escalonamento e repare que o grafo que o compilador monta das dependências é o grafo colorido que está nas instruções.
![[aula_org_arq_08_05_1.jpg]]
![[aula_org_arq_08_05_2.jpg]]
Agora o compilador reordena as instruções para diminuir o número de bolhas.
![[aula_org_arq_08_05_3.jpg]]
![[aula_org_arq_08_05_4.jpg]]
Esse processo é feito automático pelo compilador, mas em alguns casos podemos usar a função `nop` para forçar um auxílio mas não é obrigatório, ele mesmo já faz toda a manipulação necessária. Caso ele não consiga, inserimos a função como é visto abaixo.
~~~assembly
lw t1, 0(t0)
lw t2, 4(t0)
nop
nop
add t3, t1, t2
nop
nop
sw t3, 12(t0)
~~~
### Forwarding ou Bypassing
Uma outra forma de resolver esse problema das dependências é usando forwarding. Para usar ele temos que mudar nossa implementação. Veja como que ela fica abaixo. Vale ressaltar que alguns componentes e conexões não foram representados para facilitar a visualização mas eles estão lá.
![[aula_org_arq_13_05.jpg]]
Nessa técnica é realizado o adiantamento de dados no caminho interno dentro do pipeline entre a saída e a entrada da ULA. Ela evita a parada do pipeline utilizando buffers internos em vez de esperar que o elemento de dado chegue nos registradores visíveis ao programador ou na memória.
![[Pasted image 20250515211841.png]]
Entretanto, em algumas situações, nem o forwarding pode resolver o problema de parada do pipeline.
Para implementar o forwarding, primeiro temos que ter condições para que o adiantamento seja considerado:
- Destino da instrução que está entre os ciclos de EX e MEM é igual a um dos registradores de origem da instrução que está nos ciclos de ID e EX
	- EX/MEM.rd = ID/EX.rs
	- EX/MEM.rd = ID/EX.rt
- Destino da instrução que está entre os ciclos de MEM e WB é igual a um dos registradores de origem da instrução que está entre os ciclos de ID e EX
	- MEM/WB.rd = ID/EX.rs
	- MEM/WB.rd = ID/EX.rt
Veja no exemplo abaixo que temos as seguintes dependências:
![[Pasted image 20250515212530.png]]
- Entre as instruções: `sub 2, 1, 3` e `and 12, 2, 5`
- Entre as instruções: `sub 2, 1, 3` e `or 16, 6, 2`
As duas dependências `sub-add` não são problema pois o banco de registradores irá fornecer os dados corretos no ciclo de decodificação. Logo não existe hazard entre as instruções `sub` e `sw`.
#### Unidade de Forward
![[Pasted image 20250515212604.png]]
![[aula_org_arq_15_5_1.jpg]]
![[Pasted image 20250515212625.png]]
Veja agora as definições das condições para detecção de dependência de dados:
- Dependência EX:
	- `if(EX/MEM.RegWrite and (EX/MEM.rd != 0) and (EX/MEM.rd == ID/EX.rs1)) -> ForwardA = 1`
	- `if(EX/MEM.RegWrite and (EX/MEM.rd != 0) and (EX/MEM.rd == ID/EX.rs2)) -> ForwardB = 1`
- Dependência MEM:
	- `if(MEM/WB.RegWrite and (MEM/WB.Rd != 0) and ( MEM/WB.Rd == ID/EX.rs1)) -> ForwardA = 01`
	- `if(MEM/WB.RegWrite and (MEM/WB.Rd != 0) and ( MEM/WB.Rd == ID/EX.rs2)) -> ForwardB = 01`
O circuito do pipeline fica então:
![[Pasted image 20250515213115.png]]
### Paradas
Nem sempre é possível resolver as dependências com forwarding. A estrutura acima não resolve o problema da dependência quando se tem uma `lw` seguida por uma instrução que lê o desvio da `lw`. Nesses casos, a solução é parar o pipeline quando se detecta a dependência, através da unidade de parada (stall).
Veja abaixo o circuito com a unidade de parada e também o circuito com a unidade de parada.
![[aula_org_arq_15_5_2.jpg]]
Se for detectada a dependência, deve ser inserida uma função `nop` no operation.
![[Pasted image 20250515213427.png]]
Caso a parada seja detectada no estágio ID, as instruções nos estágios ID e IF devem parar. Para isso basta impedir que o registrador PC e os registradores de pipeline IF/ID sejam alterados, preservando os seus conteúdos no próximo ciclo. Como a instrução está em um pipeline, ela caminha para o estágio EX, que precisa executar algo, mas não pode ser a instrução pois não tem os dados necessários. Então ele executa uma instrução que não tem efeito, ou seja, o `nop`. Para inserir essa bolha no pipeline, basta desativar todos os sinais de controle dos estágios EX, MEM e WB.
Assim, obtemos o seguinte circuito completo:
![[Pasted image 20250515213751.png]]
### Dependência de Controle
A dependência de controle ocorre quando a próxima instrução não está no endereço subsequente ao da instrução anterior. As instruções que podem alterar a ordem de execução do programa são:
- Condicionais: if-then-else, for (bnez, bne, beq, etc)
- Incondicionais: chamadas de procedimentos (jal), goto (j), return (jr), procurando o endereço de retorno de uma tabela (jalr)
Os efeitos dos desvios condicionais são que se o desvio ocorre, o pipeline precisa ser esvaziado (e no lugar teremos bolhas). Não se sabe se o desvio ocorrerá ou não até o momento de sua execução.
As soluções para para o problema são:
- Congelar o pipeline quando se detecta que é uma instrução de desvio até que o resultado do desvio seja conhecido. Ele vai inserir bolhas no pipeline. Isso é uma solução ruim quando o pipeline é muito longo, pois congelar o pipeline pode ser muito lento.
	![[Pasted image 20250515213844.png]]
- Considerar que o desvio não vai ser tomado e que vai continuar no fluxo sequencial. Quando o desvio é tomado, as instruções buscadas, decodificadas e passadas pela ULA precisam ser descartadas. Para descartar, basta alterar os valores de controle para 0, como foi feito no tratamento de dependência de dados. Como a decisão do desvio é feita somente no estágio MEM, é necessário alterar as instruções nos estágios IF, ID e EX, isso significa dar flush (descartar) nas instruções. Ou seja, ele executa normalmente até chegar o momento em que o desvio seria executado, quando ele for executado temos que dar um flush no pipeline até chegar a instrução para a qual desviamos. 
- Mover a execução do desvio para um estágio anterior a MEM, reduzindo o atraso dos desvios. Isso implica em:
	- Cálculo do endereço destino
	- Cálculo da condição (decisão de desvio)
	Quando fazemos essa movimentação, utilizamos uma delayed branch (desvio atrasado) para as instruções de desvio. A ideia é pegar uma instrução que não depende do desvio (anteriores ou posteriores a ele) e colocá-la para ser executada logo após ele. Desse modo a instrução após o desvio é sempre executada. Essa próxima instrução é chamada de delay slot (posição de atraso). Só podemos fazer essa delayed branch com uma instrução, visto que como movemos o desvio em um ciclo de clock, teremos só uma instrução de atraso e estamos preenchendo ela. Isso vai implicar em um reordenamento das instruções (desvio atrasado otimizado).
	Para facilitar o trabalho do compilador, no preenchimento do delay slot muitas arquiteturas permitem o uso do delay slot com a opção de anulação automática dessa instrução se o desvio condicional não for tomado. Desse modo, uma instrução do endereço alvo pode ser movida para o delay slot, o que é muito útil no caso de loops. Nesse caso, está implícita uma previsão de desvio estática que diz que o desvio será sempre tomado.
	![[aula_org_arq_15_5_3.jpg]]
- Tentar prever o comportamento do desvio
	- Desvio tomado (branch taken): PC = PC + Imm
	- Desvio não tomado (branch not taken): PC = PC + 4
	Tipos de predição:
	- Estática
		- Geração de bolhas quando a previsão é errada, baixa taxa de acertos
		- Não permite adaptações com relação ao comportamento do programa (não se baseia no comportamento do seu código)
		- Pode fazer uso de um hardware para inserir bolha
		Os tipos de previsão estática são:
		- Assumir que todos os desvios não são tomados (predicted-untaken)
		- Assumir que todos os desvios são tomados (predicted-taken)
		- Assumir que todos os desvios com determinado operation code serão tomados
		- Os desvios para trás são assumidos como tomados (branch taken) e os desvios para frente são assumidos como não tomados (branch not taken). Isso é conhecido como Backward-Taken, forward not-taken (BTFNT)
	- Dinâmica
		- Ela é baseada no comportamento do seu código
		Preditor de 1-bit:
		![[Pasted image 20250515101718.png]]
		- Mantém uma pequena memória indexada pela parte menos significativa do endereço da instrução do desvio
		- Ele tem um Buffer de previsão de desvios (Branch-Prediction Buffer) ou Tabela de histórico de desvios
		- Essa tabela tem 1 bit que diz se o desvio foi tomado recentemente ou não e que indica se o próximo desvio deve ou não ser considerado
		- Em casos de erros esse bit é alterado
		- Ele erra duas vezes (quando temos um só loop): quando termina a primeira iteração (que acha que sai mas não sai) e quando sai do loop (que acha que não vai sair mas sai)
		- Não mantém o histórico
		- Um previsor de 1-bit prediz corretamente um desvio ao final de uma iteração de um loop, enquanto o loop não termina
		- Em loops aninhados, um previsor de 1-bit irá causar duas predições incorretas para o loop interno:
			- Uma vez ao final no final do loop, quando a iteração termina o loop ao invés de ir para o começo do loop
			- Uma vez quando a primeira iteração do loop for reiniciada, quando ele prediz o término do loop ao invés do começo do loop
		- Este erro duplo em loops aninhados é evitado por um esquema de previsão de dois bits
		Preditor de 2-bits:
		- Permite errar duas vezes antes de alterar a predição
		- O previsor de 2-bits (bimodal) é essencialmente um contador de dois bits com valores entre 0 e 3.
		![[Pasted image 20250515095903.png]]
# Hierarquia de Memória
## Memória
Definimos como memória todo componente capaz de armazenar informação. As características desejáveis em uma memória são:
- Rápida
- Grande
- Barata
Só que essas características são conflitantes. Então para solucionar isso fazemos uma hierarquia de memória
## Hierarquia de Memória
![[Pasted image 20250522083528.png]]
![[Pasted image 20250522084100.png]]
As características do sistema de memória do computador são:
- Localização
	- Memória secundária: foram da placa
	- Memória principal: na placa mas fora da CPU
	- Cache: interna a CPU
- Capacidade
	- Tamanho da palavra: a palavra é a unidade de endereço da memória, ou seja, é o número de bits para representar um inteiro ou uma instrução
	- Número de palavras
	- Unidade de endereçamento: byte ou (exclusivo) palavra
- Unidade de transferência
	- Memória principal: número de bits lido ou escrito na memória principal, que é uma palavra
	- Memória secundária: unidades maiores, que são chamadas de bloco
- Forma de acesso
	- Sequencial: 
		- Dados organizados em registros
		- Tempo de acesso ao registro varia
		- Ex: fita magnética
	- Direto:
		- Dados organizados em bloco
		- Tempo de acesso variável
		- Cada bloco tem um endereço
		- Ex: disco magnético
	- Aleatório:
		- Cada bloco tem um endereço único
		- Tempo de acesso constante
		- Ex: memória principal (RAM -> Random) (ROM -> Read)
	- Associativo:
		- Compara bits com conteúdo das posições de memória
		- Ex: cache
- Desempenho
	- Tempo de acesso (latência): 
		- Em memórias de acesso aleatório é o tempo gasto para realizar a operação de leitura ou escrita
		- Em memórias de acesso não aleatório é o tempo gasto para posicionar o mecanismo de leitura/escrita
	- Tempo de ciclo de memória:
		- Em memória de acesso aleatório é o tempo necessário para que o sistema esteja pronto para fazer outra operação
	- Tempo de transferência: taxa que os dados são transferidos
- Características físicas
	- Apagável/Não apagável
		- Apagável: RAM, HD, SSD
		- Não apagável: ROM, CD, DVD
	- Mecanismo de escrita
		- Elétrico
		- Máscara
	- Organização
		- Arranjo físico de bits para formar uma palavra
## Tipos de Memória
### Memórias Não Voláteis
Elas mantém o conteúdo mesmo quando são desconectadas da rede de alimentação.
Ex: ROM, PROM, EPROM, EEPROM, FLASH
### Memórias Não Voláteis
Perdem o conteúdo quando a tensão de alimentação é desligada.
Ex: RAM
### ROM - Read Only Memory
Ela consiste em uma tabela binária formada através de matrizes que geram produtos canônicos de acordo com a combinação das variáveis de entrada. Seu conteúdo é fixo (imutável). Como é uma matriz, temos que o endereço geralmente é bidimensional (linhas e colunas).
![[Pasted image 20250522095228.png]]
### PROM - ROM Programável
Ela pode ser programada uma única vez. A organização é semelhante à ROM. No local do dado temos um fusível.
### EPROM
É uma ROM Programável (escrita) eletronicamente.
### EEPROM
É uma rum reprogramável (escrita e apaga) eletronicamente. Um exemplo é a flash.
## Memória Cache
Ela tem um método de acesso associativo. Ou seja, a localização dos dados na memória é feito pelo conteúdo e não pelo endereço.
Hierarquia de acesso à memória principal:
- um nível mais próximo do processador é normalmente um subconjunto de qualquer nível mais distante
- todos os dados são armazenados no nível mais baixo
![[Pasted image 20250527103235.png]]
### Princípio da Localidade Temporal e Espacial
Analisando a parte temporal desse princípio temos que se um conteúdo na memória foi utilizado em um instante, existe a probabilidade dele ser utilizado novamente em um instante futuro.
Agora para a parte espacial, temos que se um conteúdo na memória foi utilizado, existe a probabilidade das posições que estão perto serem usadas também.
Para manter a cache, existem políticas que determinam quais elementos devem ser mantidos na cache e que controlam a consistência da informação. Caches bem implementados atingem taxas de acerto (cache hit) superior a 95%. Além de ter políticas que determinam quais elementos devem ser mantidos na cache, as memórias devem ser estruturadas,
### Conceitos
- Bloco: menor unidade a ser transferida de um nível para outro
- Acerto (hit): a informação está na cache (hit rate -> taxa de acerto)
- Falha (miss): a informação não está na cache (miss rate -> taxa de falha)
- Tempo de acerto: tempo necessário para acessar um nível da hierarquia incluindo o tempo para determinar se é acerto ou falha
- Penalidade por falha: tempo necessário para buscar um bloco de um nível inferior para um nível superior incluindo o tempo para acessar o bloco, transmiti-lo de um nível para outro e inseri-lo no nível que ocorreu a falha
### Implementação
#### Tamanho da Cache
É resultado de um compromisso entre a quantidade de dados armazenados, custo e desempenho. Se tivermos um tamanho suficientemente pequeno, estamos priorizando custo/complexidade. Já se tivermos um tamanho suficientemente grande, temos uma taxa de acerto alta e priorizamos o desempenho.
O tamanho da memória cache depende da localização da cache.
Quanto menor for a cache, mais rápida ela é, pois quanto maior a cache, maior é o número de portas envolvidas no endereçamento, o que torna ela mais lenta. Logo, quanto menor a cache, mais rápida ela é.
#### Tamanho do Bloco
Ele é baseado no princípio da localidade espacial. Assim, quanto maior o bloco, maior a taxa de acerto.
Bloco grande é bom até que a probabilidade de utilizar os dados buscados recentemente se torne menor do que a probabilidade de reutilizar os dados que foram substituídos.
#### Estrutura da Cache
![[Pasted image 20250527113458.png]]
Cada linha (informações sobre a linha + bloco (dados)) da cache possui as seguintes informações:
- tag: identifica unicamente uma linha na cache (é aqui que vem o método associativo)
- V: bit de validade, indica se é entrada é válida (1) ou não (0)
- M: bit de modificação, indica se os dados armazenados na linha estão modificados (dirty) (1) ou não (0). Ele só é necessário se a política de escrita for write-back
- Alg. Subs: bits para implementar o algoritmo de substituição. Só são necessários se o mapeamento for associativo total ou associativo por conjunto
- Dados: bloco (conjunto de palavras) vindo do nível inferior
### Função de Mapeamento
O número de blocos na memória principal é maior do que o número de linhas na cache. Portanto, é necessário:
- algoritmos para mapear blocos de memória principal em blocos da memória cache
- mecanismos para determinar o bloco da memória principal que ocupa certo bloco da memória cache
Temos os seguintes tipos de mapeamento:
- mapeamento direto
- mapeamento associativo
- mapeamento associativo por conjunto
#### Mapeamento Direto
Cada bloco na memória principal é mapeado sempre na mesma linha da cache. Veja abaixo a expressão:
$$i = j \,\,módulo \,\, m$$
Onde:
- i: é o número da linha na cache
- j: é o número do bloco na memória principal
- m: é o número de linhas na memória cache
![[Pasted image 20250603111018.png]]
Vários blocos da memória principal podem ser mapeados na mesma linha da cache. Para saber se o bloco que se quer acessar é o que está na cache usamos um campo chamado tag ou rótulo.
Nós dividimos o endereço em campos:
- byte offset: deslocamento do byte dentro da palavra
- word offset: deslocamento da palavra dentro do bloco
- index: dizer em qual linha o bloco será mapeado (resultado da operação módulo)
- tag: identificar unicamente um bloco na cache 
Para saber se a entrada na cache contém um endereço válido ou não, incluímos um bit de validade (v).
Como temos 64 bytes, ou $2^6$ bytes, temos 6 bits para representar 64 posições
![[aula_org_arq_03_06_1.jpg]]
As vantagens desse mapeamento são:
- técnica simples
- baixo custo de implementação
Já as desvantagens são:
- cada bloco é mapeado em uma posição fixa na memória cache, então se houver referência a blocos distintos mapeadas na mesma linhas, teremos blocos trocados continuamente, logo, temos uma taxa de acerto baixa
#### Mapeamento (Totalmente) Associativo
Cada bloco da memória principal pode ser carregado em qualquer linha da memória cache, ou seja, ela evita a desvantagem do mapeamento direto. Os algoritmos de substituição que ele usa são:
- FIFO (First-In, First-Out)
- LRU (Least Recently Used)
- LFU (Least Frequently Used)
Para determinar se um bloco está na cache, comparamos simultaneamente o campo do rótulo do endereço do bloco acessado com o rótulo de todos os blocos da cache.
![[Pasted image 20250603113506.png]]
![[Pasted image 20250603113625.png]]
#### Mapeamento Associativo por Conjunto
