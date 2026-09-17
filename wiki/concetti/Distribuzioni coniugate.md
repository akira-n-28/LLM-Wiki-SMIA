---
tipo: concetto
titolo: Distribuzioni coniugate
tag: [ml, statistica, bayesiano]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# Distribuzioni coniugate

Nel linguaggio [[Apprendimento Bayesiano|Bayesiano]], una distribuzione a priori si dice **coniugata** rispetto a una certa likelihood se, dopo aver applicato il Teorema di Bayes, la **posterior appartiene alla stessa famiglia di distribuzioni** della prior.

Questo garantisce che l'aggiornamento Bayesiano sia analiticamente trattabile: basta aggiornare gli iperparametri.

## Tabella delle coppie principali

| Likelihood | Prior coniugato | Posterior |
|---|---|---|
| Binomiale `Bin(n, k)` | `Beta(a, b)` | `Beta(a+k, b+n-k)` |
| Normale (varianza nota) `N(µ, σ²)` | `N(ν, φ²)` | `N(µ_n, σ²_n)` |
| Poisson `Poi(λ)` | `Gamma(α, β)` | `Gamma(α + Σx_i, β + n)` |
| Normale (precisione) | `Gamma(α, β)` per `1/σ²` | `Inv-Gamma` aggiornata |

## Esempio: Beta–Binomiale

Modello: `X_i |θ ∼ Ber(θ)`, osservazioni binarie. Prior: `θ ∼ Beta(a, b)`.

Likelihood con `s = Σx_i` successi su `n` prove:

$$
g(\tau|\theta) \propto \theta^s (1-\theta)^{n-s}
$$

Posterior:

$$
g(\theta|\tau) \propto \theta^{a+s-1}(1-\theta)^{b+n-s-1} \quad \Rightarrow \quad \theta|\tau \sim \mathrm{Beta}(a+s,\; b+n-s)
$$

La media a posteriori è `(a+s)/(a+b+n)` — interpolazione tra la media del prior `a/(a+b)` e la frequenza empirica `s/n`.

### Caso particolare: prior uniforme

`Beta(1,1)` = Uniforme su `[0,1]`. La posterior è `Beta(1+s, 1+n-s)`. Evita la degenericità dello stimatore ML per dataset sbilanciati (es. `s = 0` → MLE dà `θ̂ = 0` mentre il Bayesiano dà `1/(n+2)`).

## Esempio: Gamma–Poisson

Modello: `X_i |λ ∼ Poisson(λ)`. Prior: `λ ∼ Gamma(a, b)`.

$$
g(\lambda|\tau) \propto \lambda^{a + \sum_i x_i - 1} e^{-(b+n)\lambda} \quad \Rightarrow \quad \lambda|\tau \sim \mathrm{Gamma}(a + \textstyle\sum_i x_i,\; b + n)
$$

Iperparametri aggiornati: `α → α + Σx_i`, `β → β + n`. La media a posteriori è `(a + Σx_i)/(b + n)`.

## Esempio: Normale–Normale

Con likelihood `N(µ, σ²)` (varianza nota) e prior `µ ∼ N(ν, φ²)`:

$$
\mu|\tau \sim \mathcal{N}\!\left(\gamma_n \bar x_n + (1-\gamma_n)\nu,\; \gamma_n \frac{\sigma^2}{n}\right), \quad \gamma_n = \frac{n/\sigma^2}{1/\varphi^2 + n/\sigma^2}
$$

Per `n → ∞`, `γ_n → 1` e la posterior si concentra sulla media campionaria.

## Famiglia esponenziale

Tutte le coppie coniugate (Binomiale–Beta, Poisson–Gamma, Normale–Normale, ecc.) appartengono alla **famiglia esponenziale**. Il prior coniugato è sempre nella stessa famiglia, e l'aggiornamento consiste nel sommare statistiche sufficienti agli iperparametri.

## Quando non esistono coniugati trattabili

Per modelli complessi (es. reti neurali, mixture models), l'aggiornamento Bayesiano esatto è intrattabile. Si ricorre a:
- Approssimazione di Laplace → [[BIC]]
- Metodi MCMC: [[Metropolis-Hastings]], [[Campionamento di Gibbs]]

## Collegamenti

- Framework: [[Apprendimento Bayesiano]]
- Distribuzioni coinvolte: [[Distribuzione Beta]], [[Distribuzione Gamma]], [[Distribuzione Inverse-Gamma]], [[Distribuzione Normale Multivariata]]
- Approssimazione: [[BIC]]
- Alternativa numerica: [[Metropolis-Hastings]], [[Campionamento di Gibbs]]

## Fonti

- [[Dispense MatML — Galletti]] (§2.10, definizione 2.8, esempi 2.11-2.14, pp. 34-40)
