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
## Conjunto de Instruções
Também chamado de ISA (Instruction Set Architecture), elas definem a quantidade e funções dos registradores (bloco de registradores). Existem 6 tipos de instrução (todas de 32 bits):
- Tipo R - Register
- Tipo I - Immediate
- Tipo S - Store
- Tipo B - Branch
- Tipo U - Upper
- Tipo J - Jump
Em todas as instruções, o opcode vai estar nos 7 primeiros bits (0 a 6). Como temos só 7 bits, estamos limitador a 128 instruções. Mas para contornar isso usamos além do campo do opcode, o campo F3 para especificar a operação, ampliando a capacidade de instruções.
Das imagens abaixo, o montador vai dividir os bits em grupos de 4 e converter para hexadecimal, ficando por exemplo `0x00012903` e assim em diante. Vale ressaltar que ele não respeita a divisão dos bits entre os registradores. Cada registrador tem um valor, exemplo o `s2` é `x18` e aí salvamos o 18 em binário nos registradores.
### Tipo R
![[Pasted image 20250408103739.png]]
Exemplo de instrução: `add <rd>, <rs1>, <rs2>`.
### Tipo I
Todas as instruções que tem um valor imediato definido na instrução.
![[Pasted image 20250408104633.png]]
Exemplos de instruções: `addi <rd>, <rs1>, immediate` ou `lw <rd>, imm(<rs1>)`.
A combinação de f3 + opcode que diz se é `lw` ou `lb`, etc. 
### Tipo S
![[Pasted image 20250408105810.png]]
Exemplo de instrução: `sw <rs2>, imm(<rs1>)`.
É importante para a arquitetura que os registradores estejam sempre nas mesmas posições, então o `rs1` sempre vai estar entre 15 e 19, o `rs2` entre 20 e 24 e assim em diante. Por isso, o immediate é dividido em duas partes, de modo a não alterar as posições dos registradores.
A combinação de f3 + opcode que diz se é `sw` ou `sb`, etc.
### Tipo B
![[Pasted image 20250408114559.png]]
Exemplo de instrução: `beq <rs1>, <rs2>, imm`.
O immediate é o número de meias-palavras que tem do branch até onde é para pular. Como trabalhamos com half-words, o próprio montador, quando gera o assembly, vai colocar o valor 0 no início do valor imediato para multiplicá-lo por 2 e então obter o número de bits. E trabalhamos com half-words pois isso dobra a capacidade de representação, quando comparado com bytes.
O 12 tem que estar no final pois o último bit tem que ser o de sinal. Por causa disso, não há espaço para o 11 e por isso colocamos ele no primeiro bit do immediate.
### Tipo U
![[Pasted image 20250408114526.png]]
Exemplo de instrução: ``lui <rd>, imm``.
# RISC-V: Monociclo
## Caminho de Dados
## Unidade de Controle
### Imm Gen
Para a unidade de controle gerar os sinais de controle, a implementação pode ser feita de acordo com a tabela abaixo.

| Imm Src | Imm Ext                                                            | Tipo Instrução |
| ------- | ------------------------------------------------------------------ | -------------- |
| 00      | {{20 x {Inst{31}}}, inst{31:20}}                                   | Tipo I         |
| 01      | {{20 x {Inst{31}}}, inst{31:25}, inst{11:07}}                      | Tipo S         |
| 10      | {{19 x {Inst{31}}, inst{31}, inst{7}, inst{30:25}, inst{11:8}, 0}} | Tipo B         |
### Sinais de Controle
| Opcode | ALU Src | ALU Op | Imm Src | Branch | Mem Read | Mem Write | Mem Reg | Reg Write |
| ------ | ------- | ------ | ------- | ------ | -------- | --------- | ------- | --------- |
| Tipo R | 0       | 10     | XX      | 0      | 0        | 0         | 0       | 1         |
| lw     | 1       | 00     | 00      | 0      | 1        | 0         | 1       | 1         |
| sw     | 1       | 00     | 01      | 0      | 0        | 1         | X       | 0         |
| beq    | 0       | 01     | 10      | 1      | 0        | 0         | X       | 0         |
| addi   |         |        |         |        |          |           |         |           |
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
- `Mem Reg`:
	- 0 - é da ULA
	- 1 - é da memória de dados
- `Reg Write`:
	- 0 - Não escreve no banco de registradores
	- 1 - Escreve no banco de registradores
## Desvantagem de usar essa arquitetura
A desvantagem de usar uma arquitetura monociclo é que o ciclo de clock é o suficiente para executar a instrução mais lenta (lw).
![[Pasted image 20250424090442.png]]
A solução para essa desvantagem é dividir a execução da instrução em etapas, onde cada etapa é executada em 1 ciclo de clock. Veja abaixo.
![[Pasted image 20250424091058.png]]
# RISC-V: Pipeline
A implementação pipeline consiste em dividir a execução da instrução em etapas. Cada etapa consome 1 ciclo de clock. Além disso, temos a sobreposição das etapas de diferentes instruções no mesmo ciclo de clock. Ou seja, a ideia do pipeline é diversas instruções estarem sendo executadas no mesmo ciclo de clock (usando instruções diferentes) e usando componentes diferentes.
Nessa implementação, todas as instruções vão passar por todas as etapas (mesmo naquelas que elas não usam), pois se não teremos duas instruções diferentes na mesma etapa no mesmo ciclo de clock. Para evitar isso, fazemos as instruções passar por todas as etapas (gastando um ciclo de clock).
As etapas são:
- IF: Busca da instrução, na memória de instruções
- ID: Decodificação e busca de dados no bando de registradores
- EX: Execução na ULA
- MEM: Escrita na memória de dados
- WB: Escrita do resultado no banco de registradores
![[Pasted image 20250424092353.png]]
Na imagem podemos ver um problema do pipeline, que é que temos duas instruções usando o mesmo componente. Mas temos um jeito de contornar isso, que é dividindo o ciclo de clock em duas partes, na primeira é realizada uma escrita e na segunda parte uma leitura.
Na implementação pipeline, tempo de execução da instrução não diminui, mas aumenta o throughput (também chamado a vazão, que é bits por segundo).
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
Alguns dos registradores desses conjuntos são:
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
O que está sublinhado em vermelho é sinal de controle vindo da UC.
## Dependências do Pipeline
O pipeline apresenta três problemas:
- Conflito estrutural
- Dependência de dados
- Dependência de controle
### Conflito Estrutural
O conflito estrutural ocorre devido o acesso instantâneo ao mesmo recurso por instruções em estágios diferentes. Exemplo:
- Acesso a memória
- Acesso ao banco de registradores
- Uso simultâneo da unidade funcional (ULA)
Para resolver os problemas relacionados à memória, temos duas soluções:
- Separa dados e instruções
- Cache de dados e instruções
Para resolver os problemas relacionados ao banco de registradores:
- Divide o ciclo de clock em 2 fases, onde na primeira (baixa) escreve no banco de registradores e na segunda (alta) lê
Para resolver o uso simultâneo da ULA:
- Acrescentamos mais unidades funcionais (no nosso caso acrescentamos dois somadores)
### Dependências de Dados
O problema da dependência de dados é quando uma instrução faz uso de um operando que vai ser produzido por outra instrução que ainda está no pipeline. Isso é chamado por alguns autores como *Hazard* (perigo).
Temos dois tipos de dependência de dados:
- Dependência verdadeira/direta 
	O tipo de dependência que temos aqui é chamada Read After Write (RAW)
	Exemplo:
	![[Pasted image 20250508085910.png]]
	De vermelho temos a dependência.
	Veja que o R1 é usado como operando na segunda instrução e ele é obtida na primeira. Analisando na estrutura, o R1 só será escrito no `WB`, ou seja, no 5º ciclo de clock, mas ele será lido da memória no `ID` da segunda instrução, que ocorrerá no 3º ciclo de clock.
	Quando temos ciclos de clock em que não tem nenhuma instrução finalizada, devido a prorrogação das instruções, chamamos esses ciclos de bolha
	Para resolver isso postergamos a instrução até ela chegar no `WB`, porque assim na primeira parte do clock será a escrita e na segunda será a leitura. Como consequência, todas as próximas instruções também terão que ser postergadas.
- Dependência Falsa
	Só existe se a arquitetura suporta execução fora de ordem (out-of-order execution). Ela só existe em arquiteturas superescalares. A execução fora de ordem consiste em permitir colocar instruções que vem mais adiante, que não possuem uma dependência, antes de instruções que tem dependência.
	Aqui temos dois tipos de dependências:
	- Write After Read (WAR)
		```
		add R1, R2, R3
		sub R2, R5, R6
		```
		Supondo que ainda não temos o R3, veja que a ``sub`` pode ser calculada mas não pode ser escrita ainda pois temos que realizar o ``add`` antes.
	- Write After Write (WAW)
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
Esse processo é feito automático pelo compilador, mas em alguns casos podemos usar a função `nop` para forçar um auxílio (ver melhor ó que o nop faz) mas não é obrigatório, ele mesmo já faz toda a manipulação necessária.