---
tipo: concetto
titolo: Regressione logistica
tag: [ml, classificazione]
cluster: ml
ultima-modifica: 2026-04-30
---

# Regressione logistica

Modello per la **classificazione binaria**. Mentre la [[Regressione lineare]] produce un output continuo, qui vogliamo un output in $[0, 1]$ interpretabile come probabilità di appartenenza a una classe. Si compone la combinazione lineare con la **funzione sigmoide**:

$$
\sigma(z) = \frac{1}{1 + e^{-z}}, \qquad p(y=1 \mid x) = \sigma(a x + b)
$$

## Loss: perché serve la cross-entropy

Usare l'errore quadratico medio sulla sigmoide produce una funzione **non convessa** in $(a, b)$: l'ottimizzazione si blocca in minimi locali. Si usa allora la log-loss, che è convessa e differenziabile (vedi [[Cross-entropy]]):

$$
\ell(\Theta) = -\sum_{i=1}^n \big[y_i \ln \sigma(z_i) + (1-y_i) \ln(1 - \sigma(z_i))\big]
$$

con $z_i = a x_i + b$.

## Niente forma chiusa

A differenza della regressione lineare, $\nabla \ell = 0$ è un **sistema di equazioni trascendenti**: nessuna soluzione analitica. Si risolve iterativamente con la [[Discesa del gradiente]] (o varianti come Newton/IRLS). Una proprietà utile della derivata della sigmoide:

$$
\frac{\partial}{\partial a} \ln \sigma(a x_i + b) = (1 - \sigma(a x_i + b)) \, x_i
$$

## Collegamenti

- Loss: [[Cross-entropy]]
- Ottimizzazione: [[Discesa del gradiente]], [[Stochastic Gradient Descent]]
- È un caso particolare di MLP a un layer: [[Multi-Layer Perceptron]]
- Discusso in: [[Machine Learning]]

## Fonti

- [[Dispense Machine Learning — Galletti]] (§3.3, pp. 10-12)
