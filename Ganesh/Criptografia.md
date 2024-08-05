É o conjunto de métodos e princípios da codificação da comunicação a fim de tornar uma informação ininteligível para terceiros não autorizados.
# Definições
- plaintext -> texto original (texto plano)
- ciphertext -> texto cifrado, criptografado (texto cifrado)
- encriptar -> transforma o plaintext em um ciphertext
- decriptar -> transforma o ciphertext em um plaintext
# Criptografia Clássica
Dois tipos principais de cifras abrangeram a história da criptografia clássica: a cifra de substituição e a cifra de transposição.
## Cifras de substituição
Os símbolos do alfabeto do plaintext são substituídos por um ou mais símbolos do alfabeto do ciphertext, de acordo com uma regra, gerando o texto cifrado.
### Atbash
Trata-se de uma substituição monoalfabética de deslocamento 0 com o alfabeto do texto cifrado na ordem inversa do alfabeto do texto plano. Exemplo com o alfabeto latino:

A |B |C |D |E |F |G |H |I |J |K |L |M |N |O |P |Q |R |S |T |U |V |W |X |Y |Z
Z |Y |X |W |V |U |T |S |R |Q |P |O |N |M |L |K |J |I |H |G |F |E |D |C |B |A
### Cifra de substituição simples (monoalfabética)
Cada unidade do plaintext é substituída por uma única unidade do ciphertext, de acordo com o mapeamento entre os alfabetos do plaintext e do ciphertext. Por exemplo:

Alfabeto do plaintext: A|B|C|D|E|F|G|H|I|J|K|L|M|N|O|P|Q|R|S|T|U|V|W|X|Y|Z
Alfabeto do ciphertext: D|G|U|A|S|M|Z|E|R|B|C|I|H|V|Y|P|K|X|Q|N|T|F|W|L|O|J
#### Cifra de césar
Ela utiliza de um deslocamento de k posições para gerar o alfabeto do ciphertext a partir do alfabeto do plaintext. Por exemplo, para um deslocamento 2:

A|B|C|D|E|F|G|H|I|J|K|L|M|N|O|P|Q|R|S|T|U|V|W|X|Y|Z
C|D|E|F|G|H|I|J|K|L|M|N|O|P|Q|R|S|T|U|V|W|X|Y|Z|A|B
#### Quebrando a cifra de substituição simples
É possível quebrar a cifra de substituição simples pela análise de frequência das letras do ciphertext, desde que se conheça o idioma utilizado. Isso ocorre pois nas cifras monoalfabéticas, cada letra do plaintext é encriptada para a mesma letra do ciphertext.
### Cifra de Vigenère
Trata-se de uma cifra de substituição poli alfabética em que a palavra chave é responsável por especificar o deslocamento de cada letra do plaintext. Desse modo, é impossível realizar um ataque de frequência, como o descrito acima, já que uma letra do plaintext pode virar diferentes letras no ciphertext, a depender do seu "match" com a palavra chave ao longo do texto.

Quando a palavra chave for menor que o plaintext, ela deve ser repetida até completar o tamanho do plaintext. A encriptação pode ser descrita algebricamente: se as letras A-Z correspondem aos números 0-25, soma-se o valor da letra no plaintext com o valor numérico da sua letra pareada na palavra chave e aplica-se o resto da divisão por 26, encontrando o valor numérico da letra do ciphertext. 
Exemplo de encriptação com a palavra chave LEMON:

Plaintext: A|T|T|A|C|K|A|T|D|A|W|N 
Chave: L|E|M|O|N|L|E|M|O|N|L|E 
Ciphertext: L|X|F|O|P|V|E|F|R|N|H|R

Note que a primeira letra T foi encriptada para X, enquanto a segunda letra T foi encriptada para F, ou seja, a mesma letra no plaintext resultou em diferentes letras no ciphertext. Para decriptar, basta subtrair o valor numérico de cada letra do ciphertext do valor numérico do seu par na chave e caso resulte em um número negativo, basta somar 26.
![Tabela](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fuser-images.githubusercontent.com%2F96321435%2F233817957-ed57a13f-fc6d-4260-b8bf-56f37dc89a77.png&width=768&dpr=1&quality=100&sign=6de27035&sv=1)
#### Quebrando a cifra de vigenère (Teste de Kasiski)
Esse ataque funciona para quando a chave é menor do que o plaintext. Vamos considerar o exemplo acima, sabendo o tamanho da chave (5 letras), sabemos que a cada 5 letras do ciphertext o deslocamento para obter tais letras foi o mesmo. No caso acima, as letras L, V e H foram obtidas todas pelo mesmo deslocamento. Agora, se temos um conjunto de letras e todas foram obtidas a partir de um mesmo deslocamento, temos uma cifra de substituição simples, logo, pode-se aplicar a análise de frequência. Ao se obter a letra do plaintext e do ciphertext, é possível saber qual letra da chave que gerou esse deslocamento. 

Assim, descobrimos a primeira letra da chave. Para descobrir a próxima letra, basta repetir o processo para formar um novo conjunto (formado pelas letras X, E, R...) e supor que a letra mais abundante desse conjunto foi obtida a partir da encriptação da letra E. Note que isso tudo só é possível quando soubermos o tamanho exato da chave. Na prática, para descobrirmos o tamanho da chave é preciso encontrar padrões de repetições ao longo do ciphertext e a partir do distanciamento dessas repetições obter o tamanho da chave.

Observe a imagem com o ciphertext a seguir e repare na repetição da sequência U-S-E diversas vezes ao longo do texto.
![Exemplo](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fuser-images.githubusercontent.com%2F96321435%2F233818154-8d59781e-4eb8-4bf2-a03c-0992a9ca341c.png&width=768&dpr=1&quality=100&sign=1b6f7ab8&sv=1)
Como o distanciamento dessas repetições é sempre um número múltiplo de 8, um bom palpite para o tamanho da chave seria 8 caracteres. Mas também é possível que o tamanho da chave seja de 4 caracteres. De qualquer forma, com o tamanho da chave em mãos, basta aplicar o Teste de Kasiski para descobrir a chave utilizada e assim quebrar a cifra.
### Cifra Autokey
Essa cifra foi criada para garantir que o tamanho da chave seja sempre maior do que o plaintext. Para isso, é feito uma concatenação entre a keyword pequena e o plaintext, que resulta na chave.

Para decriptar a mensagem, o receptor deve utilizar a keyword estabelecida, para obter as primeiras letras (quantidade igual a quantidade de letras da keyword) do plaintext e depois deve usar esses letras do plaintext, concatenadas a keyword, para obter o plaintext até o final.

Essa cifra é mais segura que as cifras poli alfabéticas que usam chaves fixas, já que na autokey a chave não é repetida dentro de uma mesma mensagem, logo o método de ataque de kasiski, não se aplica nessa cifra.

Uma grande vulnerabilidade dessa cifra é que o plaintext faz parte da chave. Isso significa que a chave vai certamente conter palavras comuns em diversas posições. A chave pode ser atacada usando palavras comuns através de tentativas de decriptar a mensagem, movendo a palavra pela chave até que textos legíveis apareçam. 
### Polybus Square
Tem como objetivo dividir os símbolos do texto plano de modo que pudessem ser representados por um conjunto menor de símbolos.

![Polybus Square](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fuser-images.githubusercontent.com%2F96321435%2F233818325-75983ec1-e73e-4701-8682-575725e295c9.jpg&width=768&dpr=1&quality=100&sign=d3e62d35&sv=1)

Plaintext: G |A |N |E |S |H
Ciphertext: 22|11|33|15|43|23
### Cifra Homófona
Trata-se de uma cifra que os símbolos mais frequentes do plaintext são correspondidos para mais de um símbolo no ciphertext. Ela foi criada para dificultar a análise estatística de frequência.
![Cifra Homófona](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fuser-images.githubusercontent.com%2F96321435%2F233818401-80f2d053-f320-4423-99a4-1e35dd93224e.png&width=768&dpr=1&quality=100&sign=36782193&sv=1)
Plaintext: **A**br**a**c**a**d**a**br**a** 
Ciphertext: **8**Fb**z**H**K**G**7**FR**i**
### Cifra Poligráfica
Trata-se de uma cifra em que a substituição se dá mapeando um caractere para um grupo de símbolos, por exemplo:

Alfabeto do plaintext: A|B|C|D...
Alfabeto do ciphertext: &A|789|CVD|ZDFG...
### Enigma
Link: https://gitbook.ganeshicmc.com/criptografia/classica#enigma
## Cifras de Transposição
### Transposição Colunar
Para encriptar por meio da cifra de transposição por coluna, deve-se escrever a chave na primeira linha de uma tabela. Em seguida, escreve-se o texto da esquerda para direita e de cima para baixo, e lê-se o texto na vertical, seguindo a ordem alfabética das letras da chave. Exemplo de encriptação com a palavra chave CRIVO:

Plaintext: Somos o Ganesh 
Chave: CRIVO

![Transposição Colunar](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fuser-images.githubusercontent.com%2F96321435%2F233820030-28b3c537-eba1-433a-aff1-2e9776493940.PNG&width=768&dpr=1&quality=100&sign=85fe9106&sv=1)

Ciphertext: S nm ssa ooeoGH

Para decritptar, escrevemos o texto cifrado na tabela na posição vertical seguindo a ordem alfabética das letras da chave, em seguida lemos o texto na horizontal na direção usual.
### Rail Fence
Na cifra Rain Fence, o plaintext é escrito para baixo diagonalmente em "trilhos" sucessivos de uma cerca imaginária, movendo-se para cima quando o trilho inferior é alcançado, e para baixo novamente quando o trilho superior é alcançado e assim por diante até que todo o plaintext seja escrito. O ciphertext é então obtido lendo-se por linhas. A imagem a seguir mostra um exemplo para três trilhos.

![Rail Fence](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fuser-images.githubusercontent.com%2F96321435%2F233820215-35d0da23-83a1-4a4f-a841-6f2f4b91f538.png&width=768&dpr=1&quality=100&sign=e66a7339&sv=1)

Para decriptar, basta construir uma matriz em que o número de colunas é igual ao tamanho do ciphertext e o número de linhas é igual à chave (número de trilhos). Depois basta percorrer a matriz em zigzag, marcando com asterisco as células que receberão letras:

![Rail Fence 2](https://gitbook.ganeshicmc.com/~gitbook/image?url=https%3A%2F%2Fuser-images.githubusercontent.com%2F96321435%2F233820220-c7693f8c-1d67-4eab-b59a-69574cfdb4d2.png&width=768&dpr=1&quality=100&sign=747a560f&sv=1)

Por fim, basta preencher a matriz horizontalmente com as letras do ciphertext e lê-la de acordo com o zigzag.
## Esteganografia
A esteganografia (do grego ‘escrita escondida’) é o uso de de técnicas para ocultar a existência de uma mensagem dentro da outra, uma forma de segurança por obscurantismo. A diferença entre esteganografia e criptografia é que a primeira preocupa-se em ocultar a existência da mensagem, e a segunda o seu significado.
### Método NULL
A simples representação também remete à esteganografia, que é uma técnica para omitir uma mensagem dentro de outra, com o objetivo de fazer com que uma forma escrita seja camuflada em outra a fim de mascarar sua própria existência. Uma técnica simples de esteganografia é o método NULL, no qual a letra do meio de cada palavra da mensagem original compõe a mensagem que se deseja esconder.
# Criptografia Moderna
