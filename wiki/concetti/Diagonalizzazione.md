---
tipo: concetto
titolo: Diagonalizzazione
tag: [algebra-lineare, matematica]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Diagonalizzazione

Un endomorfismo $T: V \to V$ (o la sua matrice $A$) è **diagonalizzabile** su $K$ se esiste una base $\mathcal{F} = (f_1, \ldots, f_n)$ di **autovettori** tale che la matrice di $T$ in $\mathcal{F}$ è diagonale:

$$D = \begin{pmatrix} \lambda_1 & & \\ & \ddots & \\ & & \lambda_n \end{pmatrix}$$

Equivalentemente: $D = B^{-1} A B$, dove $B = [f_1 | \cdots | f_n]$ è la matrice degli autovettori (matrice del cambio di base dalla base canonica a $\mathcal{F}$).

## Matrici simili

$A, A' \in M_n(K)$ sono **simili** se esiste $B$ invertibile tale che $A' = B^{-1} A B$. La similitudine è una relazione di equivalenza; matrici simili:
- Hanno lo stesso [[Polinomio caratteristico]].
- Hanno gli stessi autovalori.
- Rappresentano lo stesso endomorfismo in basi diverse.

## Autospazi

L'**autospazio** relativo a $\lambda_0$ è:

$$V_{\lambda_0} = \ker(A - \lambda_0 I) = \{X \in K^n : AX = \lambda_0 X\} \leq K^n$$

Si calcola risolvendo il sistema lineare omogeneo $(A - \lambda_0 I)X = 0$ con Gauss-Jordan.

## Teorema di diagonalizzabilità

$T$ è diagonalizzabile su $K$ se e solo se tutte le seguenti condizioni valgono simultaneamente:

1. $p_T(\lambda)$ si fattorizza completamente in fattori lineari su $K$ (tutti gli autovalori sono in $K$).
2. Per ogni $\lambda_0 \in \mathrm{Spec}(T)$: $m_g(\lambda_0) = m_a(\lambda_0)$.
3. $\sum_{\lambda_0 \in \mathrm{Spec}(T)} m_g(\lambda_0) = n$ (le molteplicità geometriche sommano a $n$).

**Corollario:** se $T$ ha $n$ autovalori distinti, è automaticamente diagonalizzabile.

## Algoritmo di diagonalizzazione

1. Calcola $p_T(\lambda) = \det(A - \lambda I)$.
2. Trova le radici $\lambda_1, \ldots, \lambda_k \in K$.
3. Per ciascun $\lambda_i$, calcola $V_{\lambda_i} = \ker(A - \lambda_i I)$ con Gauss-Jordan; verifica $m_g(\lambda_i) = m_a(\lambda_i)$.
4. Se la condizione è soddisfatta, unisci le basi degli autospazi: $B = [f_1 | \cdots | f_n]$.
5. Verifica: $B^{-1} A B = D$.

## Esempio

$A = \begin{pmatrix} 3&1&1\\2&4&2\\3&3&5 \end{pmatrix}$: $p_A(\lambda) = (\lambda-2)^2(\lambda-8)$. $m_a(2) = 2$, $m_a(8) = 1$. Gauss-Jordan su $A - 2I$ dà $m_g(2) = 2$: base $\{[-1,1,0]^T, [-1,0,1]^T\}$. Su $A - 8I$: $m_g(8) = 1$: base $\{[1,2,3]^T\}$. Somma $2+1=3=n$ → $A$ è diagonalizzabile.

## Non diagonalizzabilità

$A = \begin{pmatrix} 0&1\\-1&0 \end{pmatrix}$: $p_A(\lambda) = \lambda^2+1$, senza radici reali → $A$ non è diagonalizzabile su $\mathbb{R}$. In questo caso si usa la **forma di Jordan** (forma canonica alternativa).

## Connessioni

- Richiede: [[Autovalori e autovettori]], [[Polinomio caratteristico]], [[Applicazione lineare]]
- Strumento: [[Algoritmo di Gauss-Jordan]]
- Versione numerica: [[Algoritmo QR per autovalori]]
- Discusso in: [[Algebra Lineare]], [[Machine Learning]] *(PCA)*

## Fonti

- [[Dispense AlgLin — Galletti]]
