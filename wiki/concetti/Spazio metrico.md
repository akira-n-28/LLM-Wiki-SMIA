---
tipo: concetto
titolo: Spazio metrico
tag: [topologia, ml, matematica, analisi-2]
cluster: analisi
fonti: 2
ultima-modifica: 2026-05-06
---

# Spazio metrico

Coppia $(X, d)$ dove $X$ è un insieme e $d : X \times X \to \mathbb{R}_+$ è una funzione (la **metrica**) che soddisfa:

1. $d(x, y) = 0 \iff x = y$ — non degenere.
2. $d(x, y) = d(y, x)$ — simmetria.
3. $d(x, y) \leq d(x, z) + d(z, y)$ — disuguaglianza triangolare.

## Esempi

- $(\mathbb{R}, |x-y|)$, $(\mathbb{R}^N, \|\cdot\|_2)$, $(\mathbb{R}^N, \|\cdot\|_1)$, $(\mathbb{R}^N, \|\cdot\|_\infty)$.
- $(C^0([a,b]), d_\infty)$ con $d_\infty(f,g)=\sup_{[a,b]}|f-g|$ — la distanza sup-norm.
- $(C^0([a,b]), d_1)$ con $d_1(f,g)=\int_a^b|f-g|$ — metrica $L^1$.

## Topologia in uno spazio metrico

**Palla (intorno sferico).** $B_r(x_0)=\{x\in X: d(x,x_0)<r\}$.

**Aperto.** $A\subseteq X$ aperto se $\forall x\in A\ \exists r>0: B_r(x)\subseteq A$.

**Chiuso.** $C\subseteq X$ chiuso se $X\setminus C$ è aperto.

**Punto di accumulazione.** $x$ è di accumulazione per $Y\subseteq X$ se ogni $B_r(x)$ contiene punti di $Y\setminus\{x\}$. Derivato: $D(Y)$; chiusura: $\bar{Y}=Y\cup D(Y)$.

## Successioni negli spazi metrici

$(x_n)\to x$ in $(X,d)$ se $\lim_{n\to\infty}d(x_n,x)=0$.

In $\mathbb{R}^N$: $(x_n^{(1)},\ldots,x_n^{(N)})\to(x^{(1)},\ldots,x^{(N)})$ $\Leftrightarrow$ ogni coordinata converge.

In $(C^0([a,b]),d_\infty)$: $f_n\to f$ $\Leftrightarrow$ $f_n\rightrightarrows f$ uniformemente ([[Successioni di funzioni]]).

## Spazi metrici completi

**Successione di Cauchy.** $(x_n)$ è di Cauchy se $\forall\varepsilon>0\ \exists\nu: d(x_n,x_m)<\varepsilon\ \forall n,m>\nu$.

Ogni successione convergente è di Cauchy. Il viceversa vale solo negli **spazi completi**.

**Spazio metrico completo.** $(X,d)$ è completo se ogni successione di Cauchy converge a un elemento di $X$.

| Spazio | Completo? |
|---|---|
| $(\mathbb{R},\|\cdot\|)$ | Sì |
| $(\mathbb{R}^N, \|\cdot\|_2)$ | Sì |
| $(C^0([a,b]), d_\infty)$ | Sì |
| $(\mathbb{Q}, |\cdot|)$ | No ($(1+1/n)^n\to e\notin\mathbb{Q}$) |
| $(C^0([-1,1]), d_1)$ | No (controesempio con $f_n$ a tratti che converge a segno di Heaviside) |

## Spazi normati e di Banach

Una **norma** su $V$ è $\|\cdot\|:V\to[0,+\infty)$ con: $\|x\|=0\Leftrightarrow x=0$; $\|\lambda x\|=|\lambda|\|x\|$; $\|x+y\|\leq\|x\|+\|y\|$. Ogni norma induce la metrica $d(x,y)=\|x-y\|$.

**Norme su $\mathbb{R}^N$:** $\|x\|_p=(\sum|x_i|^p)^{1/p}$ per $p\geq 1$; $\|x\|_\infty=\max_i|x_i|$.

**Spazio di Banach.** Spazio normato completo.

Esempi: $(\mathbb{R}^N, \|\cdot\|_p)$, $(C^0([a,b]),\|\cdot\|_\infty)$, $(L^p(E),\|\cdot\|_{L^p})$ ([[Spazi Lp]]).

## Prodotto scalare

$\langle x,y\rangle=\sum_{i=1}^N x_iy_i$ su $\mathbb{R}^N$. Proprietà: simmetria, bilinearità, definitezza positiva.

**Disuguaglianza di Cauchy-Schwarz.** $|\langle x,y\rangle|\leq\|x\|_2\|y\|_2$.

## A cosa serve in ML

**Dimensionality reduction non lineare** ([[Multidimensional Scaling]], [[t-SNE]]): embedding $f:X\to Z$ che preserva distanze. Vedi [[Embedding isometrico]].

## Connessioni

- Successioni di funzioni: [[Successioni di funzioni]] (convergenza uniforme = convergenza in $(C^0,d_\infty)$)
- Spazi funzionali completi: [[Spazi Lp]] (Banach per ogni $p$)
- Contrazione e punto fisso: [[Teorema delle Contrazioni]]

## Fonti

- [[Dispense Machine Learning — Galletti]] (§7.1, p. 23)
- [[Dispense AnalisiII — Galletti]] (§2, pp. 27-37)
