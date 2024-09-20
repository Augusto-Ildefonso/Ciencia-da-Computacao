# Limite
$$\lim_{x \to x_{d}} f(x) = L$$
## Continuidade
$$\lim_{x \to a} f(x) = f(a)$$
## Propriedades
1. $\displaystyle \lim_{x \to a} f(x) + g(x) = L + M$
2. $\displaystyle \lim_{x \to a} k \, f(x) = k \, f(x) = k \, L$; desde que $M \neq 0$
3. $\displaystyle \lim_{x \to a} f(x) g(x) = L \times M$
4. $\displaystyle \lim_{x \to a} \frac{f(x)}{g(x)} = \frac{L}{M}$; desde que $M \neq 0$
5. $\displaystyle \lim_{x \to a^{+}} f(x) = L$
6. $\displaystyle \lim_{x \to b^{-}} f(x) = M$
7. $\displaystyle \lim_{x \to a} f(x)$ existe <=> $L = M$
8. Se $f: A \subset \mathbb{R} \to \mathbb{R}$ é contínua e $Im \, f: B = D$ e $g(x)$, $\lim_{x \to a} g(x) = L$, então: $\displaystyle \lim_{x \to a} f(g(x)) = f(L)$ 
## Teorema do Confronto
Se $f, g, h: A \to \mathbb{R}$ são tais que $f(x) < g(x) < h(x)$, $\forall x \in B \subset A$. $\displaystyle \lim_{x \to a} f(x) = \lim_{x \to a} h(x) = L$. Então $\displaystyle \lim_{x \to a} g(x) = L$ . 

Disso temos também: $\displaystyle \lim_{x \to a} f(x) = 0$ e $|g(x)| \leq M$ => $\lim_{x \to a} f(x) \, g(x) = 0$.
## Limites Fundamentais
1. $$\displaystyle \lim_{x \to 0} \frac{\sin{x}}{x} = 1$$
2. $$\displaystyle \lim_{x \to 0} \frac{\ln(1+x)}{x} = 1$$
3. $$\displaystyle \lim_{x \to 0} \frac{e^{x} - 1}{x} = 1$ $$
4. $$\displaystyle \lim_{x \to \infty} (1 + \frac{1}{x})^{x} = e$$ 
5. $$\displaystyle \lim_{x \to \infty} (1 + \frac{a}{x})^{x} = e^{a}$$
Extra: $\displaystyle \lim_{x\to \infty} x = \lim_{x \to 0} \frac{1}{x}$
## Quando o limite não existe?
1. Os limites laterais são distintos
2. Se $x$ se aproxima de a, f(x) cresce, decresce ou oscila sem se aproximar de um valor fixo
## Assíntotas
1. Assíntota Vertical
	$x = a$ é assíntota vertical de $f$ se $\displaystyle \lim_{x \to a^{+}} f(x) = \pm \infty$ e $\displaystyle \lim_{x \to a^{-}} f(x) = \pm \infty$
2. Assíntota Horizontal
	$y = b$ é assíntota horizontal de $y = f(x)$ quando $\displaystyle \lim_{x \to \infty^{+-}} = b$ 
# Derivadas
$$f'(a) = \lim_{x \to a} \frac{f(x) - f(a)}{x-a}$$

ou

$$f'(a) = \lim_{h \to 0} \frac{f(h+a) - f(a)}{h}$$

A derivada só existe se o limite existe
## Notações
1. $f'(a)$
2. $\displaystyle \frac{d f(a)}{dx}$
3. $y = f(x)$ -> $\displaystyle \frac{dy}{dx} = y'$
## Interpretações da Derivada
1. Geométrica
	A derivada é o coeficiente angular da reta tangente a um ponto. 
	$$y - f(a) = f'(a) \, (x-a)$$
	
1. Física
	A derivada da função da posição é a velocidade instantânea e a derivada de $v(t)$ é a aceleração. 
	$$x'(t) = v(t)$$
## Derivadas fundamentais
1. Regra do tombo

	$\displaystyle f(x) = x^{a}$, $a \in \mathbb{R}$
	
	$f'(x) = a \, x^{a - 1}$
2. $\displaystyle f(x) = e^{x} \Longrightarrow f'(x) = e^{x}$
3. $\displaystyle f(x) = \ln{x} \Longrightarrow f'(x) = \frac{1}{x}$
4. $\displaystyle f(x) = \sin(x) \Longrightarrow f'(x) = \cos{x}$
5. $\displaystyle f(x) = \cos{x} \Longrightarrow f'(x) = - \sin{x}$
6. $\displaystyle f(x) = a^{x} \Longrightarrow f'(x) = a^{x} \ln{a}$, onde $a \in \mathbb{R}$
## Existência de derivada
Se $f: A \subset \mathbb{R} \longrightarrow \mathbb{R}$ é derivável em a, então $f$ é contínua em $a$.

Se $f$ é descontínua em $x = a$, então a derivada não existe.
## Propriedades
1. $\displaystyle (f+g)' (a) = f'(a) + g'(a)$
2. $\displaystyle (k f)' (a) = k  f'(a)$
3. $\displaystyle (f \times g)' (a) = f'(a)  g(a) + f(a)  g'(a)$
4. $\displaystyle \left( \frac{f}{g} \right)' (a) = \frac{f'(a)  g(a) - f(a)  g'(a)}{(g(a))^{2}}$ 
## Regra da Cadeia
$$f(x) = g(h(x))$$

$$f'(x) = (g \circ h)' (x) = g'(h(x))  h'(x)$$

Dica: $\displaystyle f(x) = (x^{2} + 1)^{x} = e^{\ln{(x^{2} + 1)^{x}}} = e^{x \, \ln{(x^2 + 1)}}$  

Dica: pode ser aplicada diversas vezes.
## Derivadas de Ordem Superior
Dado que existe uma derivada $f'(a)$, podemos pensar na derivada dela $(f')' (a) = f''(a)$. Podemos continuar este processo quantas vezes quisermos.

$\displaystyle f''$ é a derivada segunda.

$\displaystyle f'''$ é a derivada terceira.

$\displaystyle f^{(n)}$ é a derivada enésima.
## Derivação Implícita
Exemplo: $y = f(x)$ e $\displaystyle y^{3} + y = x$

$$\frac{d}{dx} (y^{3} +y) = \frac{d}{dx} (x)$$

$$3y^{2} \, \frac{dy}{dx} + \frac{dy}{dx} = 1$$

$$\frac{dy}{dx} (3y^{2} + 1) = 1$$

$$\frac{dy}{dx} = \frac{1}{3y^{2} + 1} = \frac{1}{3 \, (f(x))^{2} + 1}$$
## Derivada da Função Inversa
Usa a derivada implícita e a regra da cadeia.

$$f \circ f^{-1} = y$$

$$\frac{d}{dx} f(f^{-1}(x)) \, \cdot \, \frac{d}{dx} f^{-1}(x) = 1$$

$$\frac{d}{dx} f^{-1} (x) = \frac{1}{\frac{d}{dx}f(f^{-1}(x))}$$

Propriedade gráfica: o gráfica de $f^{-1}$ é "espelhado" do gráfico de $f$ pela reta $y = x$.
## Teoremas de Continuidade
1. Teorema de Bolzano (Anulamento)
	>>Seja $\displaystyle f: I \subset \mathbb{R} \longrightarrow \mathbb{R}$ contínua, onde $I$ é um intervalo fechado $[a, b]$. Suponha que $f(a)$ e $f(b)$ tem sinais opostos. Então existe $\displaystyle c \in (a, b)$ tal que $f(c) = 0$ ($f(a) \, \cdot \, f(b) < 0$).
2.  Teorema do Valor Intermediário
	>> Seja  $\displaystyle f: I \subset \mathbb{R} \longrightarrow \mathbb{R}$ contínua no intervalo fechado $I = [a, b]$. Também $\displaystyle c \in \mathbb{R}$ e $\gamma$ é um número entre $f(a)$ e $f(b)$. Então existe $c \in (a, b)$ tal que $f(c) = \gamma$.
	>> 
3. Teorema de Weierstrass
	>> Seja  $\displaystyle f: [a, b] \subset \mathbb{R} \longrightarrow \mathbb{R}$ contínua. Então existem $x_{1}, x_{2} \in [a,b]$ tais que $f(x_{1}) \leq f(x) \leq f(x_{2})$, $\forall x \in (a, b)$. Onde, $x_{1}$ é o ponto de mínimo de $f$ e $f(x_{1})$ é o valor mínimo de f e $x_{2}$ é o ponto de máximo de $f$ e $f(x_{2})$ é o valor máximo de f.