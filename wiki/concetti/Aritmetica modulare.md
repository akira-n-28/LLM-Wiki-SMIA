---
tipo: concetto
titolo: Aritmetica modulare
tag: [algebra, matematica, aritmetica]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Aritmetica modulare

Fissato $n \geq 2$, la **congruenza modulo $n$** su $\mathbb{Z}$ è la [[Relazione di equivalenza]]:

$$a \equiv b \pmod{n} \;\Leftrightarrow\; n \mid (a - b)$$

Equivalentemente: $a$ e $b$ hanno lo stesso resto nella divisione per $n$.

## Insieme $\mathbb{Z}_n$

L'insieme quoziente $\mathbb{Z}/{\equiv_n}$ ha $n$ classi con rappresentanti canonici:

$$\mathbb{Z}_n = \{[0]_n, [1]_n, \ldots, [n-1]_n\}$$

**Operazioni** (ben definite, indipendenti dal rappresentante):
- Somma: $[x]_n + [y]_n = [x+y]_n$
- Prodotto: $[x]_n \cdot [y]_n = [xy]_n$

$(\mathbb{Z}_n, +)$ è un [[Gruppo (struttura algebrica)|gruppo abeliano]] per ogni $n \geq 2$.

## Invertibilità

$[a]_n$ è invertibile rispetto al prodotto $\Leftrightarrow \text{MCD}(a, n) = 1$.

**Dimostrazione** $(\Rightarrow)$: se $ab \equiv 1 \pmod{n}$ allora $ab - 1 = nq$, cioè $1 = ab + n(-q)$, quindi MCD$(a,n) = 1$.  
**Dimostrazione** $(\Leftarrow)$: dall'identità di Bézout $1 = sa + tn$, si ha $sa \equiv 1 \pmod{n}$, cioè $s = a^{-1}$.

**Calcolo:** usare l'[[Algoritmo di Euclide]] esteso.

**Gruppo degli invertibili:**
$$U(\mathbb{Z}_n) = \{[a]_n \mid \text{MCD}(a,n) = 1\}$$

Esempio: $U(\mathbb{Z}_6) = \{[1], [5]\}$; $U(\mathbb{Z}_5) = \{[1],[2],[3],[4]\}$ (tutti tranne $[0]$, poiché 5 è primo).

## Funzione di Eulero

$\varphi(n) = |U(\mathbb{Z}_n)|$ = numero di interi in $\{1, \ldots, n\}$ coprimi con $n$.

**Teorema di Eulero-Fermat** (corollario del [[Teorema di Lagrange]]): se $\text{MCD}(a, n) = 1$:
$$a^{\varphi(n)} \equiv 1 \pmod{n}$$

## $\mathbb{Z}_p$ è un campo

Se $p$ è primo, ogni elemento non nullo di $\mathbb{Z}_p$ è invertibile (poiché $\text{MCD}(a, p) = 1$ per $1 \leq a < p$). Quindi $(\mathbb{Z}_p, +, \cdot)$ è un [[Anello e campo|campo]].

## Connessioni

- Prerequisiti: [[Massimo comun divisore]], [[Algoritmo di Euclide]], [[Relazione di equivalenza]]
- Struttura di gruppo: [[Gruppo (struttura algebrica)]]
- Come campo: [[Anello e campo]]
- Applicazione crittografica: [[Strutture Algebriche]]
- Discusso in: [[Strutture Algebriche]]

## Fonti

- [[Dispense StrAlg — Galletti]] (§1.8, pp. 58-72)
