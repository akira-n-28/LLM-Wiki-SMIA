---
tipo: concetto
titolo: Errore di approssimazione e di stima
tag: [ml, statistica, fondamenti]
cluster: ml
fonti: 1
ultima-modifica: 2026-04-30
---

# Errore di approssimazione e di stima

Decomposizione **globale** del [[Rischio teorico]] del learner `g_τ^G` in tre componenti:

$$
\ell(g_\tau^G) = \underbrace{\ell^*}_{\text{Bayes}} + \underbrace{(\ell(g^G) - \ell^*)}_{\text{Approssimazione}} + \underbrace{(\ell(g_\tau^G) - \ell(g^G))}_{\text{Stima (Statistico)}}
$$

dove `g^G = arg min_{g ∈ G} ℓ(g)` è il **miglior modello teorico** nella classe `G`.

## I tre termini

1. **Rischio di Bayes** `ℓ*`: limite irriducibile dovuto al rumore intrinseco (`Y = g*(X) + ε`, `Var[ε] = ν²`). Nessun modello può scendere sotto.

2. **Errore di approssimazione** `ℓ(g^G) - ℓ*`: penalità per aver limitato la ricerca a `G`. Non dipende da `τ`. Si riduce **scegliendo una classe più ampia/complessa**. Strettamente positivo se `g* ∉ G`.

3. **Errore di stima (statistico)** `ℓ(g_τ^G) - ℓ(g^G)`: divario tra il modello addestrato e il miglior modello teorico in `G`. Dipende dalla finitezza del campione. Tende a 0 per `|τ| → ∞`.

## Forma esplicita per MSE

Sotto loss quadratica:

- `ℓ* = Var(ε)`
- `ℓ(g^G) - ℓ* = E[(g^G(X) - g*(X))²]`
- `ℓ(g_τ^G) - ℓ(g^G) = E[(g_τ^G(X) - g^G(X))²]`

Caso lineare con `U ∼ U(0,1)` e `g(x) = x^T β`: i conti si esplicitano via [[Matrice di Hilbert]].

## Trade-off di complessità

$$
|G| \uparrow \;\Longrightarrow\; \text{Approssimazione} \downarrow \quad\text{ma}\quad \text{Stima} \uparrow
$$

Stesso trade-off del [[Bias-Variance trade-off]], ma a livello globale anziché puntuale.

## Collegamenti

- Versione puntuale: [[Bias-Variance trade-off]]
- Esemplificato in: [[Regressione polinomiale]] (con [[Matrice di Hilbert]])
- Stimato via: [[Cross-validation]], [[BIC]]

## Fonti

- [[Dispense MatML — Galletti]] (sezione 2.4, pp. 16-21; esempi 2.4-2.6)
