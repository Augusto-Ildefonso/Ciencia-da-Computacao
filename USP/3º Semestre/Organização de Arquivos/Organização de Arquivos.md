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
## Sistema de Arquivos
O sistema de arquivos faz parte do SO. Ele fornece a infraestrutura básica para manipulação de arquivos em memória secundária via software. Ela oferece um conjunto de operações para manipulação de arquivos. Por exemplo:
- criar: create, open
- renomear: rename
- fechar: close
- escrever dados: write
- ler dados: read
- posicionar: seek
- destruir ou remover: delete
- abrir: open
- escrever dados no final: append
## Arquivo Físico
O arquivo físico é a sequência de bytes armazenados no disco.
![[Pasted image 20250405125411.png]]
## Página de disco
É o conjunto de setores **logicamente** (ou seja, eles não são necessariamente contíguos no disco físico) contíguos no disco. Um arquivo é visto pelo sistema de arquivos como um conjunto de páginas de disco. Os arquivos são alocados em uma ou mais páginas de disco. Ele é a unidade de transferência de dados entre a RAM e o disco. A página de disco também pode ser chamado de bloco de disco ou cluster (livro).
![[Pasted image 20250405125650.png]]
## Posição corrente no Arquivo
A posição corrente no arquivo é uma abstração que permite a especificação de uma chamada do sistema para indicar onde um arquivo deve ser lido ou escrito. As características dela são:
- A leitura e escrita ocorrem a partir da posição corrente
- A posição corrente é então avançada para imediatamente após o último byte lido ou escrito
- É possível informar um endereço específico a ser lido, o qual faz com que a posição corrente seja a informada no endereço
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
# Remoção Lógica de Registros
## Abordagem Estática de Reuso de Espaço
Até agora só vimos a inserção de registros. Porém vamos ver nesse momento a remoção de registros. Isso é feita com a remoção lógica, que pode ser feita de duas formas:
- atribui um valor para um campo, exemplo: *
- usa um campo extra, exemplo: removido 0 ou  1
Na abordagem estática não faz nada em um intervalo de tempo $\Delta t$. Durante o $\Delta t$, ocorre a remoção lógica:
- registros removidos são marcados, porém não são reaproveitados
- novas inserções são realizadas no final do arquivo
- buscas desconsideram os registros marcados como removidos
Após $\Delta t$, ocorre a remoção física:
- programa é executado para reconstruir o arquivo
- todos os registros removidos são descartados
### Compactação
A compactação de um arquivo é fazer a remoção física dos registros que foram removidos logicamente. A forma mais eficiente de fazer isso é usando dois arquivos:
- Um que eu vou ler ele todo e pegar todas as informações dele, incluindo os registros que serão apagados
- Um segundo arquivo que eu vou escrever tudo, exceto o que foi marcado como removido
### Algoritmo de busca por RNN
1. Se arquivo existe e se arquivo tem dados
2. Abrir arquivo para leitura
3. byte offset = RNN * tamRegistro
4. Posicionar a posição corrente para o byte offset
5. Se encontrou e o registro não foi marcado como removido, então retorna o registro, senão registro não encontrado
6. fechar arquivo
### Algoritmo de inserção por RNN
1. Se arquivo existe
2. Abrir arquivo para escrita
3. Posicionar a posição corrente para o final do arquivo
4. Escrever o registro
5. Fechar arquivo 
### Algoritmo de remoção por RNN
1. Se arquivo existe, se arquivo tem dados...
2. Abrir arquivo para escrita
3. byte offset = RNN * tamRegistro
4. Posicionar a posição_corrente para o byte offset
5. Se encontrou e o registro não foi marcado como removido, então marca o registro como removido, senão registro não encontrado
6. Fechar arquivo
### Algoritmo de compactação
1. Abrir arquivo 1 para leitura
2. Abrir arquivo 2 para escrita
3. enquanto não terminou o arquivo 1
	1. Ler o registro do arquivo 1
	2. Se o registro não foi marcado logicamente como removido
		1. Então escrever o registro no arquivo 2
4. Fechar arquivo 1
5. Fechar arquivo 2
6. Remover arquivo 1
7. Renomear arquivo 2 para arquivo 1
Esse método é bom também pois quando for criar o arquivo 2, já sabemos o tamanho máximo do arquivo e então é possível reservar um tamanho no arquivo do disco e selecionar setores e páginas sequenciais para armazenar. Enquanto o arquivo 1, que não sabia a quantidade máxima, tem seus dados gravados em diferentes setores do arquivo.
### Abordagem estática
Essa técnica pode ser aplicada a:
- registros de tamanho fixo
- registros de tamanho variável
A frequência para se aplicar a técnica depende da aplicação e da porcentagem de registros marcados como removidos. Além disso, é usada quando tenho certeza que terá pouca remoção e inserção nos arquivos.
## Abordagem Dinâmica
Essa abordagem é indicada para aplicações interativas que acessam arquivos altamente voláteis. Os principais desafios dela são:
- marcar registros como logicamente removidos
- identificar se existem registros marcados como logicamente removidos, ou seja, se existem espaços a serem reaproveitados
- localizar os espaços ocupados por esses registros logicamente removidos sem realizar buscas exaustivas
### Registros de Tamanho Fixo
A solução para esses tipos de registros é usar uma lista encadeada de registros eliminados. As características dessa lista são:
- A lista constitui-se dos RNNs dos registros marcados como logicamente removidos
- A cabeça da lista é armazenada no registro de cabeçalho do arquivo
- A inserção e reuso de espaço ocorrem sempre no início da lista
Para implementar essa lista será usada uma pilha.
Os algoritmos são:
- Na remoção de um registro de dados, marca o registro como logicamente removido e insere o registro na lista de registros logicamente removidos (empilha). 
- Na inserção de um registro de dados, remove o registro da lista de registros logicamente removidos (desempilha) e insere os dados no espaço do registro desempilhado. 
- Na atualização de um registro de dados ocorre no registro propriamente dito.
### Registros de Tamanho Variável
A solução para esses tipos de registros é usar uma lista encadeada de registros eliminados também. As características dessa lista são:
- A lista constitui-se dos bytes offsets dos registros marcados como logicamente removidos
- A cabeça da lista é armazenada no registro de cabeçalho do arquivo
- É preciso de um dado adicional para guardar também o tamanho do registro
Para implementar a lista usaremos uma lista mesmo.
Os algoritmos são:
- Na remoção de um registro de dados, marca o registro como logicamente removido e insere o registro na lista de registros logicamente removidos (empilha ou insere ordenado na lista)
- Na inserção de um registro de dados, remove o registro da lista de registros logicamente removidos (de acordo com o tamanho solicitado) e insere os dados no espaço do registro desempilhado.
- Na atualização de um registro de dados, pode requerer remoção e posterior inserção
Para fazer o reuso do espaço que foi marcado como logicamente removido temos o seguinte algoritmo:
- Fazemos uma busca sequencial na lista
- Se encontro espaço disponível no tamanho adequado
	- Então reaproveita o espaço para armazenar o novo registro, usando uma estratégia de alocação
	- Senão, insere o novo registro no final do arquivo
O tamanho do registro que foi removido deve ser do tamanho adequado, ou seja, grande o suficiente para armazenar os dados do novo registro que for usar aquele espaço. Para encontrar o espaço correto temos três estratégias:
- First-Fit: utiliza o primeiro espaço que servir, nessa estratégia, pode sobrar lixo dentro do registro, o que é conhecido como fragmentação interna.
- Best-Fit: escolhe o espaço mais justo possível
- Worst-Fit: escolhe o maior espaço possível
# Estruturas de Indexação de Dados
## Índice
O índice é uma estrutura de acesso auxiliar usada para melhorar o desempenho na recuperação de registros. Ele ajuda pois ele restringe a pesquisa a um subconjunto dos registros, em contrapartida à análise do conjunto completo, ou então faz com que ela seja realizada em resposta a certas condições. Além disso, com ele não é necessário ordenar o arquivo de dados, nem quando novos registros são adicionados.
A estrutura de dados do índice é definida em termos das características do índice, ou seja, dos registros de dados. As operações que podemos realizar são:
- Pesquisa/busca
- Criação
- Inserção
- Remoção
- Atualização
- Destruição
- Carregamento
- Reescrita
A busca é baseada na chave de busca. O algoritmo dela é:
- Encontra a posição da chave no arquivo de índice
- Obtém o RRN ou o byte offset do registro correspondente à posição encontrada
- Encontra o registro no arquivo de dados
- Recupera o registro solicitado do arquivo de dados
Quando criamos um índice juntamente com a criação do arquivo de dados, criamos apenas o registro de cabeçalho. Entretanto, quando criamos o índice baseado em um arquivo já existente criamos o registro de cabeçalho e os demais registros (como chave de busca e campo de referência) que são obtidos a partir de uma varredura no arquivo de dados.
A inserção adiciona registros no índice devido às inserções no arquivo de dados. Uma inserção de um novo registro no arquivo de dados, que é feita no arquivo não ordenado, ou seja, é realizada no final do arquivo ou com reaproveitamento de espaço, implica na inserção de um novo registro no arquivo índice, que tem necessidade de reorganização do índice, devido à ordenação da chave.
A remoção remove registros no índice devido às remoções no arquivo de dados. Logo, uma remoção de um registro no arquivo de dados, que é lógica (há reaproveitamento de espaço), implica em uma remoção de um registro no arquivo de índice, essa inserção geralmente é física (resultando no deslocamento dos registros) mas pode ser lógica também.
A atualização modifica registros no índice devido às modificações no arquivo de dados. Temos algumas formas de fazer a atualização:
- Remoção seguida de inserção (técnica mais utilizada)
- Campo chave: reordenação do índice
- Campo não chave: ajuste do campo de referência se o registro mudar fisicamente no arquivo de dados
A destruição exclui o arquivo de índice. As demais funcionalidades relacionadas são realizadas diretamente sobre o arquivo de dados.
O carregamento carrega o arquivo de índice na memória principal antes de usá-lo. O passo a passo é:
- Aponta para o primeiro registro do arquivo de índice em disco
- Varre o arquivo de índices sequencialmente
- Cria o índice em memória principal, em geral implementado como um vetor
Por fim, a reescrita atualiza o arquivo de índice em disco com base no arquivo de índice em memória principal, quando necessário. Ele pode ser usado também para colocar alguma informação adicional, como o status no registro de cabeçalho (que indica inconsistência nos índices, devido à queda de energia, travamento do programa de atualização, etc).
## Índice Simples ou Linear
### Tipos de Índice
A princípio temos dois tipos de índice: primário e secundário. O índice primário é definido sobre um campo sem repetição. Já um índice secundário é definido sobre um campo com repetição. É importante ressaltar que essas classificações são diferentes das encontradas em bancos de dados, apesar de compartilharem o mesmo nome.
O índice secundário pode ainda ser dividido em dois tipo: fracamente ligado (loosely binding) e fortemente ligado (tight binding).
Apesar de simples, os índices proporcionam ferramentas poderosas para a recuperação de registros. Veja abaixo um esquema da estrutura de dados de um índice.
![[Captura de tela 2025-05-10 101242.png]]
Cada registro do índice contém pelo menos 2 campos de tamanho fixo: chave e posição inicial (byte offset) ou RRN do registro no arquivo de dados.
### Índice Primário
O índice primário é aquele definidos sobre campos que não possuem repetição. Veja um exemplo abaixo.
![[Pasted image 20250510101553.png]]
Na direita temos o índice e na esquerda o arquivo de dados. Perceba que o índice é formado pela junção de dois campo que assim formam identificadores únicos para cada registro, desse modo é possível definir criar índice primário.
Outra observação importante é que no índice temos valores ordenados, enquanto no arquivo de dados os registros estão desordenados.
Temos o índice com campos e registros de tamanho fixo enquanto o arquivo de dados tem campos e registros de tamanho fixo ou variável.
### Índice Secundário
#### Fracamente Ligado
![[Pasted image 20250510101936.png]]
O índice é dito fracamente ligado quando aplicamos ele sobre um índice primário. Aqui aplicamos um índice secundário sobre os dados do índice primário. Repare que o índice secundário é ordenado e permite repetição de valores. 
#### Fortemente Ligado
![[Pasted image 20250510102150.png]]
O índice é dito fortemente ligado quando aplicamos ele sobre o arquivo de dados. Repare novamente que ele é ordenado e possui repetição, mas agora ele foi aplicado diretamente sobre o arquivo de dados.
### Repetição de Valores
Quando temos repetição de valores temos dois problemas:
- Necessidade de armazenar a mesma chave secundária várias vezes
- Necessidade de reordenar os índices sempre que um novo registro é inserido no arquivo (mesmo que esse registro já tenha um valor de chave secundária já existente no arquivo)
Para isso temos algumas melhorias que amenizam esses problemas, são elas: vetores de tamanho fixo e lista invertidas.
#### Vetores de Tamanho Fixo
Associa-se um vetor de tamanho fixo a cada chave secundária. Veja o exemplo abaixo.
![[Pasted image 20250510102456.png]]
#### Listas Invertidas
Associa-se uma lista encadeada das chaves primárias a cada chave secundária. Ou seja, temos uma lista encadeada das chaves e cada elementos aponta para um arquivo diferente que tem uma lista das chaves secundárias. Desse modo quando formos inserir, por exemplo, percorremos a lista inicial até achar a chave que queremos, então abrimos o arquivo que ela indica e adicionamos o valor nele.
### Conclusão
O índice simples ou linear é adequado quando cabe em memória primária. Se ele for armazenado em memória secundária:
- Pode requerer vários acessos a disco, por causa da busca binária
- Pode ter manutenção cara, devido à adição e remoção de registros
- Requer o uso de outras organizações mais apropriadas, como árvore-B