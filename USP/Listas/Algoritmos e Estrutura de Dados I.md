# Lista 2 - Pilhas
## Exercício 1
Uma pilha é uma estrutura de dados sequencial, na qual a inserção e remoção de elementos ocorre na mesma extremidade. Disso decorre que o último elemento é o primeiro a sair, conhecido também como LIFO (Last-in/First-out). 
Ela serve para problemas em que precisamos acessar um array de elementos na ordem contrária da qual foram inseridos.
## Exercício 2
```
void maior_pilha(PILHA* p1, PILHA* p2){
	if(p1->tam > p2->tam){
		printf("P1 > P2");
	} else{
		if(p1->tam < p2->tam){
			printf("P1 < P2");
		} else{
			printf("P1 = P2");
		}
	}
}
```
