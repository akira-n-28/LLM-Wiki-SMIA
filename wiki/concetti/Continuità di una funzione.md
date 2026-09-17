---
tipo: concetto
titolo: Continuità di una funzione
tag: [analisi, matematica, analisi-1]
cluster: analisi
fonti: 1
ultima-modifica: 2026-05-06
---

# Continuità di una funzione

## Definizione

$f:A\subset\mathbb{R}\to\mathbb{R}$ è **continua in $x_0\in A$** se:
$$\forall V \text{ intorno di } f(x_0)\ \exists U \text{ intorno di } x_0:\ f(x)\in V\ \forall x\in A\cap U$$

**Definizione ε-δ equivalente:**
$$\forall\varepsilon>0\ \exists\delta>0:\ |f(x)-f(x_0)|<\varepsilon\ \forall x\in A,\ |x-x_0|<\delta$$

Se $x_0$ è punto di accumulazione, la continuità equivale a $\lim_{x\to x_0}f(x)=f(x_0)$.

**Operazioni.** Somma, prodotto, quoziente ($g\neq 0$), composizione di funzioni continue sono continue. Le funzioni elementari ($\sin, \cos, \ln, e^x, x^\alpha, \ldots$) sono continue sui loro domini naturali.

## Teorema di Weierstrass

**Enunciato.** Se $f:[a,b]\to\mathbb{R}$ è continua, allora $f$ raggiunge il suo massimo e il suo minimo su $[a,b]$:
$$\exists x_m, x_M\in[a,b]:\ f(x_m)=\min_{[a,b]}f,\quad f(x_M)=\max_{[a,b]}f$$

**Dimostrazione (idea).** Si costruisce una successione minimizzante $\{x_n\}\subset[a,b]$ con $f(x_n)\to\inf_{[a,b]}f$. Per Bolzano-Weierstrass esiste una sottosuccessione convergente $x_{n_k}\to x_m\in[a,b]$. Per continuità $f(x_{n_k})\to f(x_m)$, quindi $f(x_m)=\inf f$.

**Corollario.** $f$ continua su $[a,b]$ è **limitata**: $\exists M\geq 0:\ |f(x)|\leq M\ \forall x\in[a,b]$.

## Teorema dei valori intermedi (Bolzano)

**Enunciato.** Se $f:[a,b]\to\mathbb{R}$ è continua con $f(a)f(b)<0$, allora $\exists\xi\in(a,b):\ f(\xi)=0$.

**Dimostrazione.** Per bisezione iterata: si costruisce $I_n=[x_n,y_n]$ con $f(x_n)<0<f(y_n)$ e $|I_n|=(b-a)/2^n\to 0$. Le successioni $(x_n)$ e $(y_n)$ convergono allo stesso $\xi$; per continuità $f(\xi)=\lim f(x_n)\leq 0$ e $f(\xi)=\lim f(y_n)\geq 0$, quindi $f(\xi)=0$.

**Corollario.** $f$ continua su $[a,b]$ assume tutti i valori tra $\min f$ e $\max f$ (teorema di Darboux / dei valori intermedi generalizzato).

## Continuità uniforme

$f:A\to\mathbb{R}$ è **uniformemente continua** se il $\delta$ non dipende da $x_0$:
$$\forall\varepsilon>0\ \exists\delta>0:\ |f(x)-f(y)|<\varepsilon\ \forall x,y\in A,\ |x-y|<\delta$$

*Fatto:* $f$ continua su $[a,b]$ è automaticamente uniformemente continua (teorema di Heine-Cantor).

## Connessioni

- Prerequisito: [[Limite di una funzione]], [[Successioni]] (via Bolzano-Weierstrass)
- Applicazione nei teoremi: [[Derivata]] (continuità ≠ derivabilità), [[Integrale di Riemann]] (Riemann integrabilità)
- Teorema di Weierstrass arricchito: [[Ottimizzazione]] (esistenza del minimo su compatti)

## Fonti

- [[Dispense AnalisiI — Galletti]] (§4, pp. 88-97)
