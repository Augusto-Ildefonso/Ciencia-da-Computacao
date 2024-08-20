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

# Análise de Algoritmos
## Algoritmo
É um conjunto de instruções que devem ser seguidas para solucionar um determinado problema.
Qualquer procedimento computacional bem definido que toma algum valor ou conjunto de valores de entrada e produz algum valor ou conjunto de valores de saída.
Ferramenta para desenvolver um problema computacional bem especificado.
Assim como o hardware de um computador, constitui uma tecnologia, pois o desempenho total do sistema depende da escolha de um algoritmo eficiente tanto quanto da escolha de um hardware rápido.
Deseja-se que um algoritmo termine e seja correto.
## Recursos de um algoritmo
Uma vez que um algoritmo está pronto/disponível, é importante determinar os recursos necessários para sua execução:
- Tempo
- Memória
## Análise de algoritmos
Um algoritmo que soluciona um determinado problema, mas requer o processamento de um ano, não deve ser usado. Antes de escolher trocar um algoritmo por outro, só porque ele roda mais rápido em determinada máquina, temos que considerar alguns fatores:
- Características da máquina em que o algoritmo foi testado (quantidade de memória)
- Linguagem de programação
	- Compilada x Interpretada
 	- Alto x Baixo Nível
- Implementação pouco cuidadosa do algoritmo x contra a "super" implementação do algoritmo y.
- Quantidade de dados processados

A comunidade de computação começou a pesquisar formas de comparar algoritmos de forma independente de:
- Hardware
- Linguagem de programação
- Habilidade do programador
Portanto, deseja-se comparar algoritmos e não programas (essa área é conhecida como "análise/complexidade de algoritmos").
## Eficiência de algoritmos
Estimamos a eficiência de um algoritmo em função do tamanho do problema. Em geral, assume-se que "n" é o tamanho do problema, ou número de elementos que serão processados. E calcula-se o número de operações que serão realizadas sobre os n elementos.
O melhor algoritmo é aquele que requer menos operações sobre a entrada, pois é o mais rápido e, diferente do tempo de execução que varia de máquina para máquina, o número de operações não, então é uma boa medida de desempenho de um algoritmo. As operações que falamos são as usadas para resolver o problema. O tempo de cada operação é constante, o que muda é a quantidade de vezes.
