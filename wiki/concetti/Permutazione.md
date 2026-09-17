---
tipo: concetto
titolo: Permutazione
tag: [algebra, matematica, combinatoria]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Permutazione

## Calcolo combinatorio

Una **permutazione** di $n$ oggetti distinti è un ordinamento di tutti gli $n$ oggetti. Il numero di permutazioni di $n$ oggetti è $n!$.

| Oggetto | Formula |
|---|---|
| Permutazioni di $n$ | $n!$ |
| Disposizioni di $k$ su $n$ | $\frac{n!}{(n-k)!}$ |
| Combinazioni $\binom{n}{k}$ | $\frac{n!}{k!(n-k)!}$ |

## Permutazione come funzione biettiva

Formalmente, una permutazione di $[n] = \{1, \ldots, n\}$ è una biiezione $\sigma: [n] \to [n]$. Si scrive in **notazione a due righe**:

$$\sigma = \begin{pmatrix} 1 & 2 & \cdots & n \\ \sigma(1) & \sigma(2) & \cdots & \sigma(n) \end{pmatrix}$$

Il gruppo $S_n$ di tutte le permutazioni ha ordine $|S_n| = n!$.

## Notazione ciclica

Un **ciclo** $(a_1\, a_2 \cdots a_r)$ manda $a_1 \to a_2 \to \cdots \to a_r \to a_1$ e lascia fissi gli altri. Ogni permutazione si scrive univocamente come prodotto di **cicli disgiunti**:

$$\sigma = C_1 \cdot C_2 \cdots C_k$$

I cicli disgiunti commutano tra loro. Il **periodo** (ordine) di $\sigma$ è:

$$O(\sigma) = \text{mcm}(|C_1|, |C_2|, \ldots, |C_k|)$$

## Parità

Ogni permutazione si scrive come prodotto di **trasposizioni** (scambi di 2 elementi). Il numero di trasposizioni usato ha parità fissa (teorema): $\sigma$ è **pari** se ne usa un numero pari, **dispari** altrimenti.

$$\epsilon(\sigma) = (-1)^{\text{parità di }\sigma} \in \{+1, -1\}$$

- Un $r$-ciclo usa $r - 1$ trasposizioni (pari $\Leftrightarrow$ $r$ dispari)
- Parità di $\sigma\tau$ = somma delle parità

## Struttura ciclica e classi di coniugio

La **struttura ciclica** di $\sigma$ è la lista ordinata delle lunghezze dei suoi cicli. Due permutazioni sono [[Classi di coniugio|coniugate]] in $S_n$ $\Leftrightarrow$ hanno la stessa struttura ciclica $\Leftrightarrow$ corrispondono alla stessa **partizione di $n$**.

## Connessioni

- Struttura di gruppo: [[Gruppo simmetrico]]
- Classi di equivalenza per coniugio: [[Classi di coniugio]]
- Prerequisito di: [[Teorema di Lagrange]]
- Si collega a: [[Teorema Binomiale]]
- Discusso in: [[Strutture Algebriche]]

## Fonti

- [[Dispense StrAlg — Galletti]] (§2.1, §3.2-3.3, pp. 75-106)
