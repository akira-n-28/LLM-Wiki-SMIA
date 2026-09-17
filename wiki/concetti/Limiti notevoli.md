---
tipo: concetto
titolo: Limiti notevoli
tag: [analisi, matematica, analisi-1]
cluster: analisi
fonti: 1
ultima-modifica: 2026-05-06
---

# Limiti notevoli e o-piccoli

## Limiti notevoli principali

| Limite | Valore |
|---|---|
| $\lim_{x\to 0}\frac{\sin x}{x}$ | $1$ |
| $\lim_{x\to 0}\frac{1-\cos x}{x^2}$ | $\frac{1}{2}$ |
| $\lim_{x\to 0}\frac{\tan x}{x}$ | $1$ |
| $\lim_{x\to 0}\frac{e^x-1}{x}$ | $1$ |
| $\lim_{x\to 0}\frac{\ln(1+x)}{x}$ | $1$ |
| $\lim_{x\to+\infty}\left(1+\frac{1}{x}\right)^x$ | $e$ |

**Dimostrazione** $\sin x/x \to 1$: tramite teorema dei due carabinieri con $\sin x \leq x \leq \tan x$ per $x\in(0,\pi/2)$.

**Dimostrazione** $(1+1/x)^x \to e$: via Binomio di Newton si mostra che $a_n=(1+1/n)^n$ è crescente e limitata $(\leq 3)$; il limite si chiama $e\approx 2.718$.

## O-piccoli

$f(x)=o(g(x))$ per $x\to x_0$ significa $\lim_{x\to x_0}\frac{f(x)}{g(x)}=0$.

**Proprietà chiave:**
1. $o(g)+o(g)=o(g)$
2. $c\cdot o(g)=o(g)$ per $c\neq 0$
3. $o(g_1)\cdot o(g_2)=o(g_1 g_2)$
4. $o(g+o(g))=o(g)$
5. $|o(g)|^\lambda=o(|g|^\lambda)$

**Relazione con limiti:** $\lim\frac{f}{g}=l \Leftrightarrow f=lg+o(g)$.

## Espansioni asintotiche (per $x\to 0$)

$$e^x = 1+x+\frac{x^2}{2}+o(x^2)$$
$$\sin x = x - \frac{x^3}{6}+o(x^3)$$
$$\cos x = 1-\frac{x^2}{2}+o(x^2)$$
$$\ln(1+x) = x-\frac{x^2}{2}+o(x^2)$$
$$(1+x)^\alpha = 1+\alpha x + o(x)$$

**Cambio di variabile nelle approssimazioni.** Se $g(y)=g_1(y)+o(g_1(y))$ per $y\to y_0$ e $f(x)\to y_0$, allora $g(f(x))=g_1(f(x))+o(g_1(f(x)))$.

**Tecnica di calcolo.** Sostituire ciascuna funzione con la sua espansione di ordine appropriato, semplificare numeratore/denominatore con gli o-piccoli.

## Gerarchia degli infiniti (per $x\to+\infty$)

$$\log_a x = o(x^\alpha),\quad x^\alpha = o(a^x),\quad a^x = o(x!) \quad \forall\alpha>0,\ a>1$$

## Connessioni

- Definizione: [[Limite di una funzione]]
- Applicazione sistematica: [[Polinomi di Taylor]] (espansioni di ordine superiore)

## Fonti

- [[Dispense AnalisiI — Galletti]] (§2, pp. 39-59)
