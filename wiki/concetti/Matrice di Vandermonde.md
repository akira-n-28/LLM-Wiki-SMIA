---
tipo: concetto
titolo: Matrice di Vandermonde
tag: [algebra-lineare, ml]
cluster: algebra
fonti: 1
ultima-modifica: 2026-04-30
---

# Matrice di Vandermonde

Matrice del disegno per la [[Regressione polinomiale]]: contiene le potenze crescenti delle osservazioni `u₁, …, uₙ`.

## Definizione

Per un polinomio di grado `p-1`:

$$
X = \begin{bmatrix}
1 & u_1 & u_1^2 & \cdots & u_1^{p-1} \\
1 & u_2 & u_2^2 & \cdots & u_2^{p-1} \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
1 & u_n & u_n^2 & \cdots & u_n^{p-1}
\end{bmatrix} \in \mathbb{R}^{n \times p}
$$

## Proprietà chiave

- **Rango colonna pieno** se i punti `uᵢ` sono distinti e `n ≥ p`. Condizione necessaria perché `X^T X` sia invertibile e la stima [[Minimi quadrati|OLS]] esista univoca:
  $$\hat\beta = (X^T X)^{-1} X^T y.$$
- **Mal condizionata** per `p` grande: i `u^k` con `k` alto e `u ∈ [0,1]` diventano molto correlati ⇒ `X^T X` quasi singolare ⇒ instabilità numerica della stima.

## Connessione con la matrice di Hilbert

In aspettativa, sotto `U ∼ U(0,1)`:

$$
\mathbb{E}\!\left[\frac{1}{n} X^T X\right] = H_p, \quad H_{ij} = \frac{1}{i+j-1}
$$

(la [[Matrice di Hilbert]], notoriamente mal condizionata).

## Collegamenti

- Strumento di: [[Regressione polinomiale]]
- Usato in: [[Minimi quadrati]] (per la soluzione OLS)
- Versione "in aspettativa": [[Matrice di Hilbert]]
- Onomastica: [[Vandermonde, Alexandre]]

## Fonti

- [[Dispense MatML — Galletti]] (esempio 2.3, pp. 14-15)
