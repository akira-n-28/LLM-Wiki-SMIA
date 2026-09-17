---
tipo: concetto
titolo: Distribuzione Beta
tag: [statistica, distribuzioni, bayesiano]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-04-30
---

# Distribuzione Beta

Distribuzione continua su `[0,1]`, naturalmente usata per modellare probabilità o proporzioni.

## Densità

$$
\text{Beta}(m, n):\quad f(\theta) = \frac{\Gamma(m+n)}{\Gamma(m)\Gamma(n)} \theta^{m-1}(1-\theta)^{n-1}, \quad \theta \in [0,1]
$$

Per `m, n` interi, `Γ(k) = (k-1)!`, quindi `Beta(2,2) = 6θ(1-θ)`.

## Momenti

$$
\mathbb{E}[\theta] = \frac{m}{m+n}
$$

$$
\text{Var}(\theta) = \frac{mn}{(m+n)^2 (m+n+1)}
$$

## Casi particolari

- **Beta(1,1)** = uniforme su `[0,1]` (prior non informativo).
- **Beta(2,2)** = densità a campana centrata in `1/2`.

## Uso bayesiano (coniugata della Bernoulli/Binomiale)

Likelihood `Bin(n, k)`: il posterior con prior `Beta(a, b)` resta in famiglia:

$$
\theta\,|\,\tau \sim \text{Beta}(a + k,\; b + n - k)
$$

Esempio (lancio moneta `T,T,C,T,C`, prior `Beta(2,2)`):
- Posterior: `Beta(2+3, 2+2) = Beta(5,4)`, `E[θ|τ] = 5/9 ≈ 0.556`.

Vedi [[Distribuzioni coniugate]] e [[Apprendimento Bayesiano]].

## Collegamenti

- Coniugata di: Bernoulli/Binomiale
- Generalizza: distribuzione uniforme su `[0,1]`
- Esempio applicativo: modello mortalità neonatale (esempio 2.11 dispense)

## Fonti

- [[Dispense MatML — Galletti]] (esempio 2.12, p. 35; tabella coniugate, p. 36)
