---
tipo: concetto
titolo: Distribuzione di Poisson
tag: [probabilità, distribuzioni]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Distribuzione di Poisson

La [[Variabile aleatoria]] `X ∼ Poi(λ)` con `λ > 0` conta eventi **rari e indipendenti** in un intervallo di tempo o spazio:

$$
P(X = k) = \frac{e^{-\lambda}\,\lambda^k}{k!}, \quad k = 0, 1, 2, \ldots
$$

## Momenti

$$
E[X] = \lambda, \qquad \mathrm{Var}(X) = \lambda
$$

Proprietà rara: media = varianza. Segno distintivo della distribuzione.

## Come limite della Binomiale

Se `X ∼ B(n, p)` con `n → ∞`, `p → 0`, `np → λ`, allora `X →^d Poi(λ)`:

$$
\binom{n}{k} p^k(1-p)^{n-k} \xrightarrow{n\to\infty,\,np=\lambda} \frac{e^{-\lambda}\lambda^k}{k!}
$$

## Proprietà di additività

Se `X ∼ Poi(λ₁)` e `Y ∼ Poi(λ₂)` indipendenti, allora `X + Y ∼ Poi(λ₁ + λ₂)`.

## Processo di Poisson

Se gli arrivi in un intervallo `[0,t]` seguono un processo di Poisson a tasso `λ`, il numero di arrivi in `[0,t]` è `Poi(λt)` e i tempi tra arrivi successivi sono i.i.d. `Exp(λ)`.

## Connessione con le distribuzioni coniugate

In [[Distribuzioni coniugate]], il prior Gamma-Poisson aggiorna: se `X | λ ∼ Poi(λ)` e `λ ∼ Gamma(α,β)`, la posterior è `Gamma(α + Σxᵢ, β + n)`.

## Connessione con i corsi

- [[Probabilità e Statistica]]: §7, con derivazione come limite della Binomiale.
- [[Matematica per il Machine Learning]]: caso di distribuzione coniugata Gamma-Poisson.
- [[Modelli Matematici per la Fisica I]]: processo di Poisson in modelli fisici.

## Persone

[[Poisson, Siméon Denis]] (1837), *Recherches sur la probabilité des jugements*.

## Fonti

- [[Dispense ProbStat — Galletti]] (§7, pp. 41-43)
