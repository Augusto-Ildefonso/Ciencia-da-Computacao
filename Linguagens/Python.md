# Sintaxe básica
## Print
~~~python
# Print
print(var, "string")
~~~
## Python Identifiers
Um Python Identifier é um nome usado para identificar uma variável, função, classe, módulo ou outro objeto. Um Identifier como com a letra ``A`` até ``Z`` ou ``a`` até ``z`` ou um ``_``
seguido por nenhuma ou mais letras, ``_`` ou dígitos de `0` até `9`. O Python é case sensitive, ou seja, há diferença entre letras maiúsculas e minúsculas.

O Python tem algumas convenções para seus Identifiers:
- O nome de classes no Python começa com uma letra maiúscula, já todos os outros identifiers começam com letra minúscula.
- Começar o identifier com um único `_` indica que o identifier é um identifier privado.
- Começar o identifier com dois `_` indica que ele é uma identifier fortemente privado
- Se o identifier começar e terminar com dois `_`, então o identifier é um nome especial definido da linguagem.
## Palavras Reservadas
Palavras reservadas são palavras que não podem ser usadas como constantes, variáveis ou qualquer outro identifier. Veja a lista abaixo.

| and     | as       | assert   |
| ------- | -------- | -------- |
| break   | class    | continue |
| def     | del      | elif     |
| else    | except   | False    |
| finally | for      | from     |
| global  | if       | import   |
| in      | is       | lambda   |
| None    | nonlocal | not      |
| or      | pass     | raise    |
| return  | True     | try      |
| while   | with     | yield    |
## Indentação
O Python não usa chaves para identificar blocos de código e escopo. No lugar ele usa a indentação, então blocos de mesma indentação estão no mesmo escopo.
## Declaração em múltipla linhas
Usualmente as declarações em Python terminam com uma nova linha, mas se usar o caracter de continuação de linha`\` é possível fazer declarações em múltiplas linhas.
~~~python
total = item_um + \
		item_dois + \
		item_tres
~~~
Para declarações usando `[]`, `{}`, `()` não é preciso usar o `\`.
## Quotation
O Python aceita `'`, `"` e `"""` para declarar strings. As aspas triplas definem strings de múltiplas linhas.
## Comentários
Comentários em Python usam `#` ou `"""`, sendo o último para múltiplas linhas.
## Entrada e Saída
A saída de dados é feita com `print`. Ele pode receber uma string, número, variável, etc.
Já e entrada de dados é feita com `input`, ele pode ter ou não uma string dentro para imprimir na tela. Ele converte para string toda a entrada e aí é necessário converter de string para algum outro tipo.
## Múltiplas declarações na mesma linha
Para fazer múltiplas declarações na mesma linha usa-se `;` para separar as declarações.
# Tipo None
O tipo de dado None em Python representa o tipo sem tipo, ou poderia ser conhecido também como tipo vazio, porém falar que é um tipo sem tipo é mais apropriado

Ex:
```python
numero = None

print(numero)
print(type(numero))
```
Saída:
```
None
<class 'NoneType'>
```
O tipo None é sempre especificado com a primeira letra maiúscula, ou seja, o certo é None e não none.

Utilizamos o tipo None quando queremos criar uma variável e inicializa—la com um tipo sem tipo, antes de recebermos um valor final.

O tipo None sempre será considerado falso em Python.
# List Comprehension
Utilizando list comprehension podemos gerar novas listas com dados processados a partir de outro iterável.
Sintaxe:
```
[dado for dado in iterável]
```
Exemplos:
```
numeros [1, 2, 3, 4, 5]

res = [numero * 10 for numero in numeros]
```
```
>> [10, 20, 30, 40, 50]
```
Pode-se usar a list comprehension com condicionais, exemplo:
```
pares = [numero for numero in numeros if not numero % 2 ]
```
# Listas Aninhadas
As listas no python fazem o papel dos arrays em outras linguagens. Já as listas aninhadas fazem o papel de arrays multidimensionais. 
Exemplo de listas aninhadas:
```
listas = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
```
Para acessar os elementos indexamos, por exemplo: `lista[0][1]`.
Iterando em listas aninhadas:
```
for lista in listas:
	for elemento in lista:
		print(elemento)
```
Com list comprehension:
```
[[print(valor) for valor in lista] for lista in listas]
```

# Dictionary Comprehension
```
{chave: valor for valor in iterável}
```
Exemplo:
```
numeros = {'a': ', 'b': 2, 'c': 3, 'd': 4, 'e': 5}

quadrado = {chave: valor**2 for chave, valor in numeros.items()}

numero = [1, 2, 3, 4, 5]
res = {num: ('par' if num % 2 == 0 else 'impar') for num in numero}
```
# Set Comprehension
```
numeros{num for num in range(1, 7)}
```
O mesmo vale para a tupla.
# Expressão Lambda
São funções sem nome, ou seja, funções anônimas.
Exemplo:
```
lambda x: 3 * x + 1
```
Para utilizar a expressão:
```
calc = lambda x: 3 * x + 1
print(calc(4))
```
Lambdas com múltiplas entradas:
```
nome_completo = lambda nomes, sobrenome: nome.strip().title() + ' ' + sobrenome.strip().title()
```
# Map
Faz o mapeamento de valores para uma função. Primeiro argumento é a função e o segundo é o iterável. Retorna um Map Object. 
```
def area(r):
	return 3.14 * (r ** 2)
	
raios = [2, 5, 7.1, 0.3, 10, 44]

areas = map(area, raios)
```
Após utilizar a função map, o resultado dele zerá após o primeiro uso do resultado.
# Data Science
A principal biblioteca usada será o `Pandas`. Para instalá-lo é preciso rodar:
```
$ pip install pandas
```
A parte mais importante da biblioteca são os dataframes. Eles armazenam dados parecidos com tabelas. O pandas tem métodos poderosos para muitos procedimentos feitos com esse tipo de dado.
Para ler um csv como dataframe é necessário usar a função:
~~~python
df = pd.read_csv(caminho_do_csv)
~~~
O método `describe` imprime diversas informações estatísticas acerca do dataframe. O `count` informa quantas linhas tem valores não vazios. O `mean` é a média. O `std` é o desvio padrão que mede a dispersão dos valores. O `min`, é o menor valor da coluna. O `max` é o maior valor da coluna. Os `25%`, `50%` e `75%` mostram a porcentagem dos dados menores ou iguais o valor que aparece na frente.