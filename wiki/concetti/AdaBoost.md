---
tipo: concetto
titolo: AdaBoost
tag: [ml, ensemble, boosting]
cluster: ml
ultima-modifica: 2026-04-30
---

# AdaBoost (Adaptive Boosting)

Algoritmo di **boosting**: combina molti weak learner ([[Decision Tree|decision stump]] tipicamente) in un classificatore forte. Idea: ogni iterazione **ripesa** i dati di training per concentrare il prossimo weak learner sui campioni che il precedente ha sbagliato.

## Schema

1. Inizializza pesi uniformi $w_i^{(0)} = 1/n$.
2. Per $m = 1, \ldots, M$:
   a. Addestra un weak learner $h_m$ pesando i campioni con $w_i^{(m-1)}$.
   b. Calcola l'errore pesato $\varepsilon_m$ e il coefficiente $\alpha_m \propto \log\frac{1-\varepsilon_m}{\varepsilon_m}$ (proporzionale all'accuratezza).
   c. Aumenta i pesi sui campioni mal classificati: $w_i^{(m)} \propto w_i^{(m-1)} \exp(\alpha_m \cdot \mathbb{1}[h_m(x_i) \neq y_i])$.
3. Predici con voto pesato: $H(x) = \mathrm{sign}\left(\sum_m \alpha_m h_m(x)\right)$.

## Caratteristiche

- I coefficienti $\alpha_m$ sono **proporzionali all'accuratezza** del weak learner — chi sbaglia poco pesa di più.
- Tipicamente i weak learner sono [[Decision Tree|decision stump]] (semplici, veloci, alto bias / bassa varianza).
- **Tendenza all'overfitting** (in particolare con dati rumorosi) — l'algoritmo dà sempre più peso ai campioni difficili, che possono essere outlier.

## Confronto con Gradient Boosting

AdaBoost è un caso particolare di boosting (loss esponenziale). Il [[Gradient Boosting]] generalizza il principio a una loss arbitraria, interpretando ogni nuovo weak learner come l'approssimazione di un *gradiente negativo* nello spazio delle funzioni.

## Collegamenti

- Caso speciale di: [[Gradient Boosting]]
- Mattoncino: [[Decision Tree]]
- Confronto: [[Random Forest]] (bagging vs boosting)
- Discusso in: [[Machine Learning]]

## Fonti

- [[Dispense Machine Learning — Galletti]] (§8, pp. 26-27)
