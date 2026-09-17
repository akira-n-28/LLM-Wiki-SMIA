---
tipo: concetto
titolo: Distribuzione chi-quadro
tag: [statistica, distribuzioni]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-04-30
---

# Distribuzione chi-quadro (χ²)

Distribuzione della somma dei quadrati di variabili normali standard indipendenti.

## Definizione

Se `Z₁, …, Zₙ ∼ i.i.d. N(0,1)`:

$$
\sum_{i=1}^{n} Z_i^2 \sim \chi^2_n
$$

Equivalentemente: per `X ∼ N(μ, Σ)` con `det(Σ) > 0`:

$$
(X-\mu)^T \Sigma^{-1} (X-\mu) \sim \chi^2_n
$$

(forma quadratica gaussiana, dimostrata via decomposizione `Σ = BB^T` e MGF).

## Funzione generatrice dei momenti

$$
M_{\chi^2_n}(s) = (1 - 2s)^{-n/2}, \quad s < 1/2
$$

Equivalente alla [[Distribuzione Gamma]] con `α = n/2`, `λ = 1/2`.

## Caso non centrale

Se `Xᵢ ∼ N(μᵢ, 1)` indipendenti, `||X||² ∼ χ²_n(θ)` con parametro di non centralità `θ = ||μ||²`.

## Usi

- [[Varianza campionaria]] gaussiana: `(n-1)s²/σ² ∼ χ²_{n-1}`.
- Costruzione della [[Distribuzione t-Student]] e della [[Distribuzione F di Fisher-Snedecor]].
- Test di adattamento (chi-quadro test).
- Posterior marginale per `1/σ²` nel modello normale Bayesiano con prior improprio.

## Collegamenti

- Caso particolare di: [[Distribuzione Gamma]]
- Componente di: [[Distribuzione t-Student]], [[Distribuzione F di Fisher-Snedecor]]
- Connesso a: [[Distribuzione Normale Multivariata]] (forma quadratica)

## Fonti

- [[Dispense MatML — Galletti]] (def. 1.8 p. 6; teor. 2.4 e dim. p. 28)
