---
tipo: concetto
titolo: Cross-entropy
tag: [ml, loss, probabilità]
cluster: ml
ultima-modifica: 2026-04-30
---

# Cross-entropy

Funzione di loss per problemi di classificazione, basata sul **negative log-likelihood** della distribuzione predetta rispetto ai target.

## Caso binario (BCE)

Per target $y_i \in \{0, 1\}$ e probabilità predetta $\hat p_i = \sigma(z_i)$ con $\sigma$ sigmoide:

$$
\ell(\Theta) = -\sum_{i=1}^n \big[y_i \ln \hat p_i + (1-y_i) \ln(1 - \hat p_i)\big]
$$

## Caso generale

$$
\ell(\Theta) = -\frac{1}{N} \sum_{i=1}^N y_i \log f(x_i; \Theta)
$$

## Perché funziona meglio della MSE per la classificazione

- Composta con la sigmoide produce una loss **convessa** in $(a, b)$ — la MSE no.
- Penalizza pesantemente predizioni sbagliate ad alta confidenza: $-\ln(\hat p) \to \infty$ per $\hat p \to 0$.
- Il gradiente è proporzionale all'errore $(y_i - \hat p_i)$: niente saturazione del gradiente come capita con MSE+sigmoide.

## Connessione con la divergenza di Kullback-Leibler

Minimizzare la cross-entropy è equivalente a minimizzare la [[Divergenza di Kullback-Leibler]] $D_{KL}(p \| \hat p)$ a meno di un termine costante (entropia di $p$).

## Collegamenti

- Usata in: [[Regressione logistica]], [[Multi-Layer Perceptron]]
- Cugina informazionale: [[Divergenza di Kullback-Leibler]]
- Discusso in: [[Machine Learning]]

## Fonti

- [[Dispense Machine Learning — Galletti]] (§3.3, p. 11)
