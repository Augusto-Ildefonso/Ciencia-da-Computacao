# Definições e Conceitos
Mídia, para computação, é um meio de representação, armazenamento, distribuição e apresentação de informações. Por exemplo: Texto, gráficos, fala, música, imagens estáticas e moventes, MP3, ASCII, entre outras. 
Já multimídia é o uso simultâneo de diferentes tipos de mídia (duas ou mais), integradas por um computador, desde que se defina e classifique mídia em termos técnicos da área de computação e o entendimento de multimídia esteja no contexto de sistema multimídia.
## Classificando mídia
Sabemos que multimídia representa uma variedade de mídias. Essas podem ser classificadas de acordo com diferentes critérios.
### Percepção
Em um sistema multimídia, a informação é apresentada a pessoas. Por isso, elas deveriam envolver os nossos 5 sentidos. As mídias atuais podem ser visuais ou auditivas, os outros sentidos não tem devido a falta de maturação da tecnologia, apesar de existirem alguns casos de uso dos outros sentidos (exemplo: vibrações no controle do videogame). Nesse cenário, imagens, vídeos e texto podem ser consideradas mídias visuais, enquanto música e fala mídias auditivas.
### Representação
Nesse tipo de classificação analisamos como a mídia é representada internamente pelo computador. Ou seja, nos referimos aos formatos, como a informação é representada para ser "entendida" pelo computador. Por exemplo, texto pode ser representado por ASCII, sinais de áudio podem ser representados por PCM, imagem pode ser por PCM ou JPEG e vídeo pode ser por PCM ou MPEG.
### Apresentação
Essa classificação se refere às ferramentas e dispositivos para entrada e saída da informação. Ou seja, como a informação é apresentada pelo computador. O papel, tela e alto falantes são mídias de saída, enquanto o teclado, mouse, microfone e câmera são meios de entrada.
### Armazenamento
Essa classificação se refere à onde a informação é armazenada: papel, HD, CVC, etc.
### Transmissão
Essa classificação se refere às diferentes portadoras que habilitam a transmissão contínua (o fato de ser contínua que diferencia ela das mídias de armazenamento) da informação: cabo, fibra óptica, ar, entre outros.
### Discretas ou Contínuas
As mídias discretas são aquelas independentes do tempo. O processamento das informações não é crítico em relação ao tempo, pois a validade (ou precisão) dos dados não depende do tempo de processamento. Exemplo: textos e imagens.
Já as mídias contínuas são dependentes do tempo. O processamento de dados e a representação dependem do tempo. Os valores de representação ocorrem periodicamente e a sua interpretação correta depende do tempo de processamento. Exemplo: vídeo, áudio e animações.
## Sistemas Multimídia
As principais propriedades de um sistema multimídia são:
- Combinação de mídias: deve incluir duas ou mais mídias
- Independência entre mídias: isso permite processamento independente das mídias e flexibilidade para combinar mídias de diferentes modos
- Integração auxiliada por computador: tem que ter um computador realizando a integração. A independência de mídia possibilita combinações arbitrárias.
- Sistemas de comunicação (isso é mais antigo e opcional): um sistema multimídia deve poder se comunicar com outro. Os dados transmitidos podem ser discretos ou contínuos. Na prática, esse conceito é flexível
# Introdução à Teoria da Informação e Técnicas de Compressão
## Introdução à Técnicas de Compressão
### Por quê comprimir?
A compressão é importante para preencher o "gap" entre a demanda e a capacidade de armazenamento. Os usuários tem demandado aplicações com mídias cada vez mais sofisticadas. Porém, os meios de transmissão e armazenamento são limitados.
### Tipos de algoritmos de compressão
Há dois tipos principais de compressão: com perda e sem perda.
#### Compressão sem perda
Também chamado de *Lossless*, esse tipo de compressão é reversível. Ela busca reduzir o número de informações transmitidas de um jeito que quando descomprimimos a informação, não há perdas de informação. Exemplo de mídias que usam esse algoritmo: texto.
#### Compressão com perda
Também chamado de *Lossy*, esse tipo de compressão não é reversível (é possível trazer uma cópia parecida com a original mas não exata). O objetivo desse tipo de compressão não é reproduzir uma cópia exata da informação original após a descompressão, mas sim gerar uma versão que é percebida como uma cópia verdadeira (ela usa a capacidade do olho ou audição humana para conseguir manter essa percepção de que é uma cópia verdadeira quando ela não é). Nesse tipo de compressão tem uma relação entre a taxa de compressão e a qualidade, quanto maior a compressão, menor a qualidade e vice-versa. Exemplo de mídias que usam esse algoritmo: imagem, áudio.
## Compressão sem perdas
Uma compressão sem perda se baseia na quantidade mínima de bits necessária para representar uma informação sem que ocorram perdas.
### Teoria da informação
A teoria da informação é uma ferramenta matemática para determinar a quantidade mínima de dados para representar informação. A premissa dela é a geração da informação pode ser modelada como um processo probabilístico, para isso ela parte do princípio da incerteza.
A ideia central é que a quantidade de informação associada a um evento está diretamente ligada à sua incerteza (ou probabilidade de ocorrer). Quando mais improvável um evento for, maior será a quantidade de informação que ele carrega. Por outro lado, eventos certos (probabilidade 1) não trazem nenhuma informação nova. Em outras palavras, considerando $E$ um evento e $I(E)$ a quantidade de informação que o evento traz, temos que o princípio da incerteza consiste na ideia: Se $P(E) = 1 \longrightarrow I(E) = 0$ e $I(E) = \log \frac{1}{P(E)} = -\log P(E)$ unidades de informação. Sendo assim, se $P(E)$ é pequeno, o evento traz muita informação ($I(E)$ é grande).
#### Teorema de Shannon
Um outro conceito central na Teoria da informação é o teorema de Shannon. Ele criou uma teoria matemática para entender como a informação é transmitida em canais de comunicação e armazenada. Seu trabalho inclui:
- Entropia: medida da incerteza ou aleatoriedade em um conjunto de símbolos (ex: letras, números, pixels)
- Capacidade de canal: limite máximo de informações que podem ser transmitidas por um canal sem erros
Desse estudo ele obteve a fórmula de Shannon:
$$H^{n}_{i = 1} = - \sum P_{i} \, \log_{2} \, P_{i}$$
Onde $n$ é o número de diferentes símbolos da nossa representação (ex: 26 letras do alfabeto, 256 cores em uma imagem), $P_{i}$ é a probabilidade de ocorrência do símbolo $i$ e o $H$ é chamado de entropia. 
A entropia vai nos dar o valor mínimo de compressão que dá para obter. Ela mede a incerteza média de uma fonte de dados. Assim, quanto maior a entropia, mais aleatória é a fonte, e mais difícil é comprimir os dados.
A eficiência mede o quão perto um algoritmo de compressão está do limite teórico definido pela entropia. Um esquema é eficiente quando $NMB$ está próximo de $H$. Quanto maior a diferença entre $NMB$ e $H$, menor é a eficiência.
A eficiência de um esquema de compressão pode ser analisada comparando a entropia da fonte (limite teórico mínimo de bits necessários para representar dados) com o número médio de bits por código do esquema (desempenho real do algoritmo de compressão). O número médio de bits por código é dado por:$$NMB = \sum^{n}_{i = 1} N_{i} P_{i}$$Onde $N_{i}$ é o número de bits atribuídos ao símbolo $i$ pelo algoritmo de compressão, $P_{i}$ é a probabilidade de ocorrência do símbolo $i$ e $n$ é o total de símbolos diferentes.

### Objetivos e Problemas
O objetivo da compressão sem perdas é gerar códigos com a quantidade mínima possível de bits.
Os problemas desse tipo de compressão são:
- Tamanho do código: fixo ou variável
- Propriedade do prefixo: nenhum código de tamanho menor pode ser prefixo de um código de tamanho maior
- Como gravar apenas os bits dos códigos gerados?
### Codificação por Entropia
A codificação por entropia é sem perdas e independe do tipo de informação que está sendo comprimida. Ela só está preocupada com a forma que a informação é representada. Vejamos alguns algoritmos de codificação por entropia.
#### Codificação por Carreira (Run-Length Encoding)
Esse algoritmo é útil quando queremos codificar longas cadeias do mesmo caracter ou dígito. Nela, ao invés de transmitirmos as informações na forma de palavras-código independentes ou bits, ela é transmitida na forma de um conjunto de palavras-código que indicam não somente o caracter particular ou o bit, mas também uma indicação do número de caracteres ou bits da string. Assim, desde que o receptor já saiba o conjunto de palavras-código usado, ele simplesmente interpreta cada palavra-código e mostra o número apropriado de caracteres ou bits.
Por exemplo, se temos uma cadeia de binários, como:
$$000000011111111110000011...$$
Ao invés de transmitir a strings acima de $0$'s e $1$'s, nós podemos transmitir uma string de palavras-código em cada conjunto de palavra-código representa o bit que está sendo transmitido ($0$ ou $1$) e o número de bits da substring. Sendo assim, a cadeia acima seria representada por: 
$$0,7 \,\,\,\,\, 1,10 \,\,\,\,\, 0,5 \,\,\,\,\, 1,2 \,\,\,\,\, ...$$
Uma outra opção é que se garantirmos que a substring começa com 0, podemos representar: 
$$7, 10, 5, 2, ...$$
Para enviar as palavras-códigos de forma digital, enviamos cada dígito decimal na sua forma binária e, assumindo um número fixo de bits por palavra-código, o número de bits por palavra código seria determinada pela maior substring possível.
#### Codificação por Diferença
A codificação por diferença é usada extensivamente em aplicações onde a amplitude do valor ou sinal sobre um grande intervalo mas a diferença de amplitude entre valores/sinais sucessivos é relativamente pequeno. Ele usa um conjunto pequeno de palavras-códigos para representar somente a diferença de amplitude entre o valor/sinal atual e o seu sucessor.
Na prática, codificação por diferença pode ser tanto com perda quanto sem perda. Ela depende do número de bits usado para codificar o valor das diferenças. Se o número de bits usado é suficiente para lidar com valor máximo de diferença, então é sem perda. Se não é o caso, então nos momentos que o valor da diferença ultrapassa o valor máximo de bits usado, temporariamente será com perda.
#### Codificação de Huffman
Esse algoritmo resolve o problema do prefixo. Ele é um método estatístico que faz análise da frequência relativa dos símbolos. Ele usa árvores binárias não balanceadas, nas quais os símbolos estão nas folhas (essa árvore também é chamada de árvore de huffman)
Na codificação de Huffman, a string que será transmitida é analisada e os tipos de caracteres e as suas respectivas frequências relativas são determinadas (os símbolos com maior frequência devem ter os menores códigos). A operação de codificação envolve criar árvores binárias não balanceadas com alguns ramos (ou seja, palavras-código) mais curtos que outros. O grau de desbalanceamento é uma função da frequência relativa de ocorrências de caracteres: quanto maior a dispersão, mais desbalanceada é a árvore. A árvore resultante desse processo é chamada árvore de Huffman.
Uma árvore de Huffman é uma árvore binária na qual os ramos tem os valores 0 ou 1 atribuídos a eles. A base da árvore geralmente é chamada de nó raiz e ponto que divide um ramo é chamado de nó de ramificação. O ponto em que um ramo termina é chamado de nó folha e é nele que os símbolos que estão sendo codificados são atribuídos.
Quando um ramo é dividido, o valor binário 0 ou 1 é atribuído para cada novo ramo: 0 para o ramo à esquerda e 1 para o ramo à direita. A palavra-código usada para cada caracter, que está nos nós folha, é determinada traçando o caminho do nó raiz até o nó folha referente ao caracter, formando uma string de valores binários associado com cada ramo traçado.
![[Pasted image 20250501145806.png]]
Para ilustrar como a árvore de Huffman acima foi gerada, devemos adicionar informações referentes às frequências de ocorrência de cada caracter. A primeira etapa envolve atribuir os valores (1) e (0) aos ramos dos dois primeiros nós folha da lista — C1 e D1 — em relação a um nó de ramificação. Em seguida, esses dois nós folha são substituídos por um novo nó de ramificação cujo peso é a soma dos pesos dos dois nós folha; nesse caso, dois. Uma nova coluna é então formada, combinando esse novo nó com os demais nós restantes da primeira coluna, novamente ordenados pelo seu peso correto. Esse procedimento é repetido até que apenas dois nós permaneçam.
Para derivar as palavras-código correspondentes a cada caractere, começamos pelo caractere na primeira coluna e listamos os números dos ramos — 0 ou 1 — à medida que são encontrados. Assim, para o caractere A , o primeiro (e único) número do ramo é (1) na última coluna, enquanto para o caractere C , o primeiro número é (1) no nó de ramificação 2 e, finalmente, (0) no nó de ramificação 4. No entanto, as palavras-código reais são o inverso dessas sequências de bits. A árvore de Huffman pode então ser construída facilmente a partir desse conjunto de palavras-código.
Verificamos que essa é a árvore ótima — e, portanto, o conjunto de palavras-código ótimas — listando os pesos de todos os nós folha e de ramificação da árvore, começando pelo menor peso e prosseguindo da esquerda para a direita e de baixo para cima. As palavras-código são consideradas ótimas se a lista resultante incrementa conforme a ordem dos pesos. 
Ou seja, monta-se uma lista ordenada pela frequência. Então pegamos os dois primeiros elementos e atribuímos eles para os ramos 0 e 1. Se o peso do nó de ramificação resultante for maior do que o peso dos outros elementos, temos que inserir o nó na posição certa de acordo com a ordenação. Então repetimos os procedimentos até que só tenham dois elementos na lista. A árvore ótima é aquela que todas as folhas e nós de ramificações incrementam em ordem numérica.
Como cada caracter codificado tem um número variável de bits, o receptor deve interpretar o sinal de forma orientada a bits e não de forma fixa de 7 a 8 bits, por exemplo. Por casa da ordem em que os bits são atribuídos durante o processo de codificação, as palavras-códigos de Huffman tem a propriedade que uma palavra-código menor, nunca vai formar o começo de uma palavra-código maior. Essa propriedade é conhecida como **propriedade do prefixo** e ela implica que uma cadeia de bits recebida pode ser decodificada simplesmente por uma busca recursiva bit a bit até que cada palavra-código válida é achada (ou seja, nenhum código é prefixo de outro código maior).
Veja abaixo um fluxograma do processo de decodificação.
![[Pasted image 20250501165927.png]]
O algoritmo de decodificação assume que uma tabela de palavras-códigos está disponível no receptor e ela também possui o caracter correspondente à palavra-código. A cadeia de bits recebida é armazenada na variável ``BITSTREAM`` e a variável `CODEWORD` é usada para armazenar os bits em cada palavra-código, enquanto ela está sendo construída. Quando uma palavra-código é identificada, o caracter correspondente é escrito na variável `RECEIVE_BUFFER`. O procedimento é repetido até que todos os bits da string tenham sidos processados.
Como a árvore de Huffman varia para diferentes conjuntos de caracteres transmitidos, o receptor para fazer a decodificação deve saber as palavras-códigos referentes aos dados transmitidos. Isso pode ser feito de dois modo: ou as palavras-códigos referentes ao próximo conjunto de dados são enviadas antes dos dados, ou o receptor sabe antecipadamente quais palavras-códigos são usadas.
Essa primeiro modo leva à uma compressão adaptativa, já que as palavras-códigos podem mudar para se adequar o tipo de dado que está sendo transmitido. A desvantagem é o overhead de ter que enviar o novo conjunto de palavras-códigos (e os caracteres correspondentes) sempre que um novo tipo de dado for enviado. Uma alternativa é o receptor ter um ou mais conjuntos de palavras-códigos e para o transmissor indicar ao receptor qual o conjunto será usado no próximo conjunto de dados. Por exemplo, para enviar arquivos de texto no idioma Inglês, já foram feitos estudos para analisar a frequência de cada letra em textos em inglês, assim o receptor e transmissor poderiam usar esses dados para construírem a árvore de Huffman. A desvantagem é que esse método não é exato, então alguns textos não vão atingir o máximo de compressão que poderiam.
#### Codificação Aritmética
A codificação de Huffman só atinge o valor de Shannon se a probabilidade dos símbolos são todos inteiros e potências de $\frac{1}{2}$. Obviamente, muitas vezes esse não é o caso, então o conjunto de palavras-código produzidas são raramente ótimos. Em contrapartida, as palavras-código produzidas usando codificação aritmética sempre atingem o valor de Shannon. Entretanto, ela é mais difícil que a de Huffman, por isso será estudada somente a versão básica e estática da operação.
Para ilustrar como a codificação ocorre, considere a transmissão da mensagem comprimindo a string de caracteres com probabilidade: 
$$e = 0.3 \,\,\,\,\,\, n= 0.3 \,\,\,\,\,\, t = 0.2 \,\,\,\,\,\, w = 0.1 \,\,\,\,\,\, . = 0.1$$
No final de cada string que compõe a mensagem, um caracter conhecido será enviado, no caso é o ponto final. Quando for decodificado, o decodificador interpreta esse caracter como o terminador de string.
Diferentemente do Huffman que para cada caracter há uma palavra-código, na codificação aritmética temos uma palavra-código para cada string de caracteres codificada. O primeiro passo é dividir o intervalo numérico de 0 a 1 no número de diferentes caracteres presentes na mensagem a ser enviada, incluindo o terminador de string, e o tamanho de cada segmento será definido pela probabilidade do caracter. Veja o exemplo abaixo para os caracteres que mencionamos antes.
![[Pasted image 20250501194750.png]]
Como pode-se ver, temos 5 caracteres, logo temos 5 segmentos e cada um tem seu tamanho relacionado com a probabilidade do caracter. Importante ressaltar que uma probabilidade no intervalo, $0.8$ a $0.9$ por exemplo, tem probabilidade no intervalo acumulativo de $0.8$ a $0.8999999...$. Uma vez que fizemos essa divisão, podemos começar a codificação. Vamos usar a palavra `went.` como nossa string no exemplo de codificação.
O primeiro caracter a ser codificado é o `w` que está no intervalo $0.8$ a $0.9$. Então veremos que o valor final é um número entre $0.8$ a $0.8999999...$, pois os próximos caracteres dividiram o intervalo $0.8$ a $0.9$ em intervalos cada vez menores, de acordo com a probabilidade dos caracteres.
Partindo para o próximo caracter `e`. Agora estamos no intervalo de $0.8$ a $0.9$ e precisamos dividi-lo novamente de acordo com as probabilidades de cada caracter. Uma vez dividido pegamos o intervalo do `e` que é $0.8$ a $0.83$. Então subdividimos novamente e agora o `e` tem intervalo $0.8$ a $0.809$ ($0.8 + 0.3 \times 0.03$). Em seguida, o `n` que vai de $0.83$ a $0.86$ e assim em diante. Continuamos essa processo até o caracter de terminação de string. Nesse momento, o segmento do  `.` está no intervalo de $0.81602$ a $0.8162$, então, a palavra-código para a string completa é qualquer número entre o intervalo: 
$$0.81602 \leq palavra-código \leq 0.8162$$
No modo estático, o decodificador sabe o conjunto de caracteres que estão presentes na mensagem codificada que ele recebe, assim como o segmento que cada caracter foi atribuído e o seu intervalo relativo. Assim, o decodificador pode seguir o mesmo procedimento para determinar a string de caracteres relacionada com cada palavra-código recebida.
Como podemos perceber, o número de dígitos da nossa palavra-código final aumenta linearmente conforme o número de caracteres da string codificada aumenta. Logo, o número máximo de caracteres em uma string é determinado pela precisão com que os números de ponto flutuante são representados no computador de origem e destino. Como resultado, uma mensagem completa pode ser fragmentada em diversas strings menores. Cada string é então codificada separadamente e o resultado do conjunto de palavras-código é enviado como um bloco (binário) de pontos flutuantes, cada um em um formato conhecido. 
# Áudio
## O que é o som?
O som é um fenômeno físico e é uma onda mecânica.
## Características físicas do som
### Amplitude
A amplitude é a intensidade. Ela está relacionada ao volume do som. Quanto maior a amplitude, mais alto ouvimos o som. A amplitude é medida em decibeis (dB).
![[Pasted image 20250508172045.png]]
### Frequência
A frequência determina a altura do som (ou seja, altura é diferente de volume). Frequências altas tem uma altura maior e geram sons agudos. Já frequências baixas tem altura menor e geram sons graves.
![[Pasted image 20250508172122.png]]
## Digitalização de áudio
### Princípios de Digitalização
A princípio temos duas transformações:
- Eletrônica: conversão de ondas mecânicas em sinais elétricos
- Digital: conversão de sinais elétricos em bits
A transformação eletrônica trabalha com um sinal de áudio que é analógico.
Veja abaixo um sinal analógico e suas componentes.
![[Pasted image 20250508172235.png]]
Aqui temos a frequência sendo a taxa com que o sinal varia entre valores positivos e negativos. Ela é medida em Hertz (Hz). Já a amplitude é a diferença entre os máximos valores positivos e negativos do sinal de áudio, ela pode ser expressa observando-se a voltagem (dependente do sistema) e normalmente é expressa em decibéis (dB).
A conversão de analógico para digital leva em conta a voltagem e o tempo. Nós fazemos uma amostragem, ou seja, realiza leituras periódicas e instantâneas da voltagem em espaço de tempo uniforme. Em seguida, fazemos uma quantização que converte os valores analógicos amostrados em valores digitais.
### Amostragem
Deve-se fazer a amostragem usando o mesmo valor para os intervalos de amostragem.
![[Pasted image 20250508173316.png]]
Agora nos deparamos com um problema: quanto deve ser amostrado? Bem, se quisermos reconstruir o sinal de antes precisaremos de infinitas amostragem. Mas também se fizermos poucas amostragem o sinal fica distorcido.
Para responder essa dúvida, usamos o Teorema de Nyquist: "Para obter uma representação precisa de um sinal analógico, sua amplitude deve ser amostrada a uma taxa mínima igual ou superior ao dobro da componente de mais alta frequência presente no sinal". Isso ficou conhecido como Taxa de Nyquist.
Se fizermos a amostragem seguindo o Teorema de Nyquist, nós evitaremos o aliasing. O aliasing, também conhecido como dobramento da frequência, ocorre quando pegamos um valor abaixo da taxa de Nyquist, o que leva a distorções. Veja abaixo o sinal analógico real e o aliasing dele.
![[Pasted image 20250508174112.png]]
Para evitar o aliasing, usamos filtros anti-aliasing, que removem os componentes de alta frequência.
Em sistemas multimídia, a largura de banda do canal é normalmente menor que a largura de banda do sinal. Por causa disso, a taxa de amostragem é determinada pela largura de banda do canal. Além disso, a taxa de Nyquist será baseada na frequência mais alta suportada pelo canal.
### Quantização
A quantização é o processo pelo qual os valores analógicos das amostras tomadas da amplitude são convertidos em valores digitais. Para reconstruir o sinal precisaríamos de um número infinito de bits, o que não é viável. Então, usando um número finito de bits, representa-se cada amostra através de um número correspondente de níveis discretos.
![[Pasted image 20250508174822.png]]
Para fazer a amostragem e quantização é importante perceber que há uma relação entre o número de amostras e o número de níveis. É importante, também, ressaltar que a quantização resulta em distorções.
### Digitalização
Temos as seguintes taxas comuns de amostragem:
- 8000 Hz
- 11025 Hz
- 22050 Hz
- 44100 Hz
Temos as seguintes quantidades comuns de bits por amostra:
- 4
- 8
- 16
- 24
Temos os seguintes canais de som:
- 1 (mono)
- 2 (stereo)
- 3
- 5
- 7
- ...
Um padrão comum é a qualidade de CD: amostras a 44100 Hz (4,1 kHz), 16 bits por amostra e 2 canais de som (estéreo).
O circuito que realiza amostragem e quantização é o conversor analógico-digital (analog to digital converter - ADC). O caminho inverso dele, DAC, é usado para reprodução de áudio digital. Ele normalmente é implementado em hardware. Veja abaixo seu circuito.
![[Pasted image 20250508175633.png]]
Após a captura, os dados amostrados e quantizados devem ser guardados em algum formato (mídia de representação). Os mais comuns são WAV e MP3.
Olhando agora os aspectos quantitativos da digitalização, se quisermos saber quantos bytes serão necessários para armazenar 1 segundo de áudio, capturado com qualidade de CD, como fazermos?
Podemos realizar a segunda operação:
$$1 \, (segundo) \times 44.100 \, (taxa \, de \, amostragem) \times 2 \, (16 \, bits \, por \, amostra) \times 2 \, (som \, estéro) = 176.400 \, bytes$$
Então para transmitir esse áudio precisamos de 1,41 Mbps.

(ver dos slides)
- 8000 Hz -> fala, telefonia
- 44100 Hz -> para música

- 4 bits -> telefonia mas voz estranha
- 8 bits -> telefonia usada hoje
- 16 bits -> tele conferência
# Vídeo Digital
## Codificação do Modelo Temporal