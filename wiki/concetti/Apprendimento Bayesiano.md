---
tipo: concetto
titolo: Apprendimento Bayesiano
tag: [ml, statistica, bayesiano]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# Apprendimento Bayesiano

Paradigma in cui i parametri `θ` non sono valori fissi da stimare, ma **variabili aleatorie** a cui si associa una densità di probabilità. L'apprendimento consiste nell'aggiornare questa densità alla luce dei dati.

## Framework

Dato un training set `τ = {x_1, …, x_n}` (caso non supervisionato), si definiscono:

- **Prior** `g(θ)` — conoscenza sui parametri prima di vedere i dati.
- **Likelihood** `g(τ|θ) = Π_i g(x_i|θ)` — probabilità di osservare `τ` dato `θ` (i.i.d.).
- **Posterior** (Teorema di Bayes):

$$
g(\theta|\tau) = \frac{g(\tau|\theta)\, g(\theta)}{g(\tau)} \propto g(\tau|\theta)\, g(\theta)
$$

dove `g(τ) = ∫ g(τ|θ) g(θ) dθ` è l'**evidenza** (marginal likelihood).

## Densità predittive

- **Predittiva a priori** (prima di vedere `τ`):
  $$g(x) = \int g(x|\theta)\, g(\theta)\,d\theta$$

- **Predittiva a posteriori** (stimatore Bayesiano effettivo):
  $$g_\tau(x) = \int g(x|\theta)\, g(\theta|\tau)\,d\theta$$

## Aggiornamento iterativo e convergenza a MLE

Partendo da `w_0(θ)`, l'aggiornamento bayesiano iterato `w_t(θ) ∝ w_{t-1}(θ) g(τ|θ)` produce un'evidenza strettamente crescente (per [[Disuguaglianza di Jensen]]):

$$
L_t := \int g(\tau|\theta)\, w_t(\theta)\,d\theta \geq L_{t-1}
$$

Per `t → ∞`, `w_t` converge a una **delta di Dirac** centrata nello stimatore [[Stima di Massima Verosimiglianza|ML]]:

$$
w_\infty(\theta) = \delta(\theta - \hat\theta_{ML})
$$

In pratica ci si ferma a `t = 1` (un aggiornamento) per evitare l'overfitting del modello.

## Rischio teorico e KL

Il rischio teorico del modello Bayesiano con log-loss coincide con la [[Divergenza di Kullback-Leibler]]:

$$
\ell(g) = D_{KL}\!\left(f(\tau) \,\Big\|\, \int g(\tau|\theta) w(\theta)\,d\theta\right) + \mathrm{const}
$$

Minimizzare il rischio equivale a massimizzare l'evidenza `∫ g(τ|θ) w(θ) dθ`.

## Collo di bottiglia computazionale

Il calcolo dell'integrale `g(τ) = ∫ g(τ|θ) g(θ) dθ` è spesso intrattabile in forma chiusa. Soluzioni:
- **[[Distribuzioni coniugate]]**: prior scelto in modo che la posterior sia nella stessa famiglia.
- **Approssimazione di Laplace (→ [[BIC]])**: espansione al secondo ordine della log-posterior.
- Metodi MCMC (vedi [[Metropolis-Hastings]]).

## Connessioni con approcci frequentisti

| Approccio | θ | Stima |
|---|---|---|
| Frequentista (MLE) | Costante fissa | `θ̂_ML = argmax g(τ|θ)` |
| Bayesiano | Variabile aleatoria | `g_τ(x) = ∫ g(x|θ) g(θ|τ) dθ` |
| MAP | Variabile aleatoria | `θ̄ = argmax g(θ|τ)` |

## Vantaggi rispetto a MLE

- Permette di definire [[Intervalli di credibilità]].
- Incorpora prior knowledge.
- Gestisce meglio dataset piccoli o sbilanciati (es. zero decessi in un campione).

## Esempio: modello normale con prior gaussiano

Prior: `µ ∼ N(ν, φ²)`, `1/σ² ∼ Gamma(α, β)`. La posterior `g(µ|σ², τ)` è ancora gaussiana con media:

$$
\mu_n = \gamma_n \bar x_n + (1-\gamma_n)\nu, \quad \gamma_n = \frac{n/\sigma^2}{1/\varphi^2 + n/\sigma^2} \xrightarrow{n\to\infty} 1
$$

Con prior non informativo (`φ → ∞`), la posterior è `N(x̄_n, σ²/n)` — si ritrovano i risultati frequentisti.

## Esempio: mortalità neonatale (dataset sbilanciato)

Con `n = 100` e `s = 0` decessi: MLE dà `θ̂ = 0` (impossibilità irrealistica). Un prior `Beta(1,1)` porta a posterior `Beta(1, 101)` con media `1/102 ≈ 0.01` — più ragionevole.

## Collegamenti

- Stima puntuale: [[Stima MAP]]
- Prior+posterior coniugati: [[Distribuzioni coniugate]]
- Approssimazione: [[BIC]]
- Misura di rischio: [[Divergenza di Kullback-Leibler]]
- Intervalli: [[Intervalli di credibilità]]
- Convergenza: [[Stima di Massima Verosimiglianza]]

## Fonti

- [[Dispense MatML — Galletti]] (§2.10, pp. 30-41)
