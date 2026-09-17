---
tipo: concetto
titolo: ERM
tag: [ml, ottimizzazione]
cluster: ml
fonti: 1
ultima-modifica: 2026-04-30
---

# ERM — Empirical Risk Minimization

Principio operativo dell'[[Apprendimento statistico]]: poiché il [[Rischio teorico]] `ℓ(g)` non è computabile (distribuzione vera ignota), si minimizza il [[Rischio empirico]] `ℓ_T(g)` su una classe ristretta `G` (spazio delle ipotesi).

## Schema

$$
g^* = \arg\min_g \ell(g) \quad \longrightarrow \quad g_T^G = \arg\min_{g \in G} \ell_T(g)
$$

## Due passaggi

1. **Selezione della classe `G`**: limita la complessità per evitare overfitting. Trade-off:
   - `G` troppo piccola ⇒ alto [[Errore di approssimazione e di stima|errore di approssimazione]].
   - `G` troppo grande ⇒ alto [[Errore di approssimazione e di stima|errore di stima]] (overfitting).

2. **Minimizzazione di `ℓ_T` in `G`**: problema di ottimizzazione (in molti casi convesso, es. [[Minimi quadrati]] per modelli lineari).

## Esempio canonico

[[Regressione polinomiale]] con `G_p` = polinomi di grado `≤ p-1`. La minimizzazione di `ℓ_T` produce la stima OLS:

$$
\hat{\beta} = (X^T X)^{-1} X^T y
$$

vedi [[Minimi quadrati]].

## Limiti

`ℓ_T(g_T)` (training loss del learner) **sottostima** il rischio reale: la quantità da stimare è il **rischio di generalizzazione** `ℓ(g_T)` su dati nuovi. Strumenti per stimarlo:

- Test set indipendente
- [[Cross-validation]]
- Correzione analitica via [[Ottimismo]] e [[Rischio in-sample]]
- Penalità di complessità: [[BIC]]

## Collegamenti

- Cardine di: [[Apprendimento statistico]]
- Compromesso: [[Bias-Variance trade-off]]
- Generalizza in: [[Apprendimento Bayesiano]] (sostituendo MLE con MAP/posterior predittiva)

## Fonti

- [[Dispense MatML — Galletti]] (sezione 2.2, pp. 11-13)
