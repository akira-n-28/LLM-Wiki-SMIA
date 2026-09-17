---
tipo: concetto
titolo: Approssimazione stocastica
tag: [ottimizzazione, statistica-computazionale, ml]
cluster: ottimizzazione
fonti: 1
ultima-modifica: 2026-05-04
---

# Approssimazione stocastica

Famiglia di metodi per ottimizzare una funzione di costo `S(λ)` a cui **non si ha accesso diretto**: tipicamente `S(λ) = E_f[S̃(λ, X)]` è un valore atteso, noto solo tramite uno stimatore rumoroso `Ŝ(λ)`.

## Contesto motivante

Nel [[Importance Sampling]], si vuole trovare `λ* = argmin_λ Var_g[µ̂]`, che equivale a minimizzare:

$$
S(\lambda) = \mathbb{E}_f\!\left[\frac{H^2(X)\,f(X)}{g_\lambda(X)}\right]
$$

Non accessibile in forma chiusa; disponibile solo lo stimatore MC:

$$
\hat S(\lambda) = \frac{1}{N}\sum_{k=1}^N \frac{H^2(x_k)\,f(x_k)}{g_\lambda(x_k)}
$$

## Idea: discesa del gradiente rumoroso

Si sostituisce il gradiente vero `∇S(λ)` con il **gradiente stimato** `∇Ŝ(λ)`, calcolato per **differenze finite centrate**:

$$
\frac{\partial S}{\partial \lambda_i}(\lambda) \approx \frac{\hat S(\lambda + e_i\,\delta/2) - \hat S(\lambda - e_i\,\delta/2)}{\delta}, \quad i = 1, \ldots, d
$$

Aggiornamento:

$$
\lambda_{t+1} = \lambda_t - \beta_t \,\nabla\hat S(\lambda_t)
$$

## Trade-off su δ (ampiezza delle differenze finite)

- **δ piccolo**: la differenza finita approssima bene la vera derivata (bias↓), ma la varianza esplode come `1/δ²` (varianza↑).
- **δ grande**: varianza bassa, ma la differenza finita è inaccurata (bias↑).

$$
\mathrm{Var}\!\left[\frac{\hat S(\lambda + e_i\delta/2) - \hat S(\lambda - e_i\delta/2)}{\delta}\right] \propto \frac{1}{\delta^2}
$$

In pratica si sceglie `δ` come un compromesso, spesso dipendente da `t`.

## Trade-off sul learning rate βₜ

- **βₜ grande**: aggiornamenti veloci ma instabili.
- **βₜ piccolo**: aggiornamenti stabili ma lenti.

## Condizione di Robbins-Monro per la convergenza

Affinché la sequenza `λ₁, λ₂, …` converga all'ottimo `λ*`:

$$
\sum_{t=1}^\infty \beta_t = \infty \quad \text{e} \quad \sum_{t=1}^\infty \beta_t^2 < \infty
$$

La prima condizione garantisce che i passi possano coprire distanze arbitrarie; la seconda che il rumore venga smorzato progressivamente. Scelta tipica: `β_t = c/t`.

## Algoritmi classici

- **Robbins-Monro** (1951): ottimizzazione di `S(λ) = E[S̃(λ, X)]` usando un solo campione per step.
- **Kiefer-Wolfowitz** (1952): come Robbins-Monro ma usa differenze finite per stimare il gradiente.
- **SGD** ([[Stochastic Gradient Descent]]): caso speciale con `g = -∇E[ℓ(X, λ)]`, una osservazione per step.

## Connessione con SGD

[[Stochastic Gradient Descent]] è la versione per il training di reti neurali: `λ = β` (pesi), `S(β) = E[ℓ(X, β)]`, `Ŝ(β)` = loss su un mini-batch. Le condizioni di Robbins-Monro si traducono nel learning rate schedule decrescente tipico dei training professionali.

## Connessione con il metodo del corrispondente stocastico

L'[[Approssimazione stocastica]] usa un gradiente rumoroso e aggiorna iterativamente. Il [[Metodo del corrispondente stocastico]] fissa il campione una volta per tutte e risolve un problema deterministico. I due approcci sono complementari:

| | Approssimazione stocastica | Corrispondente stocastico |
|---|---|---|
| Campioni | Nuovi a ogni step | Fissi |
| Costo per step | Basso (`O(N/step)`) | Alto (risolve problema deterministico) |
| Convergenza | Asintotica (dipende da βₜ) | LLN + ottimizzazione deterministica |

## Connessione con Simulated Annealing

[[Simulated Annealing]] è un'altra tecnica per minimizzare funzioni di costo rumorose, ma usa il campionamento Bayesiano (catena di Markov) invece della discesa del gradiente.

## Limitazione: scarsa scalabilità in alta dimensionalità

Con `d` grande, le `2d` valutazioni per step (differenze finite centrate) diventano costose. In quel caso si usano gradienti stocastici (SGD) o tecniche di gradiente privo di gradienti (gradient-free).

## Connessione con i corsi SMIA

- [[Ottimizzazione]]: metodi del gradiente, convergenza, condizioni di Armijo.
- [[Machine Learning]]: SGD come caso speciale per il training di modelli.

## Collegamenti

- Generalizza: [[Stochastic Gradient Descent]] (caso speciale per ML)
- Alternativa: [[Metodo del corrispondente stocastico]]
- Ottimizza: [[Importance Sampling]] (parametro λ della pdf IS)
- Usata in: [[Simulated Annealing]] (concettualmente), [[Metodo Cross-Entropy]]

## Fonti

- [[Dispense MatML — Galletti]] (§3.15.1, pp. 64-65)
