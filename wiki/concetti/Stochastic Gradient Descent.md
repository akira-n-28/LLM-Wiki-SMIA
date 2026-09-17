---
tipo: concetto
titolo: Stochastic Gradient Descent
tag: [ottimizzazione, ml]
cluster: ottimizzazione
ultima-modifica: 2026-04-30
---

# Stochastic Gradient Descent (SGD)

Variante stocastica della [[Discesa del gradiente]]. A ogni iterazione si stima il gradiente della loss usando solo un sottoinsieme casuale dei dati (**mini-batch** $B \subset T$ con $|B| = m \ll n$):

$$
\frac{1}{m} \sum_{i \in B} \nabla \hat\ell(\theta) \;\approx\; \frac{1}{n} \sum_{i \in T} \nabla \hat\ell(\theta)
$$

## Algoritmo

1. Inizializza $\theta$.
2. Estrai un mini-batch $B$.
3. Aggiorna: $\theta \leftarrow \theta - \alpha \nabla \ell_\theta(B)$.
4. Torna al passo 2.

Quando si è iterato su tutti i mini-batch del dataset si è completata una **epoch**. L'addestramento procede tipicamente per molte epoch.

## Perché funziona

- Ogni passo è $n/m$ volte più economico del GD batch.
- Il gradiente rumoroso ha un effetto **regolarizzante** implicito: aiuta a sfuggire da minimi locali stretti e selle.
- Per loss non convesse (deep learning) è spesso preferibile rispetto al batch GD.

## Estensioni

Su SGD si innestano: momentum (vedi [[Discesa del gradiente]]), Adam, RMSProp, AdaGrad — tutti varianti adattive del learning rate.

## Collegamenti

- Genitore: [[Discesa del gradiente]]
- Usato in: [[Multi-Layer Perceptron]], [[Backpropagation]]
- Discusso in: [[Machine Learning]]

## Fonti

- [[Dispense Machine Learning — Galletti]] (§4.1, p. 15)
