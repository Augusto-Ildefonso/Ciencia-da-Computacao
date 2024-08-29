# Flip-flops
Em circuitos combinacionais a saída em um dado instantes depende apenas da combinação das entradas neste instantes. Existem projetos que não podem ser resolvidos com circuitos combinacionais. Muitas vezes é necessário conhecer o estado anterior e a sequência anterior para se obter a saída.
Um modo de classificar os circuitos digitais seria subdividi-los em circuitos combinacionais e circuitos sequenciais. Combinacionais são aqueles em que as saídas dependem unicamente das entradas, seguem a lógica combinacional e utiliza a álgebra de Boole como ferramenta.
Nos circuitos sequenciais, as saídas dependem das entradas presentes e também da história das entradas no passado. Saídas dependem da sequência de valores lógicos na entrada que conduzem até o presente. Apresenta memória e realimentação.
Astáveis: circuitos sem estados estáveis, mudam constantemente de estado sem a necessidade de estímulos externos.
Monoestáveis: circuitos com um estado estável, o repouso. Muda de estado com sinal externo, mas volta após algum tempo.
Biestáveis: circuitos com dois estados estáveis: repouso e ativo, somente mudam de estado com sinal externo. Exemplo: flip-flop.
Também chamados de circuitos síncronos. O momento exato em que a saída pode mudar de estado é determinado por um sinal periódico: o clock. Geralmente um trem de pulsos de onda quadrada. Sensível à nível ou à borda (subida ou descida) do clock.
A saída do flip-flop somente se modifica quando uma dada condição do sinal do clock acontece, geralmente, borda de subida ou descida do sinal.
![Imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-29%2014-42-54.png)
A saída copia a entrada D de acordo com o sinal de clock.
![Imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-29%2014-43-22.png)
Comuta a saída quando se aplica um pulso de clock.
![Imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-29%2014-43-34.png)
Geralmente, os flip-flops comerciais possuem entradas assíncronas, como clear (CLR) ou preset (PRE), as quais modificam a saída independente do sinal de clock.
![Imagem](https://raw.githubusercontent.com/Augusto-Ildefonso/Anotacoes-Aulas/master/Imagens/Captura%20de%20tela%20de%202024-08-29%2014-43-43.png)


