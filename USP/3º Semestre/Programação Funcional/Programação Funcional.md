# Linguagens
Uma linguagem puramente funcional é o Haskell, porém algumas outras aceitam programar funcional, como Python, Java, Javascript, Ruby, C++, Rust e R. É interessante essas linguagens que permitem programar funcional pois é possível mesclar os paradigmas e fazer parte funcional e parte não funcional.
# História
Alonso Church e Alan Turing pesquisavam o que seria computar. O Church criou um cálculo chamado "lambda cálculo" (o mesmo lambda que usamos em python e é usado em Haskell também) e disse ele concluiu que tudo aquilo que pode ser computável em uma expressão lambda é computável. Já Turing criou a máquina de Turing e com ela ele concluiu que tudo aquilo que pode ser computado, pode ser computado com uma máquina de Turing. Dessas duas proposições surgiu a Tese de Church-Turing
## Tese de Church-Turing
Nessa tese, o lambda cálculo e a máquina de Turing são equivalentes, ou seja, o que é computado em um é computado no outro. O interessante também é que a máquina de Turing permitiu descobrir coisas que não são computáveis.
## von Neumann
A arquitetura de von Neumann tinha semelhança com a máquina de Turing, onde a fita é a memória e a máquina de estados é a CPU. As linguagens, exceto Haskell, se dão bem com a arquitetura de von Neumann, ou seja, com a máquina de Turing. Então, o lambda cálculo ficou de lado, com poucos pesquisadores mas que continuaram trabalhando e desenvolveram o Haskell, por exemplo. Até que as pesquisas de máquina de Turing estagnaram com problemas que não existem no lambda cálculo, então com isso começou uma retomada maior do lambda cálculo e por isso a programação funcional ganhou brilho de novo.

Essa história explica porque muitas linguagens não são funcionais.
# Linguagens Seguras
Uma linguagem dita segura é quando você pode baixar e rodar um pacote sem medo de ter alguma linha de código que faça algo inesperado, como vazar memórias ou executar arquivos por exemplo. O Haskell é uma linguagem extremamente segura, diferente de C que se baixar um arquivo compilado da internet pode ter algum trecho de código que faça algo sem que você veja.
# Por que chama programação funcional?
A palavra-chave para responder a pergunta é função, mas não o que conhecemos como função em outras linguagens, mas sim da ideia de função matemática. Programação Funcional é um paradigma de programação em que definimos programas a partir de funções que se comportem como funções matemáticas. Vale destacar que as funções não podem ter efeitos colaterais, por exemplo, uma função printa algo e retorna o valor.
# Haskell
Haskell é uma linguagem puramente funcional. Então, nela você fala para o computador o que as coisas são ao invés de passar um comando para ele. Além disso você não pode dizer que algo é uma coisa e depois mudar o que ele é.
A linguagem haskell é preguiçosa, isso significa que ela só vai executar as coisas que forem diretamente ditas para serem executadas.
Ademais, Haskell é estaticamente tipado, isso significa que quando você compila o programa, o compilador sabe o tipo de cada parte do código.
Em Haskell tudo é uma função. As operações são funções, as declarações, tudo. Também, toda função ou expressão deve retornar algo. Uma expressão é um trecho de código que retorna algo.
## Operações Aritméticas
~~~haskell
-- Soma
soma = 2 + 5

-- Substracao
subtracao = 5 - 2

-- Multiplicação
multiplicao = 2 * 5

-- Divisão
divisao = 4 / 2
~~~
Podemos usar também os `()` para colocar várias operações na mesma linhas e eles seguem as precedências igual da matemática. Além disso, ele é necessário para usarmos números negativos, então para escrever `-1` em Haskell e o compilador não apontar um erro é preciso escrever `(-1)` e depois o resto das operações.
As operações esperam que na esquerda e direita tenham números.
## Operações Booleanas
~~~haskell
-- AND -> operador &&
and1 = True && False -- Falso
and2 = True && True -- True

-- OR -> operador ||
or1 = True || False -- True
or2 = False || False -- Falso

-- NOT -> operador not
negacao1 = not False -- True
negacao2 = not (True && False) -- False
~~~
## Igualdade e Diferença
~~~haskell
-- Igualdade -> operador ==
igual1 = 5 == 5 -- True
igual2 = 1 == 0 -- False

-- Diferença -> operador /= 
diferenca1 = 5 /= 5 -- False
diferenca2 = 4 /= 2 -- True
~~~
A igualdade e diferença também servem para palavras. Por exemplo `"texto" == "texto"` é verdadeiro.
Eles esperam que na esquerda e direita tenham o mesmo tipo e que eles possam ser comparados.
## Funções
Funções que tem o seu operador entre os valores são chamadas de funções infixas. Já maioria das funções que não são usadas com números, são chamadas de funções prefixas.
Em haskell a maioria das funções são prefixas. Para chamar uma função, precisamos escrever o nome dela seguido de um espaço e então o parâmetro. Por exemplo:
~~~haskell
succ 8
~~~
Essa função pega qualquer coisa que tem um sucessor definido e retorna esse sucessor.
Podemos também chamar funções que tem mais de um parâmetro, veja abaixo como se faz.
~~~haskell
min 9 10
max 9 10
~~~
Essa função pega duas coisas que podem ser ordenadas e `min` retorna o menor entre eles e `max` retorna o maior entre eles.
A aplicação de funções (as chamadas delas) tem a maior precedência de todas em haskell, maior que os parênteses até. Porém se usarmos o parênteses nos seus parâmetros, ela executará primeiro eles, por exemplo: `max (9 * 10)` retorna 91.
Se uma função precisa de dois parâmetros, podemos chamar ela como uma função infixa através do uso das crases, envolvendo o nome da função. Veja abaixo.
~~~haskell
91 `div` 10
~~~
Essa função faz a divisão de inteiros de dois números inteiros.
Para declarar funções, usamos uma estrutura similar da aplicação. A diferença é que no final vem um `=` precedido de um espaço. Veja abaixo:
~~~haskell
doubleMe x = x + x
~~~
As funções não dependem da ordem que foram declaradas.
É possível usar uma função dentro de outra função.
O caractere `'` é um caractere válido para nomear funções. Além disso, funções não podem começar com caractere maiúsculo.
Quando uma função não recebe parâmetros, dizemos que ela é uma definição (ou nome).
## Listas
Em Haskell, as listas são uma estrutura de dados homogênea, ou seja, ela só armazena elementos do mesmo tipo. As listas são denotadas por `[]` e os seus elementos são separados por `,`. Veja abaixo.
~~~haskell
lista = [1, 2, 3, 4, 5]
~~~
As strings, em Haskell, são uma lista de caracteres. Por causa disso, podemos usar funções de listas nas strings.
~~~haskell
string = "hello"
string' = ['h', 'e', 'l', 'l', 'o']
~~~
Para colocar juntar duas listas usamos o operador `++`. Só é necessário tomar cuidado pois para colocar um item no final da lista, o Haskell tem que percorrer toda a lista da esquerda, então quando for uma lista muito grande irá demorar muito. Veja abaixo como usar.
~~~haskell
[1, 2, 3, 4] ++ [5, 6, 7, 8]

"Hello" ++ " " ++ "World"
~~~
Uma forma de contornar isso é colocando no começo da lista o elemento, pois essa operação é instantânea. Para isso usa-se o `:`.
~~~haskell
'A' : "Small cat"

5: [1, 2, 3, 4]
~~~
Se quiser acessar uma lista pelo index usa-se `!!` e o índice começa no 0. Veja abaixo como usar:
~~~haskell
"Steve Buscemi" !! 6

[9.4,33.2,96.2,11.2,23.25] !! 1
~~~
Se tentar acessar um index que não existe, terá um erro.
Listas podem conter listas, que podem conter listas e assim em diante. Listas dentro de listas podem ter tamanhos diferentes mas não podem ser de tipos diferentes. Então não podem ter algumas listas que tem números e outras que tem caracteres dentro da mesma lista.
Podemos comparar listas com `<`, `<=`, `>=` e `>`. Elas são comparadas de forma lexicográfica, ou seja, primeiro comparamos as duas cabeças, se for verdadeiro, comparamos os segundos elementos e assim em diante.
~~~haskell
[3,2,1] > [2,1,0]
~~~
Vamos ver agora algumas funções para manipular listas.
### Head
Pega uma lista e retorna a cabeça dela.
~~~haskell
head [5, 4, 3, 2, 1]
~~~
### Tail
Pega uma lista e retorna a cauda dela, ou seja, retorna a lista cortando a cabeça.
~~~haskell
tail [5, 4, 3, 2, 1]
~~~
### Last
Pega uma lista e retorna o último elemento.
~~~haskell
last [5, 4, 3, 2, 1]
~~~
### Init
Pega uma lista e retorna tudo menos o último elemento.
~~~haskell
init [5, 4, 3, 2, 1]
~~~
Essas funções acima não podem ser usadas em listas vazias.
### Length
Pega uma lista e retorna o tamanho dela.
~~~haskell
length [5, 4, 3, 2, 1]
~~~
### Null
Pega uma lista e checa se ela é vazia. Se for vazia retorna True se não retorna False.
~~~haskell
null []
~~~
### Reverse
Pega uma lista e retorna ela invertida.
~~~haskell
reverse [5, 4, 3, 2, 1]
~~~
### Take
Pega um número $n$ e uma lista e retorna os $n$ primeiros elementos da lista.
~~~haskell
take 3 [5, 4, 3, 2, 1]
~~~
### Drop
Pega um número $n$ e uma lista e retorna a lista sem os $n$ primeiros elementos.
~~~haskell
drop 3 [5, 4, 3, 2, 1]
~~~
### Maximum e Minimun
O `maximum` pega uma lista de elementos que podem ser ordenados e retorna o maior deles. Já `minimun` retorna o menor deles.
~~~haskell
maximum [5, 4, 3, 2, 1]

minimum [5, 4, 3, ,2 ,1]
~~~
### Sum
Pega uma lista e retorna soma dos seus elementos.
~~~haskell
sum [1, 1, 1]
~~~
### Product
Pega uma lista e retorna o produto dos seus elementos.
~~~haskell
product [1, 2, 3]
~~~
### Elem
Pega uma coisa e uma lista e retorna True se aquela coisa está na lista e False se não está. Geralmente é chamada de forma infixa.
~~~haskell
elem 4 [1, 2, 3, 4, 5]
-- ou
4 `elem` [1, 2, 3, 4, 5]
~~~
## Ranges
Ranges é um jeito de criar listas que são sequências aritméticas de elementos que podem ser enumerados. Números e caracteres podem ser enumerados. Veja abaixo.
~~~haskell
[1..20]

['a'..'z']
~~~
Podemos definir um passo para o range, usando um segundo elemento. Veja abaixo.
~~~haskell
[3, 6..20] -- Vai imprimir de 3 em 3 até 20, no caso ele para em 18
~~~
Para fazer um passo negativo temos que fazer:
~~~haskell
[20, 19..1]
~~~
É preciso ter cuidado quando usar floats pois eles podem gerar comportamentos inesperados, devido a imprecisão da sua definição. Geralmente é melhor evitar.
Podemos criar listas infinitas se não especificarmos o limite superior dela. Veja abaixo.
~~~haskell
[13, 16..]
~~~
Isso, aliado ao fato de haskell ser uma linguagem preguiçosa, permite criar, por exemplo, uma lista dos 24 primeiros múltiplos de 13:
~~~haskell
take 24 [13, 26..]
~~~
Vejamos agora algumas funções que criam listas infinitas.
### Cycle
Pega uma lista e cria um ciclo a partir dela fazendo uma lista infinita.
~~~haskell
cycle [1, 2, 3]
~~~
### Repeat
Pega um elemento e cria uma lista infinita somente desse elemento.
~~~haskell
repeat 5
~~~
Mas um jeito mais fácil de ter uma lista de $n$ elementos do mesmo número é só usar a função `replicate n número_que_será_repetido`.
## List Comprehension
List Comprehension é uma forma de criar listas específicas a partir de listas mais gerais. Ele se assemelha ao set comprehension que temos na matemática (exemplo: $S = \{2 . x|x \in \mathbb{N}, x \leq 10\}$). Por exemplo, se quisermos criar em haskell uma lista que representa o set comprehension acima, fazemos:
~~~haskell
[x * 2 | x <- [1..10]]
~~~
Podemos adicionar uma condição (também chamado de predicate) também no list comprehension:
~~~haskell
[x * 2 | x <- [1..10], x * 2 >= 12]
~~~
O uso de predicate para criar as listas pode ser chamado de ``filtering``, ou seja, usando o predicate nós pegamos uma lista de números e filtramos ela pelo predicate.
Podemos incluir vários predicates colocando mais vírgulas.
Além disso, podemos ter várias listas de entradas e a saída é uma junção de todos os resultados que satisfazem o predicate e a função de saída. Veja abaixo.
~~~haskell
[x * y | x <- [1..10], y <- [11..20], x * 2 >= 12]
~~~
Podemos usar list comprehension para strings também.
~~~haskell
nouns = ["hobo","frog","pope"]
adjectives = ["lazy","grouchy","scheming"]
[adjective ++ " " ++ noun | adjective <- adjectives, noun <- nouns]
~~~
Como strings são listas, podemos usar list comprehension para processar e produzir strings. Além disso, podemos fazer list comprehension para listas aninhadas também.
## Tuplas
As tuplas são parecidas com as listas, dado que elas podem guardar diferentes valores em um único valor. Tuplas são usadas quando você sabe quantos valores você quer combinar e o tipo dele depende de quantos componentes ele tem e o tipo dos componentes. Ela é denotada por parênteses e separada por vírgula. Uma outra diferença para as listas é que ela pode ser composta de elementos de diferentes tipos.
Uma tupla de dois elementos é o seu próprio tipo, assim como uma de três elementos. Então se criar uma lista que tem uma tupla de dois elementos e uma de três ela vai apontar um erro, pois a lista não pode ter tipos diferentes.
Não existe tupla de um só elemento.
Assim como listas, podemos comparar os elementos de tuplas se eles forem comparáveis. Só que não podemos comparar tuplas de tamanhos diferentes.
Vejamos agora algumas funções úteis para operar em pares.
### fst
Ela recebe um par e retorna o primeiro elemento.
~~~haskell
fst (8, 11)
~~~
### snd
Ela recebe um par e retorna o segundo elemento.
~~~haskell
snd (8, 11)
~~~
Agora vejamos algumas outras funções.
### zip
Ela permite produzir uma lista de pares a partir de duas listas. As duas listas podem ter tipos diferentes e tamanhos diferentes também (ela vai parar quando acabar a menor lista). Como haskell é preguiçoso podemos usar zip em listas finitas e infinitas.
~~~haskell
zip [1,2,3,4,5] [5,5,5,5,5]
zip [1 .. 5] ["one", "two", "three", "four", "five"]
zip [5,3,2,6,2,7,2,5,4,6,6] ["im","a","turtle"]
zip [1..] ["apple", "orange", "cherry", "mango"]
~~~
## Types e Typeclasses
Como já dissemos, Haskell tem um sistema de tipos estático. Logo, o tipo de cada expressão é conhecido no tempo de compilação, o que leva a um código mais seguro. Em Haskell, tudo tem um tipo, então o compilador pode pensar muito sobre o seu programa antes de compilá-lo.
Haskell tem inferência de tipo, então se escrevemos um número em Haskell não precisamos falar que é um número, ele pode inferir que é um número sozinho. Logo, não precisamos escrever os tipos das nossas funções e expressões para compilar.
### Type
Um tipo em Haskell é um tipo de label que toda expressão tem. Ele nos diz a qual categoria de coisas aquela expressão se encaixa.
Quando temos uma expressão e imprimimos o seu tipo (ou então que vamos explicitamente escrever o tipo) temos o seguinte resultado: `expressão :: Tipo`. O `::` é lido como `has type of`. Os tipos tem sempre a primeira letra maiúscula.
Funções também tem tipos. Quando escrevemos as nossas funções, podemos escolher dar a ela uma declaração explícita de tipo. Isso é considerado uma boa prática, exceto se estamos escrevendo funções muito curtas, mas num geral vamos sempre declarar explicitamente. Por exemplo, se vamos fazer uma função de remover as letras não maiúsculas, vamos receber uma string e retornar uma string, então temos:
~~~haskell
removeNaoMaiusculas :: [Char] -> [Char]
removeNaoMaiusculas str = [ c | c <- str, c `elem` ['A'..'Z']]
~~~
Vale notar que o tipo `[Char]` é sinônimo do tipo `String`, então podemos trocar um pelo o outro.
Agora, se tivermos uma função que tem vários parâmetros:
~~~haskell
addThree :: Int -> Int -> Int -> Int
addThree x y z = x + y + z
~~~
Os parâmetros são separados por `->` e não há distinção especial entre parâmetros e retorno. O retorno será o último item na declaração e os parâmetros são os três primeiros.
Veja abaixo alguns tipos comuns:
- `Int`: Inteiro, ele é usado para números inteiros. Ele tem um valor máximo e mínimo. Geralmente em máquinas 32 bits o máximo é 2147483647 e o mínimo é -2147483648.
- `Integer`: Inteiro, ele também é usado para números inteiros. Mas diferente do `Int` ele não tem limite máximo e mínimo, então pode ser usado para representar números muito grandes. Entre tanto o `Int` é mais eficiente.
- `Float`:Float, é um número de ponto flutuante com precisão única.
- `Double`: Double, é um número de ponto flutuante com o dobro de precisão.
- `Bool`: Booleano, é um tipo que tem dois valores: ``True`` ou ``False``.
- `Char`: Caracter, ele representa caracteres. Ele é denotado por aspas simples. Uma lista de caracteres (`[Char]`) é uma `String`.
- As tuplas são tipos dependentes do seu tamanho e do seus componentes, então existe uma infinidade de tipos. Mas vale ressaltar que `()` também é um tipo que só pode ter um valor: 0.
### Type variables
Uma type variable pode ter qualquer tipo, ela é usada quando queremos fazer uma função que pode ser usada para qualquer tipo, deixando, assim, ela mais geral. Funções que tem type variables é chamada de função polimórfica. Veja abaixo como ela é usada:
~~~haskell
head :: [a] -> a
~~~
Então como podemos ver pelo tipo da função ``head``, ela pode receber uma lista de qualquer tipo e retorna um elemento de qualquer tipo.
As type variables podem ter nomes maiores mas geralmente nomeamos elas de: a, b, c, d, ....
Veja para a função `fst`:
~~~haskell
fst :: (a, b) -> a
~~~
Ela recebe uma tupla de dois elementos que podem ou não ter tipos diferentes e retorna um elemento do mesmo tipo do primeiro elemento.
### Typeclasses
Uma Typeclass é um tipo de interface que define determinado comportamento. Se um tipo faz parte de uma Typeclass significa que ele aguenta e implementa o comportamento que a Typeclass descreve.
Quando estamos definindo uma função observamos que temos um símbolo `=>`. Veja abaixo.
~~~haskell
(==) :: (Eq a) => a -> a -> Bool
~~~
Tudo antes do símbolo `=>` é chamado de class constraint. Nós podemos ler essa definição de tipo como: a função igualdade pega quaisquer dois valores que são do mesmo tipo e retorna um booleano, onde o tipo dos dois valores deve ser um membro da classe Eq (isso era a class constraint).
Alguns Typeclasses básicos são:
- `Eq`: é usado para tipos que suportam testes de igualdade. As funções que seus membros implementam são `==` e `/=`. Então, se tem uma class constraint Eq para um type variable em uma função, ela usa `==` ou `/=` em algum lugar da sua definição. Todos os tipos que mencionamos antes, exceto funções, fazem parte de Eq.
- `Ord`: é usado para tipos que podem ser ordenados. Todos os tipos, exceto funções, são parte de Ord. Ele cobre todos os tipos de comparação padrão, como `>, <, <=, >=`. Ordenação é um tipo que pode ser GT, LT ou EQ, ou seja, "greater than", "lesser than" e "equal", respectivamente. Para ser membro de Ord tem que ser membro de Eq.
- `Show`: os membros de Show podem ser representador por strings. Todos os tipos que vimos até agora estão nela, exceto funções.
- `Read`: ela é meio que o oposto do Show. A função dela é o read que pega uma string e retorna um tipo que é membro de Read. Podemos ter um problema de ler um tipo ambíguo, por exemplo se a string for "4", ele não sabe quais dos tipos membros de Read vai ser. Para resolver isso podemos usar type annotations explícitos. O type annotation é uma forma de explicitamente dizer qual o tipo de uma expressão. Para usá-lo adicionamos um `::` no final da expressão e depois especificamos um tipo. Por exemplo: `read "5" :: Int`.
- `Enum`: é usado para tipos que podem ser enumerados, seus membros são tipos ordenados sequencialmente. Os tipos dessa classe podem ser usados em list ranges. Eles também tem sucessores e predecessores definidos, que podemos verificar com as funções `succ` e `pred`. Os tipos dessa classe são: (), Char, Ordering, Int, Integer, Float e Double.
- `Bounded`: seus membros tem um limite superior e inferior. As funções `minBounded` e `maxBounded` pegam o mínimo e o máximo respectivamente. Até mesmo tuplas são membros dessa typeclass.
- `Num`: é uma typeclass numérica. Seus membros tem a propriedade de serem capazes de agir como números. Os tipos dessa classe são: Int, Integer, Float, Double. Para ser membro de Num tem que ser parte de Show e Eq.
- `Integral`: é uma typeclass numérica também. Integral inclui somente números inteiros. Logo seus tipos são: Int e Integer.
- `Floating`: é uma typeclass numérica que inclui somente números de ponto flutuante. Logo seus tipos são: Float e Double.
## Sintaxe em Funções
### Pattern Matching
Pattern Matching consiste de padrões específicos aos quais um dado deveria cumprir e então deveria verificar se ele cumpre de fato e desconstruir o dado de acordo com o padrão.
Quando definimos funções, podemos definir diferentes corpos para diferentes padrões. Veja abaixo.
~~~haskell
lucky :: (Integral a) => a -> String
lucky 7 = "LUCKY NUMBER SEVEN!"
lucky x = "Sorry, you're out of luck, pal!"
~~~
Quando chamamos lucky, os padrões vão ser checados de cima para baixo e quando ele se adequar a um padrão, o corpo da função correspondente será usado. Um padrão genérico como o último não pode vir em primeiro porque se não todos vão entrar nele, até mesmo o 7.
Quando fazemos padrões, temos que sempre incluir um padrão genérico para que nosso programa não quebre se tiver uma entrada inesperada. Ou então, devemos fazer padrões exaustivos para que cubra todas as possibilidades de padrão. Se não cobrirmos teremos um erro de que temos padrões não exaustivo.
Há também uma coisa chamada pattern. Ele é uma forma fácil de quebrar algo de acordo com um padrão e juntar isso a um nome, enquanto ainda mantemos referência ao todo. Para fazer isso colocamos um nome, seguido de um @ na frente do padrão. Veja abaixo.
~~~haskell
capital :: String -> String
capital "" = "Empty string, whoops!"
capital all@(x:xs) = "The first letter of " ++ all ++ " is " ++ [x]
~~~
Veja que podemos nos referir ao ``(x:xs)`` usando o nome `all`, poupando o trabalho de ter que digitar o padrão todas as vezes.
### Guardas
Guardas são uma forma de testar se uma propriedade de um valor (ou vários deles) são verdadeiras ou falsas. Ele é similar à um `if`. A diferença é que ela é mais legível quando temos várias condições e se dão bem com patterns.
Veja o exemplo abaixo .
~~~haskell
bmiTell :: (RealFloat a) => a -> String
bmiTell bmi
    | bmi <= 18.5 = "You're underweight, you emo, you!"
    | bmi <= 25.0 = "You're supposedly normal. Pffft, I bet you're ugly!"
    | bmi <= 30.0 = "You're fat! Lose some weight, fatty!"
    | otherwise   = "You're a whale, congratulations!"
~~~
Se `bmi <= 18.5` então ele imprime a primeira frase, se `bmi <= 25` a segunda e assim em diante. Caso não seja nenhuma das condições explícitas, usamos o ``otherwise`` como um else que irá imprimir a frase dele para qualquer valor que não se enquadre em uma das guardas acima. As guardas são indicadas por `|`.
### Where
O `where` permite juntar uma expressão à um nome e usar esse nome no código ao invés de ficar repetindo a expressão. Veja abaixo.
~~~haskell
bmiTell :: (RealFloat a) => a -> a -> String
bmiTell weight height
    | bmi <= skinny = "You're underweight, you emo, you!"
    | bmi <= normal = "You're supposedly normal. Pffft, I bet you're ugly!"
    | bmi <= fat    = "You're fat! Lose some weight, fatty!"
    | otherwise     = "You're a whale, congratulations!"
    where bmi = weight / height ^ 2
          skinny = 18.5
          normal = 25.0
          fat = 30.0
~~~
Geralmente colocamos o `where` após as guardas e indentamos ele o mesmo que elas ou um a mais, e então definimos vários nomes ou funções. Os nomes definidos `where` servem somente para essa função. Temos que alinhar os nomes igual acima em uma coluna. Podemos definir funções em `where`. Podemos aninhar `where`.
### Let
O `let` permite juntar uma expressão à uma variável e ela se torna uma expressão. Mas ela é extremamente local, então ela serve somente para a guarda que foi definida e não para todas as guardas.
~~~haskell
cylinder :: (RealFloat a) => a -> a -> a
cylinder r h =
    let sideArea = 2 * pi * r * h
        topArea = pi * r ^2
    in  sideArea + 2 * topArea
~~~
O formato é `let <bindings> in expression`. Os nomes que definimos na parte do `let` são acessíveis somente para a parte do `in`.
A diferença do `let` para o `where` é que os bindings do `let` são de fato expressões, enquanto os do `where` são construtores sintáticos.
Podemos usar ele para definir funções em um escopo local:
~~~haskell
[let square x = x * x in (square 5, square 3, square 2)]
~~~
Se quisermos fazer vários bindings mas no formato acima usamos um `;` para separar. Veja abaixo.
~~~haskell
(let a = 100; b = 200; c = 300 in a*b*c, let foo="Hey "; bar = "there!" in foo ++ bar)
~~~
Não é necessário colocar um `;` depois do último binding mas pode colocar. 
Podemos também usar o let dentro de list comprehensions.
~~~haskell
xs = [bmi | (w, h) <- xs, let bmi = w / h ^ 2, bmi >= 25.0]
~~~
Nós escondemos a parte do `in` em list comprehensions, porque a visibilidade dos nomes já está visível ali.
### Case
As expressões case em haskell além de ter a funcionalidade igual das linguagens imperativas, elas também pode ser usadas em pattern matching. O formato dela é:
~~~haskell
case expression of pattern -> result
                   pattern -> result
                   pattern -> result
                   ...
~~~
Veja um exemplo:
~~~haskell
head' :: [a] -> a
head' [] = error "No head for empty lists!"
head' (x:_) = x

head' :: [a] -> a
head' xs = case xs of [] -> error "No head for empty lists!"
                      (x:_) -> x
~~~
O primeiro pattern matching que achar vai ser executado, se ele rodar tudo e não achar nenhum matching, então vai dar um runtime error.
## Funções de Alta Ordem
Funções de alta ordem são funções que recebem funções como parâmetros e retorna funções como os valores de retorno.
### Curry
Haskell Curry foi um matemático que criou o conceito de curry. Esse conceito que permite ter compiladores eficientes para linguagens funcionais. A ideia de curry é que toda função recebe só um valor e retorna só um valor. Em todas as funções do haskell tem curry, até mesmo quando parece que não tem.
Veja na função abaixo como definimos ela:
~~~haskell
max :: (Ord a) => a -> a -> a
max 4 5
~~~
A gente lê ela como: max pega a e retorna (`->`) uma função que pega um a e retorna um a.
## Anotações da Aula
### Introdução
~~~haskell
main = do -- Monad
  putStrLn "Hello World!" -- Essa função putStrLn imprime uma linha de string na tela
  putStrLn "Oi"
  putStrLn $ show z -- O show transforma o z em string e o dólar separa as funções e faz primeiro o que está na frente (show) e depois o que está antes (putStrLn)
  putStrLn $ show c
  putStrLn $ show $ f True -- Temos que processar o f com True e aí fazer o show e depois o print
  putStrLn $ show $ f $ y > 2
  putStrLn $ show $ g x
  putStrLn $ show $ h 9.4
  putStrLn $ show $ k o3
  putStrLn $ show $ s o3
  putStrLn $ show $ head o3 -- Ele vai pegar a cabeça da lista (primeiro elemento)
  putStrLn $ show $ tail o3 -- Ele vai pegar a cauda da lista (último elemento)

x = x + 1
z = y + 1
y = 6

a = True
b = False
c = 5 > y

-- Definindo uma função
f True = 5 -- Quem está sendo definido é a primera palavra, então estamos definindo que f aplicada à True é 5
f False = 0
g t = 57 -- Criamos uma função que independente do valor que é passado para ele, ele retorna 57
h x = 57 + x -- O x dessa função não é referente ao x anterior e sim ao parâmetro x apresentado na mesma linha

m x True = x - 1
m x False = x + 1

m1 x b = if b
			then x - 1
			else x + 1
-- O m e o m1 são iguais, mas em haskell usamos poucos ifs, geralmente se quisermos fazer uma estrutura tipo a do if usamos igual foi escrito no m, criando os casos

j 0 = 1
j x = x * j (x - 1)

-- Fazendo listas em haskell
o1 = []
o2 = [5]
o3 = [6, 42, y, j 5, m 8 True]
-- o4 = [9, "oi", 3, True] -- Essa lista está errada pois os elementos tem que ter o mesmo tipo
o5 = [True, False, False, True, x > 6]
o6 = 7:o2 -- O : pega um elemento e uma lista e retorna uma lista com o elemento que ele pegou na primeira posição da lista
o7 = x:o3

k [] = 0
k (x:xs) = 1 + k xs -- Retorna o tamanho da lista --(x:xs) é uma lista formada por uma cabeça (x) e uma cauda (xs)

s [] = 0
s (x:xs) = x + s xs -- Fazendo a soma dos elementos da lista


~~~
Em Haskell, a **Monad** é um conceito abstrato que encapsula computações sequenciais, permitindo encadear operações de forma elegante. O termo `--Monad` no seu código parece ser apenas um **comentário**, sem efeito no código em si.

No entanto, como seu código usa `do`, isso indica o uso de uma **Monad**, que, nesse caso, é a `IO`. A `IO Monad` é necessária para operações de entrada e saída (I/O), como `putStrLn`, pois essas operações interagem com o "mundo externo", algo que Haskell, sendo funcional puro, não lida diretamente.

O bloco `do` permite sequenciar múltiplas operações `IO`, tornando o código mais legível. Sem `do`, seria necessário encadear chamadas com `>>` e `>>=` (operadores de composição monádica).

Podemos usar parênteses no lugar do $ mas o mais comum em haskell é o $ pois o estilo de programação em haskell é dessa forma.

O Haskell só calcula aquilo que realmente precisa, por exemplo na linha `putStrLn $ show $ g x`, o``x`` não é usado na função ``g`` então ele não é calculado e por isso não dá erro no código. Além disso, essa função é polimórfica, pois ela não depende do tipo de `t`
### Guardas em Haskell
Usamos a estrutura de guardas para poder escrever funções definidas por partes. Enquanto em outras linguagens usamos if then e else. Veja a seguir.
~~~haskell
sinal x
	| x < 0 = -1
	| x == 0 = 0
	| otherwise = 1

--Soma dos positivos de uma lista
somaPos [] = 0 -- A soma positiva de uma lista vazia é 0
somaPos (x:xs)
  | x > 0 = x + somaPos xs
  | otherwise = somaPos xs

baskara a b c
   | delta < 0 = []
   | delta == 0 = [x]
   | otherwise = [x', x'']
     where 
       delta = b ^ 2 - 4 * a * c
       x = (-b) / (2 * a)
       x' = (-b + sqrt delta) / (2 * a)
       x'' = (-b - sqrt delta) / (2 * a)
~~~
O `otherwise` é true, tanto que poderia substituir ele por ``True``. É importante ter ele porque na função acima mesmo, sem ``otherwise`` teriam valores de x para os quais a função não funcionaria
### Entrada e Saída de Dados
~~~haskell
	main = do
	  la <- getLine -- Leio a linha a como string
	  let a = read la -- Converto de string para número
	  lb <- getLine -- Leio a linha b como string
	  let b = read lb -- Converto de string para número
	  lc <- getLine -- Leio a linha c como string
	  let c = read lc -- Converto de string para número
	  let res = explica $ baskara a b c
	  putStrLn $ res
	    where
		  explica [] = "Nao ha raizes"
		  explica [x] = "Ha uma raiz: " ++ show x
		  explica [x1, x2] = "Ha duas raizes: " ++ show x1 ++ ", " ++ show x2
	  
	baskara a b c
	   | delta < 0 = []
	   | delta == 0 = [x]
	   | otherwise = [x', x'']
	     where
	       delta = b ^ 2 - 4 * a * c
	       x = (-b) / (2 * a)
	       x' = (-b + sqrt delta) / (2 * a)
	       x'' = (-b - sqrt delta) / (2 * a)
~~~
O `read` é o contrário do show, enquanto ele converte o tipo qualquer para string, o `read` converte a string para qualquer tipo que você precisar automaticamente, ele entende se é número, lista, árvore, etc. Ele sabe para qual tipo converter a string a partir da análise de para que você usa ele, tanto que se lesse uma variável que não é usada no código ele dá erro pois o read não tem como saber para qual tipo converter.
Para funções impuras como a main, a ordem importa, ela é lida em ordem. Já em funções impuras a ordem não importa, ela não é executada em ordem.
A `<-` é usada para atribuições de funções impuras, já o `=` é usado para função pura, em conjunto com o `let`.
### Função de alta ordem
Uma função de alta ordem é uma função que recebe como parâmetro outra função.
~~~haskell
main = do
  putStrLn $ show $ somaTeste ehPositivo a
  putStrLn $ show $ somaTeste ehNegativo a
  putStrLn $ show $ somaTeste ehPar a


ehPositivo x = x > 0
ehNegativo x = x < 0
ehPar x = mod x 2 == 0

somaTeste teste [] = 0

somaTeste teste (x:xs)
  | teste x = x + somaTeste teste xs
  | otherwise = somaTeste teste xs
~~~
Objeto de primeira classe é aquele tipo básico que tem nas linguagens como inteiro, float, string, etc. Os tipos básicos variam de linguagem para linguagem. Em haskell, função é um objeto de primeira classe. Com esse conceito, podemos melhorar o código acima.
~~~haskell
ehPos = \x -> x > 0 -- Isso é uma função lambda
--Então arrumando o código acima
main = do
  putStrLn $ show $ somaTeste (\x -> mod x 2 == 1) vetor -- Função para ímpar

somaTeste teste [] = 0
somaTeste teste (x:xs)
  | teste x = x + somaTeste teste xs
  | otherwise = somaTeste teste xs
~~~
Esse uso de função acima só é possível porque função é um tipo básico. Tanto que é possível ter uma função que recebe duas funções e retorna uma função. Podemos melhorar ainda o código passando o caso de teste como função lambda, a função que define a operação como função lambda, o valor e o resultado. Além disso, podemos passar as funções igual abaixo:
~~~haskell
main = do
  putStrLn $ show $ somaTeste (>0) (*) 1 vetor
  putStrLn $ show $ somaTeste (\x -> True) (*) 1 vetor

operaTeste teste op neutro [] = neutro
operaTeste teste op neutro (x:xs)
  | teste x = op x $ operaTeste teste op neutro xs
  | otherwise = operaTeste teste op neutro xs
~~~
Quando uma função recebe um parâmetro que não é usado, pode-se usar o `_` no lugar do nome do parâmetro para indicar que ele não é usado.
#### Curry
Haskell Curry foi um matemático que criou o conceito de curry. Esse conceito que permite ter compiladores eficientes para linguagens funcionais. A ideia de curry é que toda função recebe só um valor e retorna só um valor. Em todas as funções do haskell tem curry, até mesmo quando parece que não tem.
~~~haskell
multiplica x y = x * y -- Aqui da impressão que tem dois parâmetros, mas veja abaixo como o compilador enxerga
multiplica x = \y -> x * y -- Poderiamos ainda exagerar a representação igual abaixo
multiplica = \x -> (\y -> x * y)
~~~
E assim vai seguindo, com uma função sendo um parâmetro de uma função até que todas tenham só um parâmetro e retorna só um valor.
### Tipos
Vejamos os tipos que existem em haskell e como são definidas. Podemos também definir os tipos e assim toda vez que o compilador ver a variável ele vai ver como do tipo que foi definido.
#### Integer
Não tem limite.
~~~haskell
k :: Integer
k = 5
~~~
#### Inteiro
Ele é limitado, igual o int de C.
~~~haskell
k :: Int
m = 5
~~~
#### Vetor
~~~haskell
a :: [Integer] -- Uma lista de Integer
a = [1, 2, 3, 4, 5]
~~~
#### Função
~~~haskell
ehPositivo :: Integer -> Bool
ehPositivo x = x > 0
~~~
#### Tipo genérico
Esse tipo é um tipo genérico, que vai depender do que for colocado neles.
~~~haskell
ehPositivo :: [a] -> Bool -> [a] -> [a]
~~~
### TypeClass
As classes englobam diversos tipos que tem algum tipo de característica em comum
#### Class Eq
Essa classe agrupa todos os tipos que podem ser feitos a operação de igualdade.
~~~haskell
(Eq a) => ...
~~~
#### Class Num
Essa classe agrupa todos os tipos que podem ser somados.
~~~haskell
(Num a) => ...
~~~
#### Class Ord
Essa classe agrupa os tipos que podem ser feitos as operações de maior e menor.
~~~haskell
(Ord a) => ...
~~~

### Identificadores
Temos os identificadores como temos no C, então que começam com letras e é seguido de números, letras, etc. Porém, além deles, também temos identificadores que podem ser formado de caracteres especiais. A diferença entre os dois é que quando começa com letra ele é prefix, já quando é com caracteres especiais é infix. Veja abaixo.
~~~haskell
main = do
  putStrLn $ show $ 5 +-=-@ 7

f a b = a ^ 2 + b * 2 // Aqui o f é o identificador e ele fica no início, por isso é prefix

a +-=-@ b = a ^ 2 + b * 2 // Aqui o +-=-@ é o identificador e ele fica no meio, por isso é infix
~~~
Sendo assim, percebemos que as operações, como `^`, `+`, `*`, entre outras, são também funções infix. Logo, há em algum lugar no haskell uma função definida por `+`, por exemplo.
Para transformar de infix para prefix, usa-se os parênteses:
~~~haskell
z = (+) x 5
~~~
Para transformar de prefix para infix, usa-se as crases:
~~~haskell
impar x = x `mod` 2
~~~
### Quick-Sort
~~~haskell
quicksort :: (Ord a) => [a] -> [a]
quicksort [] = []
quicksort (pivot:xs) = menores ++ iguais ++ maiores
  where
    menores = quicksort $ filtra (<pivot) xs
    iguais = pivot:filtra (==pivot)
    maiores = quicksort $ filtra (>pivot) xs

filtra _ [] = []
filtra teste (x:xs)
  | teste x = x:r
  | otherwise = r
  where
    r = filter teste xs
~~~
### Crivo
É uma lista de todos os valores que não são múltiplos da cabeça. Veja abaixo um crivo para números primos.
~~~haskell
main = do
  putStrLn "HW"
  putStrLn $ show $ pega 10 $ primos
  putStrLn $ show $ pegaEqto (<100) $ primos
  putStrLn $ show $ pega 10 $ ignoraEqto (<1000) $ primo
  putStrLn $ show $ soma $ pegaEqto (<200) $ ignoraEqto (<100) primos

primos = crivo [2..] -- Lista infinita
  where
    -- crivo (x:xs) = x : (crivo $ filtro (naoEhMultiplo x) xs)
    -- crivo (x:xs) = x: (crivo $ filtro (\y -> y `mod` x /= 0) xs)
    crivo (x:xs) = x : (crivo $ filtro ((/=0).(`mod` x)) xs) -- o . é uma função que faz composição de função
    -- (.) :: (a->b) -> (c->a) -> (c->b)

naoEhMultiplo :: Integer -> Integer -> Bool
naoEhMultiplo x y = y `mod` x /= 0

filtro :: (a -> Bool) -> [a] -> [a]
filtro _ [] = []
filtro t (x:xs)
  | t x = x:filtro t xs
  | otherwise = filtro t xs

pega :: Integer -> [a] -> [a]
pega _ [] = []
pega 0 _ = []
pega n (x:xs) = x:pega (n-1) xs

-- Ela pega os valores da lista enquanto uma condição é verdadeira
pegaEqto :: (a-> Bool) -> [a] -> [a]
pegaEqto _ [] = []
pegaEqto t (x:xs)
pega Eqto t (x:xs)
  | t x = x:pegaEqto t xs
  | otherwise = []

-- Ele ignora enquanto uma condição é verdadeira
ignoraEqto :: (a -> Bool) -> [a] -> [a]
ignoraEqto _ [] = 0
ingoraEqto t (x:xs)
  | t x = ignoraEqto t xs
  | otherwise = xs --pega a cauda

soma:: (Num a) => [a] -> a
soma [] = 0
soma (x:xs) = x + soma(xs)
~~~
### Função zip
Vamos fazer uma função que zipa duas listas.
~~~haskell
zipa [] _ = 
zipa _ [] = []
zipa (x:xs) (y:ys) = (x, y) : zipa xs ys -- (x, y) é uma tupla que é formada pelas cabeças das listas
~~~
### Mapa
### Função de Primeira Classe
Funções são consideradas tipos e é extremamente fácil realizar a criação de uma nova função.
### Função de alta ordem
Uma função de alta ordem é aquela que aceita uma outra função como parâmetro.
### Função Pura
Uma função pura é definida como dado uma determinada entrada, ela sempre devolve a mesma coisa. Ademais, ela não possui nenhum efeito colateral.
### Transparência referencial
Dado uma definição de uma variável, qualquer uso posterior daquela variável pode ser substituída pela sua primeira definição.
### Estado Imutável
Uma vez declarada uma variável, não é possível mudar o valor dela posteriormente. Por causa disso, não existe contador ou acumulador em haskell. Uma das grandes vantagens disso é a facilidade em paralelização.
### Recursão
A recursão é a única forma de criar contadores, acumuladores, etc.
### Recursão de cauda
É quando chamamos a recursão no final da definição da função. Em haskell, recursão de cauda não estoura a memória.
### Sistema de tipos
Análise de tipos é essencial para programação funcional, ele te da garantia se as chamadas de funções estão certas, se aplicação está certa.
### Preguiça
A execução é não-estrita, ou seja, ele não executa as coisas a menos que precise.
### Criando tipo
~~~haskell
data DiaDaSemana = Dom | Seg | Ter | Qua | Qui | Sex | Sab

horaDeAcordar :: Dia da Semana -> (Integer, Integer)
horaDeAcordar Dom = (9, 30)
horaDeAcordar Sab = (8, 0)
horaDeAcordar _ = (7, 15)
~~~
O `Dom`, ..., `Sab` são construtores, isso permite usarmos eles dentro da função. Mas isso também tem alguns problemas. Por exemplo, se quisermos imprimir com o ``show`` dará um erro pois o show é um typeclass de todas as classes que podemos imprimir, mas o construtor que criamos, não entra automaticamente em nenhum typeclass. Então funções como o ``show``, ou até mesmo um ``elem`` não funcionarão pois eles dependem de alguns tipos e o nosso construtor não foi alocado para nenhum typeclass.
~~~haskell
main = do
  putStrLn $ show $ horaDeAcordar Ter -- Funciona pois a função foi criada então definimos ela pra funcionar com o nosso construtor
  putStrLn $ show $ Dom -- Não funciona pois o Dom não pertence ao typeclass do show
  putStrLn $ show $ elem Ter [Dom, Qua, Ter, Sex, Sab] -- Não funciona pois elem espera elementos que podem ser comparados
  putStrLn $ show $ elem Ter [Seg..Sex] -- Não funciona o ..
~~~
O typeclass dá tipo um "superpoder" para o tipo.
Para conseguirmos arrumar o erro, temos alguns jeitos.
#### Primeiro modo
~~~haskell
data DiaDaSemana = Dom | Seg | Ter | Qua | Qui | Sex | Sab
instance Show DiaDaSemana where
  show Dom = "Sunday"
  show Seg = "Monday"
  show Ter = "Tuesday"
  show Qua = "Wednesday"
  show Qui = "Thursday"
  show Sex = "Friday"
  show Sab = "Saturday"
~~~
O `instance` serve para falar que o `DiaDaSemana` é uma instância (está dentro da classe) da classe show, logo, agora ele funciona com o show. Então o `putStrLn $ show $ Dom` funciona agora.
~~~haskell
data DiaDaSemana = Dom | Seg | Ter | Qua | Qui | Sex | Sab
instance Show DiaDaSemana where
  show Dom = "Sunday"
  show Seg = "Monday"
  show Ter = "Tuesday"
  show Qua = "Wednesday"
  show Qui = "Thursday"
  show Sex = "Friday"
  show Sab = "Saturday"
  
-- elem :: (Eq a) => a -> [a] -> Bool
instance Eq DiaDaSemana where
  Dom == Dom = True
  Dom == _ = False
  Sab == Sab = True
  Sab == _ = False
  Sex == Sex = True
  Sex == _ = False
  Qui == Qui = True
  Qui == _ = False
  Qua == Qua = True
  Qua == _ = False
  Ter == Ter = True
  Ter == _ = False
  Seg == Seg = True
  Seg == _ = False
-- Podemos também fazer só o Dia == Dia e dps _ == _ = False
~~~
Agora o `putStrLn $ show $ elem Ter [Dom, Qua, Ter, Sex, Sab]` funciona.
~~~haskell
data DiaDaSemana = Dom | Seg | Ter | Qua | Qui | Sex | Sab
instance Show DiaDaSemana where
  show Dom = "Sunday"
  show Seg = "Monday"
  show Ter = "Tuesday"
  show Qua = "Wednesday"
  show Qui = "Thursday"
  show Sex = "Friday"
  show Sab = "Saturday"
  
-- elem :: (Eq a) => a -> [a] -> Bool
instance Eq DiaDaSemana where
  Dom == Dom = True
  Dom == _ = False
  Sab == Sab = True
  Sab == _ = False
  Sex == Sex = True
  Sex == _ = False
  Qui == Qui = True
  Qui == _ = False
  Qua == Qua = True
  Qua == _ = False
  Ter == Ter = True
  Ter == _ = False
  Seg == Seg = True
  Seg == _ = False
  
instance Enum DiaDaSemana where
  succ Dom = Seg
  succ Seg = Ter
  succ Ter = Qua
  succ Qua = Qui
  succ Qui = Sex
  succ Sex = Sab
  succ Sab = Dom
  pred Seg = Dom
  pred Ter = Seg
  pred Qua = Ter
  pred Qui = Qua
  pred Sex = Qui
  pred Sab = Sex
  pred Dom = Sab
~~~
Agora o `..` funciona.
#### Segundo modo
~~~haskell
data DiaDaSemana = Dom | Seg | Ter | Qua | Qui | Sex | Sab
  deriving (Eq, Show, Read, Ord, Enum, Bounded)
~~~
Usando o `deriving` pedimos para implementar para gente uma derivação trivial do ``Eq`` para o nosso data. O `deriving` só é capaz de derivar algumas classes: 
- `Eq`: ele é igual a ele mesmo e diferente de todo o resto
- `Show`: ele vai transformar o nome do construtor em string e imprimir
- `Read` (a classe de todo mundo que dado uma string eu sei transformar naquele tipo): se eu der uma string ele sabe converter naquele mesmo (se colocar "Jan" ele vai associar ao Jan)
- `Ord`: ele segue a ordem que foi escrito no data
- ``Enum``: ele segue a ordem que foi escrito no data também
- ``Bounded`` (são todos os tipos que existem um primeiro e um último): ele vai pegar o primeiro e o último da ordem que está no data
Não é possível fazer um ``deriving`` para uma classe que eu criei
#### Voltando a criar tipos
~~~haskell
data Arvore = Nula | No Arvore Integer Arvore
  deriving (show, Read, Eq)
  
criaNo :: Integer -> Arvore
criaNo x = No Nula x Nula

adicionaElem :: Integer -> Arvore -> Arvore
adiconaElem x Nula = criaNo x
adicionaElem x (No e n d)
  | x == n = No e n d
  | x < n = No (adicionaElem x e) n d
  | otherwise = No e n (adicionaElem x d)
~~~
Temos dois construtores : `Nula` e `No`. O `No` é um construtor que recebe uma árvore, integer e uma outra árvore para construir.
Para deixar a árvore aceitando qualquer tipo podemos fazer:
~~~haskell
data Arvore a = Nula | No (Arvore a) a (Arvore a

criaNo :: a -> Arvore a
criaNo x = No Nula x Nula

-- mas agora o a tem q ser ordenável para adicionar o elemento, então temos que mudar
adicionaElem :: (Ord a) => a -> Arvore a -> Arvore a
adiconaElem x Nula = criaNo x
adicionaElem x (No e n d)
  | x == n = No e n d
  | x < n = No (adicionaElem x e) n d
  | otherwise = No e n (adicionaElem x d)

 ~~~
Podemos lidar com a impressão usando o case.
~~~haskell
putStrLn $ show $
  case encontra (>10) [4, 5, 2, 10, 19, 3, 21] of
    Nada -> "Não deu"
    Algum x -> "Encontrei esse aqui " ++ show x

-- O encontra retorna Nada ou Algum x onde x é um valor de algum tipo
~~~
Podemos usar o case of nas funções também para selecionar o que retornar
### Monad
O tipo nomad é `IO`. Se ele não tiver nenhum valor, colocamos o unit `()` depois que é um tipo sem valor, tipo o void.
### Manipulando arquivo
~~~haskell
import System.IO

main = do
  h <- openFile "nome-arquivo.extensão" ReadMode
  contents <- hGetContents h
  let ls = lines contents
  let l = length ls
  putStrLn $ show l
  hClose h
~~~
Essa biblioteca faz uma leitura lazy e por isso temos que fechar o arquivo somente depois da impressão porque se não vai dar erro pois ele não leu antes de fechar.
### Pilares de funcional
1. Preguiça
2. Função de primeira classe
3. Função de alta ordem
4. Função pura
5. Recursão
6. Sistema de tipos
7. Estado imutável
8. Transparência Referencial