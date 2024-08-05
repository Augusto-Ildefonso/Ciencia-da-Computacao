# Tipos Abstratos de Dados
Um tipo de dado é um conceito abstrato (quando desprendemos ele do hardware) definido por um conjunto de propriedades lógicas. Assim que um tipo de dado abstrato é definido, assim como as suas operações válidas, podemos implementar esse tipo de dado. 
Ele pode ser implementado por hardware ou por software. No caso do software, existe um programa que consiste de instruções de hardware já existentes que serão usadas para interpretar esse dado. Ou seja, há uma especificação de como o novo tipo de dado pode ser interpretado a partir dos tipos de dados já existentes e também de como as operações definidas para ele ocorrerão.
## Tipo de Dado Abstrato (TDA)
Usando a definição de tipo de dado acima que se define o que é um tipo de dado abstrato. Ele é o conceito matemático básico que define o tipo de dado. Desse modo, como é um conceito matemático, ele não é definido com base na implementação. Um exemplo de TDA é o inteiro.
Um TDA consiste em duas partes: uma definição de valores e uma definição de operadores. A definição de valores determina o conjunto de valores para o TDA e é dividida em duas partes:
- Uma cláusula de definição
- Uma cláusula de condição
Vale mencionar que usamos a notação de colchetes para indicar as partes de um tipo abstrato.
A outra parte é a definição de operadores. Cada operador é definido como uma função abstrata com três partes:
- Cabeçalho
- Pré-condições opcionais
- Pós-condições
Veja agora um exemplo em C de um tipo de dado abstrato chamado RATIONAL:
```
// Definição de valor
abstract typedef <integer, integer> RATIONAL;
condition RATIONAL[1] <> 0;

// Definição de operador
abstract RATIONAL makerational(a, b)
int a, b;
precondition b <> 0;
postcondition makerational[0] == a;
			  makerational[1] == b;

abstract RATIONAL add(a,b) /* written a + b */
RATIONAL a,b;
postcondition add[1] == a[1] * b[1] ;
              add[0] == a[0] * b[1] + b[0] * a [1];
              
abstract RATIONAL mult(a,b) /* written a * b*/
RATIONAL a,b;
postcondition mult[0] == a[0] * b[0] ;
              mult[1] == a[1] * b[1] ;
              
abstract equal(a,b) /* written a == b */
RATIONAL a,b;
postcondition equal == (a[0] * b[1] == b[0] * a[1]) ;
```
As palavras abstract typedef introduzem uma definição de valor e a palavra condition é usada para indicar condições impostas sobre o tipo recém-definido.
Agora para a definição de operadores, o cabeçalho é as duas primeiras linhas de cada operação. A palavra abstract indica que não é uma função de C e sim uma função abstrata. O comentário com a palavra-chave written indica uma nova forma de escrever a função. A pós-condição (postcondition) indica o que a função faz.
A pré-condição (precondition) especifica restrições que devem ser atendidas antes da aplicação da operação.