---
tipo: concetto
titolo: Distribuzione Gamma
tag: [statistica, distribuzioni]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-04-30
---

# Distribuzione Gamma

Famiglia di distribuzioni continue su `R⁺` con due parametri `α > 0` (forma) e `λ > 0` (rate).

## Densità

$$
f(x) = \frac{\lambda^\alpha\, x^{\alpha-1}\, e^{-\lambda x}}{\Gamma(\alpha)}, \quad x \in \mathbb{R}^+
$$

## Funzione generatrice dei momenti

$$
M_X(s) = \left(\frac{\lambda}{\lambda - s}\right)^\alpha, \quad s < \lambda
$$

Si ricava integrando `e^{sx} f(x)` e riconoscendo la densità di una Gamma con rate `λ-s` (dimostrazione classica: integrale di una densità = 1).

## Casi particolari

- **Esponenziale**: `α = 1` ⇒ `f(x) = λ e^{-λx}`.
- **Chi-quadro**: `α = n/2`, `λ = 1/2` ⇒ `χ²_n`. Vedi [[Distribuzione chi-quadro]].

## Usi nel framework Bayesiano

- **Coniugata** della Poisson: `λ ~ Gamma(α, β)`, posterior `Gamma(α + Σxᵢ, β + n)`.
- **Coniugata** della precisione gaussiana: `1/σ² ~ Gamma(α, β)`. Da cui `σ² ∼` [[Distribuzione Inverse-Gamma]] `(α, β)`.

Vedi [[Distribuzioni coniugate]] e [[Apprendimento Bayesiano]].

## Collegamenti

- Generalizza: esponenziale
- Caso particolare: [[Distribuzione chi-quadro]]
- Trasformata in: [[Distribuzione Inverse-Gamma]] (per `1/X`)
- Coniugata in: [[Distribuzioni coniugate]]

## Fonti

- [[Dispense MatML — Galletti]] (def. 2.5, p. 27; uso bayesiano pp. 30-39)
