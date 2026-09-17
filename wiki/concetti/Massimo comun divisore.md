---
tipo: concetto
titolo: Massimo comun divisore
tag: [algebra, matematica, aritmetica]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Massimo comun divisore

Dati $a, b \in \mathbb{Z}$ non entrambi nulli, un intero $d \in \mathbb{Z}$ è il loro **massimo comun divisore** se:
1. $d | a$ e $d | b$ (è divisore comune)
2. Se $d' | a$ e $d' | b$, allora $d' | d$ ($d$ è il massimo nell'ordine della divisibilità)

Si denota $\text{MCD}(a, b)$ o $(a, b)$. Per convenzione si prende $d > 0$.

## Identità di Bézout

**Teorema.** Per ogni $a, b \in \mathbb{Z}$ non entrambi nulli esiste $d = \text{MCD}(a, b)$ e si scrive come combinazione lineare:

$$\exists s, t \in \mathbb{Z}: d = s \cdot a + t \cdot b$$

I coefficienti $s, t$ non sono unici. Si trovano con l'[[Algoritmo di Euclide]] esteso.

**Dimostrazione (principio del buon ordinamento):** $S = \{xa + yb \mid x,y \in \mathbb{Z}, xa+yb > 0\}$ è non vuoto; il suo minimo $d$ è il MCD.

## Proprietà

- $\text{MCD}(a,b) = \text{MCD}(|a|,|b|)$
- $\text{MCD}(0, a) = |a|$
- $\text{MCD}(a,b) = \text{MCD}(b, r)$ dove $r$ è il resto di $a$ diviso $b$ (base dell'[[Algoritmo di Euclide]])
- $a$ e $b$ sono **coprimi** se $\text{MCD}(a,b) = 1$, equivalente a $\exists s,t: sa + tb = 1$

## Conseguenze dell'identità di Bézout

1. $a$ e $b$ coprimi $\Leftrightarrow 1 = ah + bk$ per qualche $h, k \in \mathbb{Z}$
2. Se $a, b$ coprimi e $a | c$ e $b | c$, allora $a \cdot b | c$
3. Se $a$ è irriducibile, allora $a$ è primo: $a | bc \Rightarrow a|b \lor a|c$

## Equazioni diofantine

$ax + by = c$ (con $a, b, c \in \mathbb{Z}$) ammette soluzioni intere $\Leftrightarrow \text{MCD}(a, b) \mid c$.

Se $d = \text{MCD}(a,b)$ e $d | c$: sia $d = ah + bk$ (Bézout), allora $(x_0, y_0) = (hq, kq)$ con $c = dq$ è una soluzione.

**Esempio:** $12x + 18y = 48$, $\text{MCD}(12,18) = 6$ e $6 | 48$ ✓; soluzione $(-8, 8)$.

## Teorema fondamentale dell'aritmetica

Ogni $n \geq 2$ si fattorizza in modo unico (a meno dell'ordine) come prodotto di irriducibili: $n = p_1^{r_1} \cdots p_k^{r_k}$.

Dimostrazione per induzione: esistenza + unicità (usando che irriducibile $\Leftrightarrow$ primo in $\mathbb{Z}$).

## Connessioni

- Calcolo: [[Algoritmo di Euclide]]
- Applicazione: [[Aritmetica modulare]] (invertibilità $a$ in $\mathbb{Z}_n$ $\Leftrightarrow$ $\text{MCD}(a,n) = 1$)
- Teorema di Eulero-Fermat: [[Teorema di Lagrange]]
- Discusso in: [[Strutture Algebriche]]

## Fonti

- [[Dispense StrAlg — Galletti]] (§1.7, pp. 45-57)
