---
tipo: concetto
titolo: Bias-Variance trade-off
tag: [ml, statistica, fondamenti]
cluster: ml
fonti: 1
ultima-modifica: 2026-04-30
---

# Bias-Variance trade-off

Decomposizione **puntuale** dell'errore quadratico medio della previsione di un learner `g_T^G(x)` rispetto alla ground truth `g*(x)`, al variare del training set `τ`:

$$
\mathbb{E}_\tau\!\left[(g_\tau^G(x) - g^*(x))^2\right] = \underbrace{\Big(\mathbb{E}_\tau[g_\tau^G(x)] - g^*(x)\Big)^2}_{\text{Bias}^2 \text{ puntuale}} + \underbrace{\text{Var}_\tau[g_\tau^G(x)]}_{\text{Varianza puntuale}}
$$

Si ottiene espandendo `D(x,τ) = g_τ^G(x) - g*(x)` e usando `Var(X) = E[X²] - (E[X])²`.

## Interpretazione

- **Bias**: errore **sistematico** del modello — quanto, in media sui training set, la previsione si discosta dalla verità.
- **Varianza**: errore **stocastico** — quanto la previsione fluttua al variare di `τ`.

## Trade-off

Aumentando la complessità del modello `g`:

$$
\text{complessità} \uparrow \;\Longrightarrow\; \text{Bias} \downarrow \quad\text{e}\quad \text{Varianza} \uparrow
$$

Esempio canonico: in [[Regressione polinomiale]], aumentando il grado `p`:
- Bias↓ (il polinomio si avvicina alla `g*`).
- Varianza↑ (il modello "insegue" il rumore: overfitting).

## Relazione con la decomposizione globale

Integrando sul marginale di `X`:

$$
\mathbb{E}_{X,T}\!\left[\ell(g_T^G)\right] = \ell^* + \mathbb{E}_X\!\left[(\mathbb{E}_T[g_T^G(X)|X] - g^*(X))^2\right] + \mathbb{E}_X\!\left[\text{Var}_T[g_T^G(X)|X]\right]
$$

Decomposizione duale: vedi [[Errore di approssimazione e di stima]].

## Strumenti per gestire il trade-off

- Selezione della complessità via [[Cross-validation]]
- [[BIC]]: penalità che bilancia fit e numero di parametri
- Regolarizzazione (non trattata in dettaglio nelle dispense MatML)

## Collegamenti

- Versione globale: [[Errore di approssimazione e di stima]]
- Si manifesta in: [[Regressione polinomiale]], [[Cross-validation]]
- Argomento trasversale: [[Bias-Variance trade-off]]

## Fonti

- [[Dispense MatML — Galletti]] (sezione 2.4, pp. 16-22)
