# Revisão de C
## Algoritmo
Procedimento computacional bem definido que recebe valores de entrada e produz valores de saída. Ele é uma sequência de passos computacionais que transformam em uma entrada e uma saída.
Exemplo de programa em C:
```
#include <stdio.h>
#include <stdlib.h>

float potencia(float base, int exp);

float potencia(float base, int exp){
	float res = 1;
	int i;

	for(i = 0; i < exp; i++){
		res *= base;
	}

	return res;
}

int main(void){
	float x;
	int exp;

	scanf("%f %d", &x, &exp);

	printf("%f\n", potencia(x, exp));

	return EXIT_SUCCESS;
}
```
## Ponteiros
Padrões de armazenamento de inteiros:
- Little Endian: 4º 3º 2º 1º (bytes menos significativos primeiros)
- Big Endian: 1º 2º 3º 4º (bytes mais significativos primeiro)
Intel é little endian e Sun Microsystens é big endian.
Diferentes arquiteturas:
- 32 bits -> o ponteiro vai ter 4 bytes
- 64 bits -> o ponteiro vai ter 8 bytes
## Funções Novas
- memcpy - copia os valores do número de bytes da origem para o destino
# Recursão
Recursividade consiste na ideia de dividir o problema consecutivamente em pedaços menores até se tornar algo trivial.
Para ter um algoritmo recursivo, ele deve cumprir três regras:
- Deve ter um caso básico
- Deve se aproximar do caso básico a cada estado
- Deve chamar a si mesmo recursivamente
Uma função é recursiva quando é definida em seus próprios termos, direta ou indiretamente.
A função recursiva ocupará mais espaço na memória (stack) do que a iterativa. Caso dê para criar uma iterativa é melhor. Mas tem certos problemas que a função iterativa dará muito mais trabalho do que a recursiva e por isso vale a pena usar ela.
Exemplo de código recursivo:
```
#include <stdio.h>

int fat(int x){
	if(x == 1){
		return(1);
	} else{
		return(x * fat(x-1));
	}
}

int main(void){
	int x;

	scanf("%d", &x);

	printf("%d! = %d\n", x, fat(x));

	return(0);
}
```
## Efeitos da recursão
### A cada chamada
- Empilham-se na memória os dados locais (variáveis e parâmetros) e o endereço de retorno. A função corrente só termina quando a função chamada terminar
- Executa-se a nova chamada (que também pode ser recursiva)
- Ao retornar,  desempilham-se os dados da memória, restaurando o estado antes da chamada recursiva
### Mesmo resultado com diferença de haver duplicação de código
Para usar recursão depende do problema, pois nem sempre a recursão será a melhor forma de resolver o problema, já que pode haver uma versão simples e não recursiva da função (que não duplica o código e não consome mais memória).
## Quando usar
Quando o problema pode ser definido recursivamente de forma natural.
### Como usar
1. Definir o problema de forma recursiva, ou seja, em termos dele mesmo
2. Definir a condição de término (ou condição básica)
3. A cada chamada recursiva, deve-se tentar garantir que se está mais próximo de satisfazer a condição de término
## Extra
### time.h
Essa biblioteca possui funções que permitem calcular o tempo de execução.
```
clock_t inicio, fim;

inicio = clock();

fim = clock();

printf("%f", (double) ((fim - inicio) / CLOCKS_PER_SEC));
```
## Recursão de Cauda
É quando tem uma chamada recursiva no final do código. Eles são mais facilmente transformáveis em programas iterativos. A recursão pode virar uma condição
Uma rotina apresenta recursão de cauda se a chamada recursiva está no final do seu código, tendo como única função criar um "looping" que será repetido até que a condição de parada seja satisfeita.
Pode ser eliminada facilmente se empregarmos, em seu lugar, uma estrutura de repetição que esteja condicionada à expressão de teste usada na versão recursiva.