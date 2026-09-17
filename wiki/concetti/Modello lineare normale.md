---
tipo: concetto
titolo: Modello lineare normale
tag: [ml, statistica, regressione]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# Modello lineare normale

Modello di regressione in cui la risposta dipende linearmente dai predittori con errore gaussiano:

$$
Y = X\beta + \sigma Z, \quad Z \sim \mathcal{N}(0, I_n)
$$

dove `X ∈ ℝ^{n×p}` è la matrice del modello, `β ∈ ℝ^p` il vettore dei parametri, `σ > 0` la deviazione standard del rumore. Ne consegue:

$$
Y \sim \mathcal{N}(X\beta,\, \sigma^2 I_n)
$$

## Stima con minimi quadrati

Lo stimatore [[Minimi quadrati|OLS]] minimizza la norma dei residui:

$$
\hat\beta_{LS} = \arg\min_{\beta} \|Y - X\beta\|_2^2 = X^\dagger Y = (X^T X)^{-1} X^T Y
$$

## Equivalenza con MLE

La verosimiglianza del modello normale è:

$$
g(Y|\beta, \sigma^2, X) = (2\pi\sigma^2)^{-n/2} \exp\!\left(-\frac{1}{2\sigma^2} \|Y - X\beta\|_2^2\right)
$$

Massimizzare rispetto a `β` equivale a minimizzare `‖Y - Xβ‖²`, quindi:

$$
\hat\beta_{ML} = \hat\beta_{LS}
$$

## Stima della varianza

Sostituendo `β̂` nella log-likelihood e massimizzando rispetto a `σ²`:

$$
\hat\sigma^2_{ML} = \frac{\|Y - X\hat\beta\|_2^2}{n}
$$

**Stimatore distorto**: divide per `n`, non per `n - p` (i gradi di libertà persi per stimare `β`). Lo stimatore non distorto è:

$$
\hat\sigma^2 = \frac{\|Y - X\hat\beta\|_2^2}{n - p}
$$

## Connessione con il [[Modello lineare normale|modello Bayesiano]]

Con prior `g(β|σ²) = N(0, σ² D)` e `g(σ²) ∝ 1/σ²`, la stima [[Stima MAP|MAP]] è:

$$
\bar\beta = \Sigma X^T y, \quad \Sigma = (X^T X + D^{-1})^{-1}
$$

che coincide con la [[Regolarizzazione di Tikhonov|regressione ridge]] quando `D = λI`.

## BIC per il modello lineare normale

Il modello ha `d = p + 1` parametri liberi (`β ∈ ℝ^p` e `σ²`). Il [[BIC]] è:

$$
\mathrm{BIC} = n \log\hat\sigma^2_{ML} + (p+1) \log n
$$

## Proiezione geometrica

`Ŷ = X\hat\beta = PY` con `P = X(X^T X)^{-1}X^T` matrice di proiezione su `span(X)`. Il residuo `Y - Ŷ = (I - P)Y` è ortogonale a `span(X)`.

## Connessioni

Equivale alla [[Regressione polinomiale]] quando le colonne di `X` sono potenze di un regressore scalare.

## Collegamenti

- Stima dei parametri: [[Minimi quadrati]]
- Equivalenza: [[Stima di Massima Verosimiglianza]]
- Stima Bayesiana: [[Apprendimento Bayesiano]], [[Stima MAP]]
- Selezione del modello: [[BIC]], [[Cross-validation]]
- Distribuzione di Y: [[Distribuzione Normale Multivariata]]
- Coincide con: [[Regressione polinomiale]] per feature polinomiali

## Fonti

- [[Dispense MatML — Galletti]] (§2.9, esempio 2.16, pp. 29-30, 42)
