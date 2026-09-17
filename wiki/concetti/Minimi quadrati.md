---
tipo: concetto
titolo: Minimi quadrati
tag: [ml, regressione, ottimizzazione]
cluster: ml
fonti: 1
ultima-modifica: 2026-04-30
---

# Minimi quadrati (OLS — Ordinary Least Squares)

Metodo di stima che minimizza la somma dei quadrati dei residui:

$$
\hat\beta = \arg\min_{\beta \in \mathbb{R}^p} \|y - X\beta\|_2^2
$$

## Soluzione in forma chiusa

Se `X` ha **rango colonna pieno** (necessariamente `n ≥ p`):

$$
\hat\beta = (X^T X)^{-1} X^T y = X^\dagger y
$$

dove `X† = (X^T X)^{-1} X^T` è la **pseudoinversa di Moore-Penrose**.

## Interpretazione geometrica

`X β̂ = P y`, con `P = X X†` matrice di proiezione ortogonale sul `span(X)`. Si vuole il vettore in `span(X)` più vicino a `y`.

Proprietà di `P`:
- Idempotente: `P² = P`.
- Simmetrica: `P^T = P`.
- `P X = X` (proiettare le colonne di `X` su sé stesse le lascia invariate).

## Equazioni normali

Da `P X = X` e `P^T = P`, manipolando `X β̂ = P y`:

$$
X^T X \hat\beta = X^T y
$$

## Equivalenza con MLE gaussiano

Per il [[Modello lineare normale]] `Y = Xβ + σZ`, `Z ∼ N(0, Iₙ)`, la stima di [[Stima di Massima Verosimiglianza|massima verosimiglianza]] coincide con OLS:

$$
\hat\beta_{ML} = \hat\beta_{LS}
$$

## Calcolo dell'ottimismo (caso lineare)

Per OLS con `p` parametri e `n` osservazioni, l'[[Ottimismo]] atteso è:

$$
\mathbb{E}[\text{OP}] = \frac{2 \ell^* p}{n}
$$

(sfrutta `Tr(X X†) = Tr(X† X) = p`).

## Collegamenti

- Soluzione di: [[Regressione polinomiale]], [[Modello lineare normale]]
- Coincide con: MLE gaussiano (vedi [[Stima di Massima Verosimiglianza]])
- Strumento: [[Matrice di Vandermonde]]

## Fonti

- [[Dispense MatML — Galletti]] (esempi 2.2-2.3, pp. 14-15; ottimismo p. 23)
