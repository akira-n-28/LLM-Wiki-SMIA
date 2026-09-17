---
tipo: concetto
titolo: Apprendimento statistico
tag: [ml, statistica, fondamenti]
cluster: ml
fonti: 1
ultima-modifica: 2026-04-30
---

# Apprendimento statistico

Disciplina che mira a **scoprire pattern nei dati** osservati per fare previsioni e comprendere la struttura del fenomeno. A differenza dell'apprendimento automatico in senso stretto, è **primario** l'atto di capire il modello, e solo successivamente l'accuratezza.

## Elementi fondamentali

- **Vettore delle features**: `x ∈ Rᵈ`
- **Variabile di risposta**: `Y ∈ R` (in generale)
- **Stima del modello**: `ŷ = g(x)`

A seconda del task:
- Regressione: `Y ∈ R`
- Classificazione binaria: `Y ∈ {0,1}`
- Classificazione multiclasse: `Y ∈ {0, …, C-1}`

## Tipologie

- **Supervisionato**: regressione, classificazione (si conosce `(x, y)`).
- **Non supervisionato**: clustering, PCA, kernel density estimation (vedi [[Apprendimento non supervisionato]]).

## Obiettivo formale

Data una distribuzione `(X, Y)` e una [[Funzione di perdita]] `L`, si cerca:

$$
g^* = \arg\min_g \mathbb{E}[L(Y, g(X))] = \arg\min_g \ell(g)
$$

`ℓ(g)` è il [[Rischio teorico]]. Poiché la distribuzione è ignota, in pratica si minimizza il [[Rischio empirico]] su un training set ([[ERM]]).

## Trade-off centrali

- [[Bias-Variance trade-off]] (puntuale)
- [[Errore di approssimazione e di stima]] (decomposizione globale)

## Collegamenti

- Si fonda su: [[Statistica inferenziale]]
- Strumenti chiave: [[ERM]], [[Funzione di perdita]], [[Cross-validation]]
- Variante: [[Apprendimento Bayesiano]]
- Pagina del corso: [[Matematica per il Machine Learning]]
- Si collega a: [[Machine Learning]] (Rodolà), [[Ottimizzazione]] (Sciandrone), [[Informatica per il Machine Learning]]

## Fonti

- [[Dispense MatML — Galletti]] (sezione 2.1, pp. 9-11)
