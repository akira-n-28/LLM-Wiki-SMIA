---
tipo: concetto
titolo: Base di uno spazio vettoriale
tag: [algebra-lineare, matematica]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Base di uno spazio vettoriale

Un insieme $\beta = \{v_1, v_2, \ldots, v_n\} \subseteq V$ è una **base** di $V$ se:
1. $V = \mathrm{span}(v_1, \ldots, v_n)$ — $\beta$ è un sistema di generatori per $V$.
2. $v_1, \ldots, v_n$ sono [[Dipendenza lineare|linearmente indipendenti]].

**Equivalenza:** $\beta$ è una base $\Leftrightarrow$ ogni $v \in V$ si scrive in modo **unico** come $v = c_1 v_1 + \cdots + c_n v_n$. L'$n$-upla $(c_1, \ldots, c_n)$ sono le **coordinate** di $v$ in base $\beta$.

## Esempi di basi canoniche

| Spazio $V$ | Base canonica $\beta$ | $\dim V$ |
|---|---|---|
| $\mathbb{R}^n$ | $\{e_1, e_2, \ldots, e_n\}$ (vettori one-hot) | $n$ |
| $M_{m,n}(\mathbb{R})$ | $\{E_{ij}\}$ (matrici elementari) | $m \cdot n$ |
| $\mathbb{R}_t[x]$ | $\{1, x, x^2, \ldots, x^t\}$ | $t+1$ |

## Dimensione

Due basi dello stesso spazio vettoriale finitamente generato hanno la **stessa cardinalità**: questa è la **dimensione** $\dim_K V$.

$$\dim_K V = |\beta| \quad \text{per ogni base } \beta$$

- $\dim_K \{O_V\} = 0$
- $\dim_K \mathbb{R}^n = n$
- $\dim_K M_{m,n}(\mathbb{R}) = m \cdot n$
- $\dim_K \mathbb{R}_t[x] = t+1$

## Teorema del completamento di una base

Sia $\beta = \{v_1, \ldots, v_n\}$ una base di $V$ e sia $\{w_1, \ldots, w_p\}$ (con $p \leq n$) un insieme indipendente. Allora si possono aggiungere $n - p$ vettori da $\beta$ per formare una nuova base di $V$ con $n$ vettori.

**Conseguenze:**
- Un insieme indipendente con $n$ vettori in uno spazio di dimensione $n$ è già una base.
- Un sistema di $n$ generatori in uno spazio di dimensione $n$ è già una base.
- Un insieme con più di $n$ vettori in uno spazio di dimensione $n$ è necessariamente dipendente.

## Isomorfismo delle coordinate

Fissata una base $\beta$ di $V$ con $\dim V = n$, l'applicazione

$$F_\beta : V \to K^n, \quad v \mapsto \begin{pmatrix} c_1 \\ \vdots \\ c_n \end{pmatrix}$$

è un **isomorfismo** di spazi vettoriali. Ogni spazio di dimensione $n$ è isomorfo a $K^n$.

## Cambiamenti di base

Se $\mathcal{B} = (v_1, \ldots, v_n)$ e $\mathcal{B}' = (v'_1, \ldots, v'_n)$ sono due basi ordinate di $V$, esiste un'unica matrice invertibile $B$ (matrice del cambiamento di base) tale che:

$$\mathcal{B}' = \mathcal{B} \cdot B, \qquad x = B \cdot x'$$

dove $x$ e $x'$ sono le coordinate dello stesso vettore nelle due basi. Si calcola con Gauss-Jordan: $[B | B'] \sim [I | B^{-1}B']$.

## Connessioni

- Richiede: [[Dipendenza lineare]], [[Sottospazio generato]]
- Strumento: [[Algoritmo di Gauss-Jordan]]
- Usata in: [[Applicazione lineare]], [[Diagonalizzazione]]
- Discusso in: [[Algebra Lineare]], [[Spazio vettoriale]]

## Fonti

- [[Dispense AlgLin — Galletti]]
