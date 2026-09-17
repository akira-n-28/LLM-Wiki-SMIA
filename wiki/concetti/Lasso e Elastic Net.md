---
tipo: concetto
titolo: Lasso e Elastic Net
tag: [ml, regressione, regolarizzazione]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-05
---

# Lasso e Elastic Net

Forme di regolarizzazione per la regressione lineare che estendono la [[Regolarizzazione di Tikhonov|Ridge (L2)]] aggiungendo penalità L1 o combinando L1 e L2.

## Problema comune

La regressione lineare multivariata può overfittare quando il modello è più complesso del necessario. La regolarizzazione aggiunge un termine di penalità alla loss:

$$
\text{Cost}(h) = \text{MSE}(y, \hat{y}) + \lambda \cdot \text{Complexity}(w)
$$

## Ridge (L2) — richiamo

$$
\min_w \text{MSE}(y, \hat{y}) + \lambda \sum_i w_i^2
$$

Ha soluzione chiusa $\hat{w} = (X^\top X + \lambda I_p)^{-1} X^\top y$. Riduce i pesi verso zero ma non li annulla esattamente. Utile con predittori fortemente correlati.

## Lasso (L1)

**Least Absolute Shrinkage and Selection Operator.**

$$
\min_w \text{MSE}(y, \hat{y}) + \lambda \sum_j |w_j|
$$

Geometricamente il vincolo L1 è un rombo nello spazio dei pesi: la soluzione ottima tocca spesso uno spigolo, dove alcune coordinate sono esattamente zero. Questo produce **sparsità**: per valori elevati di $\lambda$, molti coefficienti vengono eliminati.

**Limiti:**
1. Se $p > n$ (più features che campioni), il Lasso seleziona al massimo $n$ variabili.
2. Con variabili altamente correlate, tende a sceglierne una e scartare le altre (non fa "grouped selection").

## Elastic Net

Combina L1 e L2 per superare i limiti del Lasso:

$$
\min_w \text{MSE}(y, \hat{y}) + \lambda \left[ \alpha \sum_j |w_j| + (1-\alpha) \sum_i w_i^2 \right]
$$

dove $\alpha \in [0,1]$ è il mixing parameter e $\lambda \geq 0$ la forza totale di regolarizzazione.

- $\alpha = 1$ → Lasso puro
- $\alpha = 0$ → Ridge puro

**Vantaggi rispetto al Lasso:**
- Conserva la sparsità di L1.
- Il termine L2 favorisce la **grouped selection**: con variabili correlate, le seleziona o scarta insieme.
- Può selezionare più di $n$ variabili quando $p > n$.

## Confronto visivo

Le curve di livello della MSE sono ellissi; il vincolo L2 è un cerchio (bordo liscio → pesi ridotti ma non azzerati), il vincolo L1 è un rombo (angoli sugli assi → sparsità).

## Connessione con la regolarizzazione

Tutti e tre (Ridge, Lasso, Elastic Net) si inquadrano nella famiglia $L_q$ con $q = 2$, $q = 1$ e la loro combinazione.

## Collegamenti

- Generalizza: [[Regolarizzazione di Tikhonov]] (Ridge)
- Applicazione: [[Regressione lineare]]
- Contesto: [[Overfitting e underfitting]]
- Discusso in: [[Informatica per il Machine Learning]] (§3.2, pp. 12-13)

## Fonti

- [[Dispense InfML — Galletti]] (§3.2, pp. 12-13)
