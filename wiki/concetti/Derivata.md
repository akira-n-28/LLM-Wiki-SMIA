---
tipo: concetto
titolo: Derivata
tag: [analisi, matematica, analisi-1]
cluster: analisi
fonti: 1
ultima-modifica: 2026-05-06
---

# Derivata

## Definizione

Il **rapporto incrementale** di $f$ in $x_0$ con incremento $h$ è $\frac{f(x_0+h)-f(x_0)}{h}$.

$f:A\subset\mathbb{R}\to\mathbb{R}$ è **derivabile in $x_0\in A$** se esiste finito:
$$f'(x_0) = \lim_{h\to 0}\frac{f(x_0+h)-f(x_0)}{h}$$

**Significato geometrico.** $f'(x_0)$ è la pendenza della retta tangente al grafico in $(x_0, f(x_0))$.

**Approssimazione affine.** Derivabilità $\Leftrightarrow$ esistenza di $m$ tale che:
$$f(x) = f(x_0) + m(x-x_0) + o(x-x_0) \quad (x\to x_0)$$
e in tal caso $m = f'(x_0)$.

**Derivabilità implica continuità**, ma non viceversa (es. $|x|$ in $x=0$).

## Derivate fondamentali

| $f(x)$ | $f'(x)$ |
|---|---|
| $c$ (costante) | $0$ |
| $x^\alpha$ | $\alpha x^{\alpha-1}$ |
| $\sin x$ | $\cos x$ |
| $\cos x$ | $-\sin x$ |
| $e^x$ | $e^x$ |
| $a^x$ | $a^x \ln a$ |
| $\ln x$ | $\dfrac{1}{x}$ |
| $\log_a x$ | $\dfrac{1}{x\ln a}$ |
| $\arctan x$ | $\dfrac{1}{1+x^2}$ |
| $\arcsin x$ | $\dfrac{1}{\sqrt{1-x^2}}$ |

## Regole di derivazione

**Somma/prodotto scalare.** $(f+g)'=f'+g'$, $(cf)'=cf'$.

**Prodotto (Leibniz).** $(fg)' = f'g + fg'$.

**Quoziente.** $\left(\dfrac{f}{g}\right)' = \dfrac{f'g - fg'}{g^2}$ per $g\neq 0$.

**Catena.** $(g\circ f)'(x) = g'(f(x))\cdot f'(x)$.

**Funzione inversa.** Se $f$ è invertibile e derivabile con $f'(x)\neq 0$:
$$(f^{-1})'(y) = \frac{1}{f'(f^{-1}(y))}$$

## Classi di regolarità

$f\in C^0$: continua. $f\in C^1$: derivabile con $f'$ continua. $f\in C^n$: $n$ volte derivabile con $f^{(n)}$ continua. $f\in C^\infty$: derivabile infinite volte.

## Teoremi sui valori critici

**Teorema di Fermat.** Se $f$ ha un estremo locale in $x_0\in\mathring{A}$ ed è derivabile in $x_0$, allora $f'(x_0)=0$.

**Teorema di Rolle.** Se $f\in C^0([a,b])$, derivabile su $(a,b)$, con $f(a)=f(b)$, allora $\exists\xi\in(a,b):\ f'(\xi)=0$.

**Teorema di Lagrange (del valor medio).** Se $f\in C^0([a,b])$ e derivabile su $(a,b)$:
$$\exists\xi\in(a,b):\ f'(\xi) = \frac{f(b)-f(a)}{b-a}$$

*Dimostrazione:* si applica Rolle a $g(x) = f(x) - \frac{f(b)-f(a)}{b-a}(x-a)$.

**Corollari di Lagrange.**
- $f'=0$ su $(a,b)$ $\Rightarrow$ $f$ costante.
- $f'\geq 0$ su $(a,b)$ $\Rightarrow$ $f$ crescente; $f'>0$ $\Rightarrow$ strettamente crescente.
- $f'\leq 0$ su $(a,b)$ $\Rightarrow$ $f$ decrescente.

## Monotonia e convessità

**Monotonia.** $f$ crescente su $I$ $\Leftrightarrow$ $f'(x)\geq 0\ \forall x\in I$ (con $f'>0$ quasi ovunque).

**Convessità.** $f$ è **convessa** (concava verso l'alto) su $I$ se $\forall x,y\in I,\ \lambda\in[0,1]$:
$$f(\lambda x+(1-\lambda)y)\leq\lambda f(x)+(1-\lambda)f(y)$$

Se $f\in C^2$: convessa $\Leftrightarrow$ $f''(x)\geq 0$ su $I$.

**Punti di flesso.** $x_0$ è un punto di flesso se $f''$ cambia segno in $x_0$.

## Classificazione dei punti critici

Sia $f'(x_0)=0$ (punto critico).

- Se $f''(x_0)>0$: **minimo locale**.
- Se $f''(x_0)<0$: **massimo locale**.
- Se $f''(x_0)=0$: test non conclusivo (può essere flesso o estremo).

## Studio di funzione

Schema: **dominio** → **simmetrie** → **segno e zeri** → **monotonia** ($f'$) → **estremi** → **convessità** ($f''$) → **asintoti** → **grafico**.

**Asintoti:**
- Orizzontale $y=l$: $\lim_{x\to\pm\infty}f(x)=l$.
- Obliquo $y=mx+q$: $m=\lim_{x\to+\infty}f(x)/x$, $q=\lim_{x\to+\infty}(f(x)-mx)$.
- Verticale $x=x_0$: $\lim_{x\to x_0^\pm}f(x)=\pm\infty$.

## Connessioni

- Prerequisito: [[Limite di una funzione]], [[Continuità di una funzione]]
- Approssimazione di ordine superiore: [[Polinomi di Taylor]]
- Applicazione: [[Integrale di Riemann]] (TFC inverte la derivata)

## Fonti

- [[Dispense AnalisiI — Galletti]] (§5, pp. 98-134)
