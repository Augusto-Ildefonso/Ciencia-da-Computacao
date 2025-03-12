# Linguagens
Uma linguagem puramente funcional é o Haskell, porém algumas outras aceitam programar funcional, como Python, Java, Javascript, Ruby, C++, Rust e R. É interessante essas linguagens que permitem programar funcional pois é possível mesclar os paradigmas e fazer parte funcional e parte não funcional.
# História
Alonso Church e Alan Turing pesquisavam o que seria o computar. O Church criou um cálculo chamado "lambda cálculo" (o mesmo lambda que usamos em python e é usado em Haskell também) e disse ele concluiu que tudo aquilo que pode ser computável em uma expressão lambda é computável. Já Turing criou a máquina de Turing e com ela ele concluiu que tudo aquilo que pode ser computado, pode ser computado com uma máquina de Turing. Dessas duas proposições surgiu a Tese de Church-Turing
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
~~~haskell
main = do -- Monad
  putStrLn "Hello World!" -- Essa função putStrLn imprime uma linha de string na tela
  putStrLn "Oi"
  putStrLn $ show z -- O show transforma o x em string e o dólar separa as funções e faz primeiro o que está na frente (show) e depois o que está antes (putStrLn)
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
o6 = 7:o2 -- O : pega um elemento e uma lista e retorna uma lista com o elemento que ele pegou na primeira posição da 
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
