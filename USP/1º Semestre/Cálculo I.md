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
8. Se $f: A \subset \mathbb{R} \to \mathbb{R}$ é contínua e $Im \, f: B = D$ e $g(x)$, $\displaystyle \lim_{x \to a} g(x) = L$, então: $\displaystyle \lim_{x \to a} f(g(x)) = f(L)$ 
## Teorema do Confronto
Se $f, g, h: A \to \mathbb{R}$ são tais que $f(x) < g(x) < h(x)$, $\forall x \in B \subset A$. $\displaystyle \lim_{x \to a} f(x) = \lim_{x \to a} h(x) = L$. Então $\displaystyle \lim_{x \to a} g(x) = L$. 

Disso temos também: $\displaystyle \lim_{x \to a} f(x) = 0$ e $|g(x)| \leq M$ => $\displaystyle \lim_{x \to a} f(x) \, g(x) = 0$.
## Limites Fundamentais
1. $\displaystyle \lim_{x \to 0} \frac{\sin{x}}{x} = 1$
2. $\displaystyle \lim_{x \to 0} \frac{\ln(1+x)}{x} = 1$
3. $\displaystyle \lim_{x \to 0} \frac{e^{x} - 1}{x} = 1$ 
4. $\displaystyle \lim_{x \to \infty} (1 + \frac{1}{x})^{x} = e$ 
5. $\displaystyle \lim_{x \to \infty} (1 + \frac{a}{x})^{x} = e^{a}$
Extra: $\displaystyle \lim_{x\to \infty} x = \lim_{x \to 0} \frac{1}{x}$
## Quando o limite não existe?
1. Os limites laterais são distintos
2. Se $x$ se aproxima de a, f(x) cresce, decresce ou oscila sem se aproximar de um valor fixo
## Assíntotas
1. Assíntota Vertical
	$x = a$ é assíntota vertical de $f$ se $\displaystyle \lim_{x \to a^{+}} f(x) = \pm \infty$ e $\displaystyle \lim_{x \to a^{-}} f(x) = \pm \infty$
2. Assíntota Horizontal
	$y = b$ é assíntota horizontal de $y = f(x)$ quando $\displaystyle \lim_{x \to \infty^{+-}} = b$ 
