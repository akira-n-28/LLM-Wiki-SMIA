---
tipo: concetto
titolo: Integrale di Lebesgue
tag: [analisi, matematica, analisi-2]
cluster: analisi
fonti: 1
ultima-modifica: 2026-05-06
---

# Integrale di Lebesgue

## Motivazione

L'integrale di Riemann non gestisce bene:
1. Funzioni con "molti" punti di discontinuità (es. funzione di Dirichlet: $f=1$ su $\mathbb{Q}$, $0$ altrove — non Riemann-integrabile).
2. Passaggio al limite sotto il segno: $\lim\int f_n\neq\int\lim f_n$ senza ipotesi forti.

La teoria di Lebesgue risolve entrambi i problemi.

## Misura di Lebesgue

**Plurintervallo.** Unione finita di intervalli chiusi a due a due privi di punti interni in comune: $m(P)=\sum_i m(I_i)$.

**Misura di aperto/compatto.**
- $m(A)=\sup\{m(P): P\subseteq A, P\text{ plurintervallo}\}$ (aperto).
- $m(K)=\inf\{m(P): P\supseteq K, P\text{ plurintervallo}\}$ (compatto).

**Insieme misurabile** $E\subseteq\mathbb{R}^N$ (limitato): misura interna $m_i(E)=\sup\{m(K):K\subseteq E\}$ e esterna $m_e(E)=\inf\{m(A):A\supseteq E\}$. $E$ è misurabile se $m_i(E)=m_e(E)=:m(E)$.

**Insiemi a misura nulla.** Ogni insieme numerabile ha misura nulla (es. $\mathbb{Q}$). L'integrale non cambia su insiemi a misura nulla.

**"Quasi ovunque" (q.o.).** Una proprietà vale q.o. se l'insieme dove non vale ha misura nulla.

## Integrale di Lebesgue

Si costruisce in due passi:

**Funzioni non negative.** Per $f:E\to[0,+\infty]$ misurabile, $\int_E f\,dx\in[0,+\infty]$.

**Funzioni di segno qualunque.** $f^+(x)=\max\{f(x),0\}$, $f^-(x)=\max\{-f(x),0\}$. Se $\int_E|f|<+\infty$ ($f$ **sommabile**):
$$\int_E f\,dx = \int_E f^+\,dx - \int_E f^-\,dx$$

**Proprietà.** Linearità, monotonia, additività sull'unione disgiunta, $|\int f|\leq\int|f|$.

## Teoremi di convergenza

### Beppo Levi (convergenza monotona)

Sia $(f_n)$ successione di funzioni misurabili non negative con $f_n(x)\leq f_{n+1}(x)$ q.o. e $f_n\to f$ puntualmente. Allora:
$$\lim_{n\to\infty}\int_{\mathbb{R}^N} f_n\,dx = \int_{\mathbb{R}^N} f\,dx$$

*Corollario (integrazione termine a termine).* Se $f_n\geq 0$: $\int\sum_{n=1}^\infty f_n = \sum_{n=1}^\infty\int f_n$.

### Lemma di Fatou

Per $(f_n)$ misurabile non negativa:
$$\int_{\mathbb{R}^N}\liminf_{n\to\infty}f_n\,dx \leq \liminf_{n\to\infty}\int_{\mathbb{R}^N}f_n\,dx$$

(La disuguaglianza può essere stretta.)

### Lebesgue (convergenza dominata)

Sia $f_n\to f$ q.o. su $E$ e $\exists g$ sommabile con $|f_n(x)|\leq g(x)$ q.o. $\forall n$. Allora:
$$\lim_{n\to\infty}\int_E|f_n-f|\,dx = 0 \qquad\text{e quindi}\qquad \lim_{n\to\infty}\int_E f_n\,dx=\int_E f\,dx$$

*Applicazione.* Calcolo di limiti di integrali dipendenti da parametro.

## Derivazione sotto il segno di integrale (Feynman)

Sia $F(t)=\int_E f(x,t)\,dx$. Se:
1. $x\mapsto f(x,t)$ sommabile $\forall t$,
2. $t\mapsto f(x,t)\in C^1$ q.o.,
3. $|\partial_t f(x,t)|\leq g(x)$ q.o. $\forall t$, con $g$ sommabile,

allora $F\in C^1$ e $F'(t)=\int_E\frac{\partial f}{\partial t}(x,t)\,dx$.

## Teorema di Fubini e Tonelli

**Tonelli** (funzioni non negative): $f:\mathbb{R}^N\times\mathbb{R}^k\to[0,+\infty]$ misurabile.
$$\int_{\mathbb{R}^{N+k}}f(x,y)\,dx\,dy = \int_{\mathbb{R}^N}\!\!\int_{\mathbb{R}^k}f(x,y)\,dy\,dx = \int_{\mathbb{R}^k}\!\!\int_{\mathbb{R}^N}f(x,y)\,dx\,dy$$

**Fubini** (funzioni sommabili): stessa formula, ma richiede $f$ sommabile su $\mathbb{R}^{N+k}$.

**Integrali doppi su insiemi normali.** $E=\{(x,y):x\in[a,b],\alpha(x)\leq y\leq\beta(x)\}$:
$$\iint_E f(x,y)\,dx\,dy = \int_a^b\!\!\int_{\alpha(x)}^{\beta(x)}f(x,y)\,dy\,dx$$

## Cambi di variabile

Per $\Phi:A\to B$ diffeomorfismo $C^1$ con $A,B\subseteq\mathbb{R}^N$:
$$\int_B f(y)\,dy = \int_A f(\Phi(x))|\det J_\Phi(x)|\,dx$$

**Coordinate polari** ($N=2$): $x=\rho\cos\theta$, $y=\rho\sin\theta$, $|\det J|=\rho$.
$$\iint_E f\,dx\,dy = \int_0^{2\pi}\!\!\int_0^{R(\theta)}f(\rho\cos\theta,\rho\sin\theta)\,\rho\,d\rho\,d\theta$$

**Coordinate sferiche** ($N=3$): $x=\rho\sin\varphi\cos\theta$, $y=\rho\sin\varphi\sin\theta$, $z=\rho\cos\varphi$, $|\det J|=\rho^2\sin\varphi$.

**Coordinate cilindriche** ($N=3$): $x=\rho\cos\theta$, $y=\rho\sin\theta$, $z=z$, $|\det J|=\rho$.

## Connessioni

- Integrale di Riemann come caso particolare: [[Integrale di Riemann]]
- Spazi costruiti sull'integrale di Lebesgue: [[Spazi Lp]]
- Misura e probabilità: [[Spazio di probabilità]] (misura di probabilità)
- Applicazione: cambio di variabile nelle v.a. ([[Variabile aleatoria]])

## Fonti

- [[Dispense AnalisiII — Galletti]] (§4, pp. 70-112)
