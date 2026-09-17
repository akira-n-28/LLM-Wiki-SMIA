---
tipo: concetto
titolo: Varianza e covarianza
tag: [probabilità, fondamenti]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Varianza e covarianza

## Varianza

La **varianza** di una [[Variabile aleatoria]] `X` con media `µ = E[X]` misura la dispersione dei valori attorno alla media:

$$
\mathrm{Var}(X) = E\!\left[(X - \mu)^2\right] = E[X^2] - E[X]^2
$$

La **deviazione standard** è `σ = √Var(X)`.

## Proprietà della varianza

- `Var(aX + b) = a²·Var(X)` — la traslazione non cambia la varianza
- `Var(X) ≥ 0`, con eguaglianza sse X è costante
- Per X⊥Y: `Var(X + Y) = Var(X) + Var(Y)`
- In generale: `Var(X + Y) = Var(X) + Var(Y) + 2·Cov(X,Y)`

## Varianze notevoli

| Variabile | Var(X) |
|-----------|--------|
| Ber(p) | p(1-p) |
| B(n,p) | np(1-p) |
| Geo(p) | (1-p)/p² |
| Poi(λ) | λ |

## Covarianza

$$
\mathrm{Cov}(X, Y) = E[XY] - E[X]\,E[Y]
$$

Proprietà:
- `Cov(X, X) = Var(X)`
- `Cov(aX, bY) = ab·Cov(X, Y)`
- Se X⊥Y: `Cov(X,Y) = 0` (non vale il viceversa in generale)

## Indice di correlazione

$$
\rho(X,Y) = \frac{\mathrm{Cov}(X,Y)}{\sqrt{\mathrm{Var}(X)\,\mathrm{Var}(Y)}} \in [-1, 1]
$$

`ρ = ±1` sse X = aY + b (relazione lineare perfetta). La [[Disuguaglianza di Cauchy-Schwarz]] garantisce `|ρ| ≤ 1`.

## Connessione con il Bootstrap e le stime

In [[Bootstrap]], `V̂ar(θ̂) = (1/B) Σ_b (θ̂_b* - θ̄*)²` è un'approssimazione campionaria della varianza dello stimatore.

In [[Riduzione della varianza]], il parametro ottimale `α* = Cov(Y,Ỹ)/Var[Ỹ]` minimizza la varianza dello stimatore con variabile di controllo — riducendola del fattore `(1 - ρ²)`.

## Connessione con il Bias-Variance Trade-off

Il [[Bias-Variance trade-off]] decompone `E[(g(x) - y)²]` in termini che includono `Var[g(x)]` — la varianza del predittore al variare del training set.

## Connessione con i corsi

- [[Probabilità e Statistica]]: definizione e proprietà fondamentali.
- [[Matematica per il Machine Learning]]: la [[Varianza campionaria]] è la stima campionaria di Var(X); appare nel bias-variance e nell'ottimismo.

## Persone

Concetto formalizzato da [[Gauss, Carl Friedrich]] nel contesto degli errori di misura; nome "varianza" introdotto da [[Fisher, Ronald]] (1918).

## Collegamenti

- Dipende da: [[Valore atteso]], [[Variabile aleatoria]]
- Usata in: [[Bias-Variance trade-off]], [[Riduzione della varianza]], [[Bootstrap]], [[Disuguaglianza di Chebyshev]]
- Stima campionaria: [[Varianza campionaria]]

## Fonti

- [[Dispense ProbStat — Galletti]] (§3, pp. 27-30)
