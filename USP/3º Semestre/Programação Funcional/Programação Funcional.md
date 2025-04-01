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
## Introdução
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
## Guardas em Haskell
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
## Entrada e Saída de Dados
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
## Função de alta ordem
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
### Curry
Haskell Curry foi um matemático que criou o conceito de curry. Esse conceito que permite ter compiladores eficientes para linguagens funcionais. A ideia de curry é que toda função recebe só um valor e retorna só um valor. Em todas as funções do haskell tem curry, até mesmo quando parece que não tem.
~~~haskell
multiplica x y = x * y -- Aqui da impressão que tem dois parâmetros, mas veja abaixo como o compilador enxerga
multiplica x = \y -> x * y -- Poderiamos ainda exagerar a representação igual abaixo
multiplica = \x -> (\y -> x * y)
~~~
E assim vai seguindo, com uma função sendo um parâmetro de uma função até que todas tenham só um parâmetro e retorna só um valor.
## Tipos
Vejamos os tipos que existem em haskell e como são definidas. Podemos também definir os tipos e assim toda vez que o compilador ver a variável ele vai ver como do tipo que foi definido.
### Integer
Não tem limite.
~~~haskell
k :: Integer
k = 5
~~~
### Inteiro
Ele é limitado, igual o int de C.
~~~haskell
k :: Int
m = 5
~~~
### Vetor
~~~haskell
a :: [Integer] -- Uma lista de Integer
a = [1, 2, 3, 4, 5]
~~~
### Função
~~~haskell
ehPositivo :: Integer -> Bool
ehPositivo x = x > 0
~~~
### Tipo genérico
Esse tipo é um tipo genérico, que vai depender do que for colocado neles.
~~~haskell
ehPositivo :: [a] -> Bool -> [a] -> [a]
~~~
## TypeClass
As classes englobam diversos tipos que tem algum tipo de característica em comum
### Class Eq
Essa classe agrupa todos os tipos que podem ser feitos a operação de igualdade.
~~~haskell
(Eq a) => ...
~~~
### Class Num
Essa classe agrupa todos os tipos que podem ser somados.
~~~haskell
(Num a) => ...
~~~
### Class Ord
Essa classe agrupa os tipos que podem ser feitos as operações de maior e menor.
~~~haskell
(Ord a) => ...
~~~

## Identificadores
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
## Quick-Sort
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