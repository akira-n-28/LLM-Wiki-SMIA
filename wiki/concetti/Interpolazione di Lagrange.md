---
tipo: concetto
titolo: Interpolazione di Lagrange
tag: [calcolo-numerico, approssimazione, metodi-numerici]
cluster: numerico
fonti: 1
ultima-modifica: 2026-05-05
---

# Interpolazione di Lagrange

Dati $n+1$ nodi distinti $x_0, \ldots, x_n$ e valori $f_0, \ldots, f_n$, il **polinomio interpolante di Lagrange** è l'unico $p \in \mathcal{P}_n$ tale che $p(x_i) = f_i$ per ogni $i$.

## Basi di Lagrange

Le **basi di Lagrange** associate ai nodi sono:

$$\ell_i(x) = \prod_{j=0, j\neq i}^{n} \frac{x - x_j}{x_i - x_j}, \quad i = 0, \ldots, n$$

Soddisfano $\ell_i(x_j) = \delta_{ij}$ (delta di Kronecker). Il polinomio interpolante è:

$$p(x) = \sum_{i=0}^{n} f_i\, \ell_i(x)$$

## Formula dell'errore

Se $f \in C^{n+1}([a,b])$, allora per ogni $x \in [a,b]$ esiste $\xi = \xi(x) \in (a,b)$ tale che:

$$f(x) - p(x) = \frac{f^{(n+1)}(\xi)}{(n+1)!}\, \omega_{n+1}(x), \quad \omega_{n+1}(x) = \prod_{i=0}^{n}(x-x_i)$$

L'errore dipende sia dalla regolarità di $f$ che dalla distribuzione dei nodi (tramite $\omega_{n+1}$).

## Fenomeno di Runge

Con nodi **equidistanti** su $[-1,1]$ e grado $n$ crescente, l'errore di interpolazione diverge ai bordi dell'intervallo (per funzioni come $f(x)=1/(1+25x^2)$). Il grado alto non garantisce la convergenza.

**Causa:** $\|\omega_{n+1}\|_\infty$ cresce esponenzialmente con $n$ per nodi equidistanti.

## Costante di Lebesgue

$$\Lambda_n(X) = \max_{x \in [a,b]} \sum_{i=0}^{n} |\ell_i(x)|$$

Misura l'amplificazione degli errori sui valori $f_i$. Vale $\|p - f\|_\infty \leq (1 + \Lambda_n) \|p^* - f\|_\infty$ (dove $p^*$ è il best approximation). Per nodi equidistanti, $\Lambda_n \sim 2^n/n$; per nodi di Gauss-Lobatto, $\Lambda_n \sim \log n$.

## Nodi di Gauss-Lobatto (Chebyshev-Lobatto)

$$x_k = -\cos\!\left(\frac{k\pi}{n}\right), \quad k = 0, \ldots, n$$

Minimizzano (quasi) $\|\omega_{n+1}\|_\infty$ su $[-1,1]$ e garantiscono $\Lambda_n = O(\log n)$: crescita logaritmica invece che esponenziale. Praticamente eliminano il fenomeno di Runge.

## Interpolazione composita (piecewise)

Invece di usare un unico polinomio di grado $n$ alto, si suddivide $[a,b]$ in $m$ sottointervalli di ampiezza $h=(b-a)/m$ e si interpola con polinomi di grado basso (tipicamente 1 o 3) su ciascuno.

**Errore composito (grado 1):** $O(h^2)$; **(grado 3, spline cubica):** $O(h^4)$.

La convergenza è garantita per qualsiasi $f$ continua al crescere di $m$, indipendentemente da dove cadono i nodi locali.

## Legame con l'integrazione numerica

Le formule di quadratura di [[Integrazione numerica]] (trapezi, Cavalieri-Simpson) si ottengono integrando esattamente il polinomio interpolante di $f$ sui nodi.

## Connessioni

- Prerequisito di: [[Integrazione numerica]]
- Si collega a: [[Metodi per equazioni non lineari]], [[Numeri di macchina e aritmetica floating-point]]
- Discusso in: [[Metodi Numerici]]

## Fonti

- [[Dispense Metodi Numerici — Galletti]]
