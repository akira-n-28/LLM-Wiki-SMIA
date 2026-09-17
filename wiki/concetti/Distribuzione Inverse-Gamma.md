---
tipo: concetto
titolo: Distribuzione Inverse-Gamma
tag: [statistica, distribuzioni, bayesiano]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-04-30
---

# Distribuzione Inverse-Gamma

Distribuzione di `Z = 1/X` quando `X ∼ Gamma(α, β)`. È la distribuzione **coniugata della varianza** `σ²` nel modello gaussiano (perché `1/σ² ∼ Gamma`).

## Densità

Applicando il teorema di cambio di variabile (`x = 1/z`, `|dx/dz| = 1/z²`):

$$
f_Z(z) = \frac{\beta^\alpha}{\Gamma(\alpha)}\, z^{-(\alpha+1)}\, e^{-\beta/z} \propto \frac{e^{-\beta/z}}{z^{\alpha+1}}, \quad z > 0
$$

## Momenti

$$
\mathbb{E}[Z] = \frac{\beta}{\alpha - 1}, \quad \alpha > 1
$$

$$
\text{Var}(Z) = \frac{\beta^2}{(\alpha-1)^2(\alpha-2)}, \quad \alpha > 2
$$

## Uso bayesiano

Nel modello gaussiano `xᵢ ∼ N(μ, σ²)` con prior `1/σ² ∼ Gamma(α, β)`, il posterior per `σ²` resta una Inverse-Gamma. Caso del modello con prior improprio per `μ`:

$$
\frac{1}{\sigma^2}\Big|\,\tau \sim \text{Gamma}\!\left(\alpha + \frac{n-1}{2},\; \beta + \frac{n S_n^2}{2}\right)
$$

Per `n → ∞`, `E[σ²] → S²_n` (converge alla [[Varianza campionaria]] classica).

## Collegamenti

- Trasformata di: [[Distribuzione Gamma]]
- Coniugata in: [[Distribuzioni coniugate]] (modello normale)
- Compare in: [[Campionamento di Gibbs]] (Gibbs sampling per `σ²` nel modello normale Bayesiano)

## Fonti

- [[Dispense MatML — Galletti]] (oss. 2.14, p. 37; ricavata pp. 36-39)
