# Definições e Conceitos
## Definindo mídia e multimídia
Mídia, para computação é um meio de representação, armazenamento, distribuição e apresentação de informações. Por exemplo: Texto, gráficos, fala, música, imagens estáticas e moventes, MP3, ASCII, entre outras. Já multimídia é o uso simultâneo de diferentes tipos de mídia (duas ou mais), integradas por um computador, desde que se defina e classifique mídia em termos técnicos da área de computação e o entendimento de multimídia esteja no contexto de sistema multimídia.
## Classificando mídia
Para poder definir melhor mídia vamos usar a classificação delas. As mídias podem ser classificadas em alguns tipos.
### Percepção
Essas mídias podem ser visuais ou auditivas, os outros sentidos não tem devido a falta de maturação da tecnologia, apesar de existirem alguns casos de uso dos outros sentidos (exemplo: vibrações no controle do videogame).
### Representação
Nos referimos aos formatos. Como a informação é representada para ser "entendida" pelo computador.
### Apresentação
Como a informação é apresentada pelo computador. Ferramentas e dispositivos para entrada e saída de informação
### Armazenamento
Onde a informação é armazenada: papel, HD, CVC, etc.
### Transmissão
Portadoras que habilitam a transmissão <span style="color:rgb(0, 132, 255)">contínua</span> (o fato de ser contínua que diferencia ela das mídias de armazenamento) da informação: cabo, fibra óptica, ar, entre outros.
### Discretas ou Contínuas
As mídias discretas são aquelas independentes do tempo. O processamento das informações não é crítico em relação ao tempo, pois a validade (ou precisão) dos dados não depende do tempo de processamento. Exemplo: textos e imagens.
Já as mídias contínuas são dependentes do tempo. Os valores de representação ocorrem periodicamente e a sua interpretação correta depende do tempo de processamento. Exemplo: vídeo, áudio e animações.
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
Também chamado de *Lossless*, esse tipo de compressão é reversível. Exemplo de mídias que usam esse algoritmo: texto.
#### Compressão com perda
Também chamado de *Lossy*, esse tipo de compressão não é reversível (é possível trazer uma cópia parecida com a original mas não exata). Nesse tipo de compressão tem uma relação entre a taxa de compressão e a qualidade, quanto maior a compressão, menor a qualidade e vice-versa. Exemplo de mídias que usam esse algoritmo: imagem, áudio.
## Compressão sem perdas
Uma compressão sem perda se baseia na quantidade mínima de bits necessária para representar uma informação sem que ocorram perdas.
### Teoria da informação
A teoria da informação é uma ferramenta matemática para determinar a quantidade mínima de dados para representar informação. A premissa dela é a geração da informação pode ser modelada como um processo probabilístico, para isso ela parte do princípio da incerteza.
#### Teorema de Shannon
Ele estudou a transferência de informação em canais de comunicação. Desse estudo ele obteve a fórmula de Shannon:
$$H^{n}_{i = 1} = - \sum P_{i} \, \log_{2} \, P_{i}$$
Onde $n$ é o número de diferentes símbolos, $P_{i}$ é a probabilidade de ocorrência do símbolo $i$ e o $H$ é chamado de entropia. A entropia vai nos dar o valor mínimo de compressão que dá para obter.
A eficiência de um esquema de compressão pode ser anali (pegar dos slides)
### Objetivos e Problemas
O objetivo da compressão sem perdas é gerar códigos com a quantidade mínima possível de bits.
Os problemas desse tipo de compressão são:
- Tamanho do código: fixo ou variável
- Propriedade do prefixo: nenhum código de tamanho menor pode ser prefixo de um código de tamanho maior
- Como gravar apenas os bits dos códigos gerados?
### Codificação de Huffman
Esse algoritmo resolve o problema do prefixo. Ele é um método estatístico que faz análise da frequência relativa dos símbolos. Ele usa árvores binárias não balanceadas, nas quais os símbolos estão nas folhas (essa árvore também é chamada de árvore de huffman)
#### Como fazer o algoritmo?
Para construir uma árvore de Huffman é necessário obter a frequência dos símbolos:
- Os símbolos com maior frequência devem ter os menores códigos
- Monta-se uma lista ordenada pela frequência
# Áudio
## O que é o som?
O som é um fenômeno físico e é uma onda mecânica.
## Características físicas do som
### Amplitude
A amplitude é a intensidade. Ela está relacionada ao volume do som. Quanto maior a amplitude, mais alto ouvimos o som. A amplitude é medida em decibeis (dB).
(colocar tabela)
### Frequência
A frequência determina a altura do som (ou seja, altura é diferente de volume). Frequências altas tem uma altura maior e geram sons agudos. Já frequências baixas tem altura menor e geram sons graves.
(colocar tabela)
## Digitalização de áudio
### Princípios de Digitalização
A princípio temos duas transformações:
- Eletrônica: conversão de ondas mecânicas em sinais elétricos
- Digital: conversão de sinais elétricos em bits
A transformação eletrônica trabalha com um sinal de áudio que é analógico.

(ver dos slides)
- 8000 Hz -> fala, telefonia
- 44100 Hz -> para música

- 4 bits -> telefonia mas voz estranha
- 8 bits -> telefonia usada hoje
- 16 bits -> tele conferência