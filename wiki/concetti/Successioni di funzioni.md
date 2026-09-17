---
tipo: concetto
titolo: Successioni di funzioni
tag: [analisi, matematica, analisi-2]
cluster: analisi
fonti: 1
ultima-modifica: 2026-05-06
---

# Successioni di funzioni

## Convergenza puntuale

Data $(f_n)_{n\in\mathbb{N}}$ con $f_n:I\subseteq\mathbb{R}\to\mathbb{R}$, la successione **converge puntualmente** a $f:I\to\mathbb{R}$ se:
$$\forall x\in I,\quad \lim_{n\to+\infty}f_n(x)=f(x)$$

Equivalentemente: $\forall\varepsilon>0\ \forall x\in I\ \exists\nu_{\varepsilon,x}$ t.c. $|f_n(x)-f(x)|<\varepsilon\ \forall n>\nu_{\varepsilon,x}$.

Il $\nu$ dipende sia da $\varepsilon$ che da $x$.

**Esempio canonico.** $f_n(x)=x^n$ su $[0,1]$: converge puntualmente a $f(x)=0$ per $x\in[0,1)$ e $f(1)=1$. La limite è discontinua anche se ogni $f_n$ è continua.

## Convergenza uniforme

$(f_n)$ **converge uniformemente** a $f$ su $I$ se:
$$\lim_{n\to+\infty}\sup_{x\in I}|f_n(x)-f(x)|=0$$

Equivalentemente: $\forall\varepsilon>0\ \exists\nu_\varepsilon$ (non dipendente da $x$) t.c. $|f_n(x)-f(x)|<\varepsilon\ \forall x\in I\ \forall n>\nu_\varepsilon$.

**Uniforme $\Rightarrow$ puntuale** (ma non viceversa: $f_n(x)=x^n$ su $[0,1]$ non converge uniformemente).

## Proprietà della convergenza uniforme

Se $f_n\rightrightarrows f$ uniformemente su $[a,b]$:

- **Continuità.** Se ogni $f_n\in C^0([a,b])$, allora $f\in C^0([a,b])$.
- **Integrazione.** $\displaystyle\lim_{n\to+\infty}\int_a^b f_n = \int_a^b f$ (scambio limite/integrale).
- **Derivazione.** Se $f_n\in C^1$ e $f_n'\rightrightarrows g$, allora $f'=g$ e $f\in C^1$.

La convergenza puntuale non garantisce nessuna di queste proprietà.

## Serie di funzioni

Data $(g_n)$, la **serie** $\sum_{n=0}^\infty g_n$ converge puntualmente/uniformemente se le somme parziali $s_N=\sum_{n=0}^N g_n$ convergono puntualmente/uniformemente.

**Criterio di Weierstrass (M-test).** Se $|g_n(x)|\leq M_n\ \forall x\in I$ e $\sum M_n<+\infty$, allora $\sum g_n$ converge uniformemente (e assolutamente) su $I$.

## Serie di potenze

Una **serie di potenze** è $\sum_{n=0}^\infty a_n(x-x_0)^n$.

**Raggio di convergenza** (Cauchy-Hadamard): posto $l=\limsup_{n\to\infty}\sqrt[n]{|a_n|}$,
$$\varphi = \begin{cases} 0 & l=+\infty \\ 1/l & l\in(0,+\infty) \\ +\infty & l=0 \end{cases}$$

La serie converge assolutamente per $|x-x_0|<\varphi$ e diverge per $|x-x_0|>\varphi$. Su ogni $[x_0-r,x_0+r]$ con $r<\varphi$ la convergenza è uniforme.

**Proprietà della serie di potenze** (all'interno del raggio):
- È continua, derivabile e integrabile termine a termine.
- La serie derivata ha lo stesso raggio di convergenza.

## Serie di Taylor e sviluppabilità

$f$ è **sviluppabile in serie di Taylor** in $x_0$ se coincide con la sua serie di Taylor in un intorno di $x_0$:
$$f(x) = \sum_{n=0}^\infty \frac{f^{(n)}(x_0)}{n!}(x-x_0)^n$$

**Criterio di sviluppabilità.** Se $f\in C^\infty$ in un intorno di $x_0$ e il resto di Lagrange $R_n(x)\to 0$ per $n\to\infty$, allora $f$ è sviluppabile.

Condizione sufficiente: $\exists M>0$ t.c. $|f^{(n)}(x)|\leq M^n$ in un intorno di $x_0$ (es. $\sin$, $\cos$, $e^x$).

**Funzioni di classe $C^\infty$ non analitiche** esistono: $f(x)=e^{-1/x^2}$ (con $f(0)=0$) ha tutti i valori della serie di Taylor nulli in 0, ma $f\neq 0$.

## Connessioni

- Prerequisito: [[Successioni]], [[Polinomi di Taylor]] (resto di Lagrange)
- Spazio $C^0([a,b])$ come spazio metrico completo: [[Spazio metrico]]
- Serie di funzioni in $L^p$: [[Spazi Lp]]
- Applicazioni: analisi delle trasformate di Fourier, approssimazione di funzioni

## Fonti

- [[Dispense AnalisiII — Galletti]] (§1, pp. 2-26)
