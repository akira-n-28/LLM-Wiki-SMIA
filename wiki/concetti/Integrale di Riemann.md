---
tipo: concetto
titolo: Integrale di Riemann
tag: [analisi, matematica, analisi-1]
cluster: analisi
fonti: 1
ultima-modifica: 2026-05-06
---

# Integrale di Riemann

## Definizione

Data una **partizione** $P=\{a=x_0<x_1<\cdots<x_n=b\}$ di $[a,b]$, si definiscono le **somme di Darboux**:
$$S^-(f,P) = \sum_{k=1}^n\inf_{[x_{k-1},x_k]}f\cdot(x_k-x_{k-1}), \qquad S^+(f,P) = \sum_{k=1}^n\sup_{[x_{k-1},x_k]}f\cdot(x_k-x_{k-1})$$

$f:[a,b]\to\mathbb{R}$ è **Riemann-integrabile** se $\sup_P S^-(f,P) = \inf_P S^+(f,P)$, e il valore comune è $\int_a^b f(x)\,dx$.

**Criterio di integrabilità.** $f$ è integrabile $\Leftrightarrow$ $\forall\varepsilon>0\ \exists P:\ S^+(f,P)-S^-(f,P)<\varepsilon$.

**Classi integrabili.** Ogni $f\in C^0([a,b])$ è integrabile. Ogni $f$ monotona su $[a,b]$ è integrabile.

## Proprietà

- **Linearità.** $\int_a^b(\alpha f+\beta g)=\alpha\int_a^b f+\beta\int_a^b g$.
- **Monotonia.** $f\leq g$ $\Rightarrow$ $\int_a^b f\leq\int_a^b g$.
- **Additività.** $\int_a^b f = \int_a^c f + \int_c^b f$ per $c\in(a,b)$.
- **Stima.** $\left|\int_a^b f\right|\leq\int_a^b|f|\leq M(b-a)$ se $|f|\leq M$.

## Teorema Fondamentale del Calcolo

**TFC II (funzione integrale).** Se $f\in C^0([a,b])$, la funzione $F(x)=\int_a^x f(t)\,dt$ soddisfa $F'(x)=f(x)$.

**TFC I (Torricelli-Barrow).** Se $F$ è una primitiva di $f$ (cioè $F'=f$) su $[a,b]$:
$$\int_a^b f(x)\,dx = F(b) - F(a) =: \bigl[F(x)\bigr]_a^b$$

## Tecniche di integrazione

**Per parti.** Se $f,g\in C^1([a,b])$:
$$\int_a^b f'(x)g(x)\,dx = \bigl[f(x)g(x)\bigr]_a^b - \int_a^b f(x)g'(x)\,dx$$

**Sostituzione.** Se $\varphi:[c,d]\to[a,b]$ è $C^1$ con $\varphi(c)=a$, $\varphi(d)=b$:
$$\int_a^b f(x)\,dx = \int_c^d f(\varphi(t))\,\varphi'(t)\,dt$$

**Frazioni parziali.** Per $\int R(x)\,dx$ con $R$ funzione razionale: decomporre $R(x)$ in somma di frazioni semplici del tipo $\frac{A}{x-a}$, $\frac{Bx+C}{x^2+px+q}$ (con $\Delta<0$), integrabili elementarmente.

## Valor medio

$$\frac{1}{b-a}\int_a^b f(x)\,dx \in [\min f, \max f]$$

Se $f\in C^0([a,b])$, per il teorema dei valori intermedi $\exists\xi\in(a,b):\ f(\xi)=\frac{1}{b-a}\int_a^b f$.

## Integrali impropri

**Caso 1: $b=+\infty$.** $\int_a^{+\infty}f = \lim_{R\to+\infty}\int_a^R f$ (converge/diverge).

**Caso 2: singolarità in $b$.** $\int_a^b f = \lim_{\varepsilon\to 0^+}\int_a^{b-\varepsilon} f$ se $f$ non è limitata in $b$.

Analogamente per $a=-\infty$ o singolarità in $a$.

**Criterio del confronto.** Se $0\leq f\leq g$ su $[a,+\infty)$:
- $\int_a^{+\infty}g<+\infty$ $\Rightarrow$ $\int_a^{+\infty}f<+\infty$.
- $\int_a^{+\infty}f=+\infty$ $\Rightarrow$ $\int_a^{+\infty}g=+\infty$.

**Esempi canonici.**
- $\int_1^{+\infty}\frac{1}{x^\alpha}dx$ converge $\Leftrightarrow$ $\alpha>1$.
- $\int_0^1\frac{1}{x^\alpha}dx$ converge $\Leftrightarrow$ $\alpha<1$.

## Criterio integrale per le serie (Cauchy)

Se $f:[1,+\infty)\to[0,+\infty)$ è decrescente:
$$\sum_{k=1}^\infty f(k) \text{ converge} \Leftrightarrow \int_1^{+\infty}f(x)\,dx < +\infty$$

Questo fornisce la convergenza di $\sum 1/k^\alpha$ ($\alpha>1$, vedi [[Successioni]]).

## Connessioni

- Prerequisito: [[Derivata]] (TFC inverte la derivata), [[Continuità di una funzione]] (integrabilità)
- Collegamento a serie: [[Successioni]] (criterio integrale di Cauchy)
- Applicazioni: calcolo di aree, lunghezze d'arco, medie, probabilità

## Fonti

- [[Dispense AnalisiI — Galletti]] (§6, pp. 135-163)
