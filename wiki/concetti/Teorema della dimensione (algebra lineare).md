---
tipo: concetto
titolo: Teorema della dimensione (algebra lineare)
tag: [algebra-lineare, matematica]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Teorema della dimensione (Rank-Nullity)

Sia $T: V \to W$ una trasformazione lineare con $V$ spazio vettoriale di dimensione finita $n$. Allora:

$$\dim_K V = \dim_K \ker T + \dim_K \mathrm{Im}(T)$$

ovvero, usando le notazioni **nullità** $n(T) = \dim \ker T$ e **rango** $\mathrm{rg}(T) = \dim \mathrm{Im}(T)$:

$$n = n(T) + \mathrm{rg}(T)$$

## Interpretazione

Il teorema dice che le dimensioni dell'informazione "persa" ($\ker T$) e "trasmessa" ($\mathrm{Im}(T)$) sommano alla dimensione del dominio. Non si può "creare" informazione con una trasformazione lineare.

## Versione matriciale

Per $T = L_A$ con $A \in M_{m,n}(\mathbb{R})$ e $T: \mathbb{R}^n \to \mathbb{R}^m$:

$$n = n(A) + \mathrm{rg}(A)$$

- $\mathrm{rg}(A)$ = numero di pivot nella ridotta a scala = numero di variabili vincolate.
- $n(A)$ = numero di variabili libere nel sistema $AX = 0$.
- $\mathrm{Im}(L_A) = \mathrm{span}(\text{colonne di } A)$, dimensione = $\mathrm{rg}(A)$.

## Corollari

- $T$ è iniettiva $\Leftrightarrow n(T) = 0 \Leftrightarrow \mathrm{rg}(T) = n$.
- $T$ è suriettiva $\Leftrightarrow \mathrm{rg}(T) = \dim W = m$.
- $T: V \to V$ con $\dim V = n$ è un isomorfismo $\Leftrightarrow$ iniettiva $\Leftrightarrow$ suriettiva.
- Per $A$ quadrata $n \times n$: $A$ invertibile $\Leftrightarrow \mathrm{rg}(A) = n \Leftrightarrow \ker A = \{0\} \Leftrightarrow \det A \neq 0$.

## Esempio

$T: \mathbb{R}^3 \to \mathbb{R}^3$ con matrice $A = \begin{pmatrix} 1&-1&0\\-2&2&0\\0&0&1 \end{pmatrix}$. Gauss-Jordan dà $\mathrm{rg}(A) = 2$, quindi $n(A) = 3 - 2 = 1$: $\ker A = \mathrm{span}\{[1,1,0]^T\}$, $\mathrm{Im}(A) = \mathrm{span}\{[1,-2,0]^T, [0,0,1]^T\}$.

## Connessioni

- Enunciato in: [[Applicazione lineare]]
- Calcolato con: [[Algoritmo di Gauss-Jordan]]
- Discusso in: [[Algebra Lineare]]

## Fonti

- [[Dispense AlgLin — Galletti]]
