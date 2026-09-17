---
tipo: concetto
titolo: Polinomi di Taylor
tag: [analisi, matematica, analisi-1]
cluster: analisi
fonti: 1
ultima-modifica: 2026-05-06
---

# Polinomi di Taylor

## Definizione

Il **polinomio di Taylor di ordine $n$** di $f$ centrato in $x_0$ è:
$$T^n_{f;x_0}(x) = \sum_{k=0}^{n}\frac{f^{(k)}(x_0)}{k!}(x-x_0)^k$$

Richiede $f\in C^n$ in un intorno di $x_0$.

## Resto di Peano

Se $f\in C^n$ in un intorno di $x_0$:
$$f(x) = T^n_{f;x_0}(x) + o\bigl((x-x_0)^n\bigr) \quad (x\to x_0)$$

Il polinomio di Taylor è **l'unico** polinomio di grado $\leq n$ con questa proprietà.

## Resto di Lagrange

Se $f\in C^{n+1}$ in $[x_0, x]$ (o $[x, x_0]$):
$$f(x) = T^n_{f;x_0}(x) + R_n(x), \quad R_n(x) = \frac{f^{(n+1)}(\xi)}{(n+1)!}(x-x_0)^{n+1}$$
per qualche $\xi$ compreso tra $x_0$ e $x$. Utile per **stime quantitative** dell'errore.

*Dimostrazione:* via teorema di Cauchy (generalizzazione di Lagrange al rapporto $R_n(x)/(x-x_0)^{n+1}$).

## Sviluppi notevoli in $x_0=0$

$$e^x = \sum_{k=0}^n\frac{x^k}{k!} + o(x^n) = 1+x+\frac{x^2}{2}+\frac{x^3}{6}+\cdots$$

$$\sin x = \sum_{k=0}^{\lfloor(n-1)/2\rfloor}\frac{(-1)^k}{(2k+1)!}x^{2k+1}+o(x^n) = x-\frac{x^3}{6}+\frac{x^5}{120}+\cdots$$

$$\cos x = \sum_{k=0}^{\lfloor n/2\rfloor}\frac{(-1)^k}{(2k)!}x^{2k}+o(x^n) = 1-\frac{x^2}{2}+\frac{x^4}{24}+\cdots$$

$$\ln(1+x) = \sum_{k=1}^n\frac{(-1)^{k+1}}{k}x^k+o(x^n) = x-\frac{x^2}{2}+\frac{x^3}{3}-\cdots$$

$$(1+x)^\alpha = 1+\alpha x+\frac{\alpha(\alpha-1)}{2}x^2+\cdots+\binom{\alpha}{n}x^n+o(x^n)$$

$$\frac{1}{1-x} = 1+x+x^2+\cdots+x^n+o(x^n)$$

## Tecnica di calcolo

1. Identificare l'ordine richiesto (di solito il grado del denominatore o del confronto).
2. Espandere ciascuna funzione al giusto ordine, tenendo traccia degli o-piccoli.
3. Sommare/moltiplicare/comporre: gli o-piccoli si propagano per le proprietà in [[Limiti notevoli]].
4. Leggere il coefficiente desiderato o il comportamento asintotico.

**Cambio di variabile.** Se $u=g(x)\to 0$ per $x\to x_0$, sostituire direttamente: $f(g(x))=T^n_{f;0}(g(x))+o(g(x)^n)$.

## Connessioni

- Prerequisito: [[Derivata]] ($f^{(k)}$ esistente), [[Limiti notevoli]] (o-piccoli)
- Applicazione: calcolo di limiti in forma $0/0$, approssimazioni numeriche, discesa del gradiente (Taylor al primo ordine = linearizzazione)
- Convergenza della serie di Taylor: separato dalla questione dell'approssimazione locale

## Fonti

- [[Dispense AnalisiI — Galletti]] (§5.4, pp. 127-134)
