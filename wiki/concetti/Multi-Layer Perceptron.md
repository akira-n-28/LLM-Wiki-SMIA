---
tipo: concetto
titolo: Multi-Layer Perceptron
tag: [reti-neurali, deep-learning, ml]
cluster: ml
ultima-modifica: 2026-04-30
---

# Multi-Layer Perceptron (MLP)

Modello di rete neurale **feedforward** ottenuto componendo iterativamente trasformazioni affini e non linearità. Una composizione di sole funzioni lineari resta lineare; introducendo una non linearità $\sigma$ tra i layer si ottiene un modello arbitrariamente espressivo:

$$
g_\Theta(x) = (\sigma \circ f_{\Theta_n}) \circ (\sigma \circ f_{\Theta_{n-1}}) \circ \cdots \circ (\sigma \circ f_{\Theta_1})(x)
$$

dove ogni layer è $x_{l+1} = \sigma_l(W_l x_l + b_l)$ con pesi $W_l$ e bias $b_l$.

## Componenti

- **Neurone (unità nascosta):** una riga di $W$ — funzione scalare $\mathbb{R}^p \to \mathbb{R}$.
- **Larghezza** del layer: numero di neuroni in parallelo.
- **Profondità:** numero di layer impilati.
- **Funzioni di attivazione $\sigma$:**
  - sigmoide $\sigma(x) = \frac{1}{1+e^{-x}}$ (range $[0,1]$, satura sui bordi)
  - **ReLU** $\sigma(x) = \max(0, x)$ (lineare positiva, non satura)
  - tanh, GELU, ...

## Output e codominio

Il layer di output determina il codominio: se $\sigma$ finale è la sigmoide, la rete mappa $\mathbb{R}^p \to [0,1]^q$ (utile per multi-label).

## Espressività: teorema di approssimazione universale

Vedi [[Teorema di approssimazione universale]]: un MLP con un solo strato nascosto sufficientemente largo può approssimare *qualunque* funzione continua su un compatto.

## Addestramento

Loss tipica: MSE per regressione, [[Cross-entropy]] per classificazione. Ottimizzazione: [[Stochastic Gradient Descent|SGD]] con [[Backpropagation]] per il calcolo efficiente del gradiente sulla rete profonda.

## Collegamenti

- Caso degenere a 1 layer: [[Regressione logistica]] (con sigmoide).
- Calcolo gradiente: [[Backpropagation]], [[Grafo computazionale]].
- Garanzia teorica: [[Teorema di approssimazione universale]].
- Modello fully-connected con dinamica: [[Modelli Matematici per la Fisica II]] tratta il modello di Hopfield, parente "ricorrente" dell'MLP.
- Discusso in: [[Machine Learning]], [[Informatica per il Machine Learning]] (in ingest futuro), [[Ottimizzazione]] (problema dell'addestramento).

## Fonti

- [[Dispense Machine Learning — Galletti]] (§5, pp. 15-17)
