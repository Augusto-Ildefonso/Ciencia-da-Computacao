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

(ver se precisa completar)
# Organização de Arquivos
Arquivos são uma sequência de bytes armazenadas em disco. Nós usamos ilusões para trabalhar com eles. As ilusões que usamos são **campos** e **registros**. Os campos são semelhante aos campos da struct em C, mas a struct é feita para memória primária, já o campo é feito para memória secundária. Já o registro é semelhante à struct. Sendo assim, um registro é composto por 1 ou mais campos. O registro é uma estrutura que determina todas as características de uma entidade do mundo real. Quando vamos armazenar no disco, temos que especificar onde começa e termina cada campo e cada registro, além de quando termina ou não.
## Organização em Campos
Os slides tem erros, pois nas figuras tem bytes offsets após inteiros com delimitadores, sendo que como o inteiro é de tamanho fixo ele não deve ter delimitador (nem mesmo indicador de tamanho). Além disso, o próprio fato de ter inteiros (tamanho fixo) no meio de campos de tamanhos variáveis é um erro, para arrumar é necessário que o inteiro (e todos os outros de tamanho fixo) estejam no começo do registro ou no final.
### Métodos
Temos dois tipos de campo: **fixo** e **variável**. Em campos de tamanhos fixos, todos os campos possuem um tamanho fixo. Já em campos de tamanho variável, para indicar quando termina e quando começa podemos:
- começar cada campo com um indicador de tamanho OU (ou exclusivo)
- colocar delimitadores
### Campos de Tamanho Fixo
Cada campo ocupa no arquivo um tamanho fixo, pré-determinado. Veja abaixo um exemplo de arquivo de dados, considerando a seguinte estrutura:
- nome: string de 12 bytes
- rua: string de 10 bytes
- número: inteiro (4 bytes)
- cidade: string de 20 bytes
![[Pasted image 20250325141510.png]]
Os números azuis representam bytes offset, ou seja, elas indicam deslocamento. Todo arquivo de dados vive na ilusão de que o arquivo começa no byte offset 0. Quando estamos num SO, pegamos o endereço do arquivo e somamos com o byte offset 0 e ai chegamos na posição da memória que está o arquivo de dados.
Quando temos campos de tamanho fixo, o tamanho deles indica o começo e fim do campo.
#### Vantagens e Desvantagens
As vantagens de campos fixos são:
- facilidade na busca/pesquisa, pois sabemos os offsets de cada dado, então podemos ir direto no offset desejado
- indicado para situações nas quais o comprimento dos campos é fixo ou apresenta pouca variação
As desvantagens de campos fixos são:
- desperdício de espaço de armazenamento
- possibilidade de truncamento de dados
- inapropriado para situações nas quais se tem grande quantidade de dados de tamanho variável
### Campos de Tamanho Variável
#### Indicador de Tamanho
O tamanho de cada campo em bytes é armazenado imediatamente antes do dado. Veja o exemplo abaixo.
![[Pasted image 20250325142415.png]]
As vantagens desse método são:
- economia de espaço de armazenamento, mesmo com a necessidade de se gastar alguns bytes adicionais para guardar o tamanho dos campos
- dados não precisam ser truncados
As desvantagens desse método são:
- dificuldade na busca
A busca não pode usar uma fórmula matemática, é necessária uma leitura byte a byte mas é possível pular bytes.
#### Delimitador
Esse método faz o uso de caracteres especiais que não fazem parte do domínio do dado para separar os campos. Eles são escolhidos para serem inseridos ao final de cada campo (ou seja, são armazenados imediatamente depois do dado). Exemplos de delimitadores comumente usados: \, tab, #. Veja o exemplo abaixo que usa o | como delimitador.
![[Pasted image 20250325143516.png]]
As vantagens desse método são:
- não tem truncamento
- sem desperdício (economia) de espaço de armazenamento
As desvantagens desse método são:
- busca byte a byte, sem chance de pular, logo, tem uma dificuldade na busca
- necessidade de escolher um delimitador que não pertence ao domínio dos dados
### Busca
Analisando para facilitar a busca:
- se é possível o campo ser de tamanho fixo, então o campo é de tamanho fixo
- senão o campo é de tamanho variável
	- então o primeiro escolhe o método de indicador de tamanho (pode pular)
	- senão escolhe o delimitador
## Organização em Registros
Como o registro é um conjunto de campo, as ideais aplicadas a campos são aplicadas aos registros.
### Métodos
Os tipos de registros são: fixo e variável. Os registros de tamanhos fixos tem como método: todos os registros possuem o mesmo tamanho fixo. Já os registros de tamanho variável tem dois métodos:
- começar cada registro com um indicador de tamanho
- colocar delimitadores entre registros
### Registro de Tamanho Fixo
Todos os registros têm o mesmo número de bytes. Pode-se ter:
- registros de tamanho fixo com campos de tamanho fixo
- registros de tamanho fixo com campos de tamanho variáveis
Esse é um dos métodos mais comuns de organização de arquivos.
#### Registro de Tamanho Fixo e Campos de Tamanho Fixo
Veja o exemplo abaixo que tem as seguintes características:
- Registros de tamanho fixo: de 46 bytes
- Campos de tamanho fixo:
	- nome: string de 12 bytes
	- rua: string de 10 bytes
	- número: inteiro (4 bytes)
	- cidade: string de 20 bytes
![[Pasted image 20250325145349.png]]
#### Registros de Tamanho Fixo e Campos de Tamanho Variável
Veja o exemplo abaixo que tem as seguintes características:
- Registros de tamanho fixo: de 46 bytes
- Campos de tamanho variável:
	- delimitador: | (caractere de 1 byte)
![[Pasted image 20250325150024.png]]
#### Acesso Direto por RNN
RNN (Relative Record Number) (o primeiro campo tem RNN 0, o segundo tem RNN 1 e assim em diante) é usado para registros de tamanho fixo. Ele fornece a posição relativa de cada registro dentro do arquivo. Ele permite calcular o byte offset no qual cada registro começa. A fórmula usada para achar o byte offset é:
$$byte \, offset = RNN \times tamanho \, do \, registro$$
![[Pasted image 20250325150554.png]]
### Registro de Tamanho Variável
#### Indicador de Tamanho
O tamanho de cada registro em bytes é armazenado imediatamente antes do registro. Os campos devem ser separados por outro método para campos (exemplo: delimitador, indicador de tamanho, etc).
Esse método é muito utilizado para manipular registro de tamanhos variáveis.
![[Pasted image 20250325151540.png]]
#### Delimitadores
Esse método consistem em separar os registros com delimitadores. O delimitador de registro é colocado ao final do registro. Há necessidade de ser usado em conjunto com um método para campos (ex: delimitador, indicador de tamanho, etc).
Veja o exemplo abaixo que tem como delimitador de campo o | e de registro o #.
![[Pasted image 20250325152455.png]]
### Escolha dos registros
- Registro de tamanho fixo - busca facilitada
- registro de tamanho variável
	- indicador de tamanho - pular na busca
	- delimitador - exibe leitura byte a byte sempre
## Organização Híbrida de Campos e Registros
No mundo real, muitas vezes nos deparamos com situações em que temos campos fixos e variáveis na mesma aplicação, ou seja, há uma mistura de campos de tamanho fixo com campos de tamanho variável.
Para resolvermos esse problema, primeiro temos que escolher a organização dos registros (muitas vezes os registros de tamanho fixo ganham dos variáveis).
### Escolha da organização em registros
Temos que escolher a organização que melhor se adequa à aplicação e tem suporte da linguagem de programação.
- Tamanho fixo
	- RNN provê acesso direto aos registros
	- pode haver desperdício de armazenamento ou truncamento dos dados
- Tamanho variável
	- impacta na busca pelos registros
	- acomoda os dados sem desperdício de espaço de armazenamento ou truncamento
Veja o exemplo abaixo.
![[Pasted image 20250325153148.png]]
![[Pasted image 20250325153206.png]]
