---
tipo: concetto
titolo: Matrice di Hilbert
tag: [algebra-lineare, ml]
cluster: algebra
fonti: 1
ultima-modifica: 2026-04-30
---

# Matrice di Hilbert

Matrice quadrata `p × p` con elementi:

$$
H_{ij} = \frac{1}{i + j - 1}
$$

Esempio per `p = 4`:

$$
H_4 = \begin{bmatrix}
1 & 1/2 & 1/3 & 1/4 \\
1/2 & 1/3 & 1/4 & 1/5 \\
1/3 & 1/4 & 1/5 & 1/6 \\
1/4 & 1/5 & 1/6 & 1/7
\end{bmatrix}
$$

## Origine "polinomiale"

Si ottiene integrando il prodotto esterno del vettore di feature polinomiali su `[0,1]`:

$$
H_p = \int_0^1 \begin{bmatrix} 1 \\ u \\ \vdots \\ u^{p-1} \end{bmatrix} [1, u, \dots, u^{p-1}]\, du
$$

L'elemento `(i,j)` è `∫₀¹ u^{i+j-2} du = 1/(i+j-1)`.

## Uso nel framework MatML

Compare nella decomposizione esatta del rischio per la [[Regressione polinomiale]] sotto `U ∼ U(0,1)`. Il sistema delle equazioni normali in aspettativa è:

$$
H_p \beta = \tilde H \beta^*
$$

dove `H̃` è il blocco rettangolare `p × 4` (4 = grado della ground truth + 1).

## Mal condizionamento

`H_p` è celebre per il suo **numero di condizione esponenzialmente grande** (cresce circa come `(1+√2)^{4p}/√p`). Conseguenze:
- Instabilità numerica nella risoluzione di `H_p β = ...`.
- Spiega perché in pratica si usano basi polinomiali ortogonali (Legendre, Chebyshev) anziché le potenze nude.

## Collegamenti

- Strumento di: [[Regressione polinomiale]], [[Errore di approssimazione e di stima]]
- Onomastica: [[Hilbert, David]]
- Connessa a: [[Matrice di Vandermonde]] (versione "campionaria" finita)

## Fonti

- [[Dispense MatML — Galletti]] (esempio 2.6, pp. 19-20)
