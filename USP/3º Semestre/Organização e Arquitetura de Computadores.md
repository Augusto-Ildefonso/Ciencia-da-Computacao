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
# Evolução e Questões de Desempenho
## 1ª Geração -> Válvulas
### ENIAC
O ENIAC (Electronic Numerical Integrator And Computer) é o primeiro computador digital eletrônica de grande escala. Ele foi feito por John Presper Eckert e John Mauchly no laboratório de pesquisas balísticas do exército americano, ele ia ser usado num projeto para cálculo de alcance e trajetória de projéteis. Ele iniciou em 1943 e terminou em 1946, muito tarde para todo o esforço da guerra. Ele foi usado até 1955.

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
![[Pasted image 20250227090656.png]]
### Estrutura do IAS
![[Pasted image 20250227090736.png]]
## 2ª Geração -> Transistores
Essa geração começou em 1947 com a invenção de transistores por William Shockley el al na Bell Laboratories. Outros pontos importantes dessa segunda geração são: ALU e UC mais complexas, presença de linguagens de programação de alto nível, software de sistema.
### Convertendo as linguagens
Quando temos uma linguagem de alto nível, para poder executar o código dela, o compilador transforma o código em um código em assembly e por fim o assembler converte o assembly para código binário de máquina.
![[Pasted image 20250227091750.png]]
### Compilador vs Interpretador
Um compilador traduz todo o código-fonte de um programa para linguagem de máquina de uma só vez, gerando um arquivo executável que pode ser executado posteriormente sem a necessidade do código original. Já um interpretador analisa e executa o código linha a linha, sem gerar um executável, o que facilita a depuração, mas pode tornar a execução mais lenta. Enquanto compiladores oferecem maior desempenho final, interpretadores trazem mais flexibilidade durante o desenvolvimento.
## 3ª Geração -> Diminui o tamanho dos transistores
Na terceira geração a série IBM360 (1964) substituiu a séria 7000 e não havia compatibilidade entre elas. Com a IBM360 foi criada a 1ª família de computadores:
- Usavam arquitetar do conjunto de instruções similares ou idênticas
- Tinham sistemas operacionais similares ou idênticos
- Velocidade crescete
- Número crescente de portas de E/S e terminais
- Capacidade de memória variada
- Custo variado

Além disso essa geração introduziu o conceito de multiprogramação, ou seja, ter vários programas na memória ao mesmo tempo (time-sharing e troca de contexto).
### DEC PDP - 8
O DEC PDP - 8 foi o primeiro minicomputador, pequeno o suficiente para uso em uma bancada de laboratório. Eles eram mais baratos, custando mais ou menos 16 mil dólares, enquanto o IBM360 custava mais de 100 mil dólares. Eles tinham uma estrutura de barramento.
![[Pasted image 20250227092545.png]]
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
Com o aumento da densidade dos componentes  em um chip, Gordon Moore (co-fundador da intel) propôs uma lei que dizia:
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

