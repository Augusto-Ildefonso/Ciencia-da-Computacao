# Armazenamento Secundário
## Organização
![[Pasted image 20250311153018.png]]
### Disco
O disco é o conjunto de pratos empilhados. Os dados são gravados nas superfícies desses pratos.]![[Captura de tela 2025-03-11 152437.png]]
### Superfície
A superfície é organizada em trilhas.
### Trilhas
As tracks, também chamadas de trilhas, servem para o endereçamento do disco. Essas trilhas são organizadas em setores, que são a menor porção endereçável do disco.
### Cilindro
Conjunto de trilhas na mesma posição.
## Capacidade do disco (nominal)
### Capacidade do setor
É o número de bytes.
### Capacidade da trilha
Número de setores/trilha x capacidade do setor.
### Capacidade do cilindro
Número de trilhas/cilindro x capacidade da trilha.
### Capacidade do disco
Número de cilindros x capacidade do cilindro.
## Custo de Acesso a Disco
O tempo de acesso (seek time) é o tempo para posicionar a cabeça de leitora (movimento da cabeça de leitora para se posicionar na trilha) e gravação no cilindro correto.
O delay de rotação (rotational delay) é o tempo para rotacionar o disco para que a cabeça de leitora e gravação seja posicionada no setor correto.
O tempo de transferência (transfer time) é o tempo para transferir o dado para a memória primária.
## Seeking
É o movimento de posicionar a cabeça de L/E sobre a trilha/setor desejado (mas deixando claro ele não movimenta a cabeça de leitora pois tem vários buffers entre o programa e o disco rígido, mas podemos pensar como foi dito, pois estamos abstraindo). O conteúdo de todo um cilindro pode ser lido em um único seeking. O seeking é o movimento mais lento da operação de leitura/escrita. Ele deve ser reduzido ao mínimo.
## Disco Físico e Disco Lógico
A formatação física (disco físico) é a organização do disco em setores/trilhas/cilindros que já vem de fábrica. Ela pode ser mudada por meio de partições.
A formatação lógica (disco lógico) instala o sistema de arquivos no disco, subdivide o disco em regiões endereçáveis e introduz o overhead relacionado ao espaço ocupado com informações para gerenciamento.