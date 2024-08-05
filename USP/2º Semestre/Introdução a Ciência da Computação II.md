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
# Recursão
Recursividade consiste na ideia de dividir o problema consecutivamente em pedaços menores até se tornar algo trivial.
Para ter um algoritmo recursivo, ele deve cumprir três regras:
- Deve ter um caso básico
- Deve se aproximar do caso básico a cada estado
- Deve chamar a si mesmo recursivamente
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
