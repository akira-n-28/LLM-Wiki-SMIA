---
tipo: concetto
titolo: Funzione sigmoide
tag: [ml, reti-neurali, statistica]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# Funzione sigmoide

La **funzione sigmoide** (o logistica) mappa ogni $x \in \mathbb{R}$ nell'intervallo $(0, 1)$:

$$
\sigma(x) = \frac{1}{1 + e^{-x}}
$$

## Proprietà

- **Range**: $(0, 1)$ — interpretabile come probabilità.
- **Monotona crescente**: $\sigma'(x) = \sigma(x)(1 - \sigma(x)) > 0$.
- **Simmetria**: $\sigma(-x) = 1 - \sigma(x)$.
- **Derivata elegante**: $\frac{d\sigma}{dx} = \sigma(x)(1 - \sigma(x))$ — si esprime in termini di $\sigma$ stessa.
- **Satura** per $|x| \gg 0$: $\sigma(x) \to 1$ per $x \to +\infty$, $\sigma(x) \to 0$ per $x \to -\infty$.

## Uso in regressione logistica

In classificazione binaria si modella $P(y=1 \mid x) = \sigma(ax + b)$. La [[Cross-entropy|log loss]] che ne deriva è:

$$
c(x_i, y_i) = -y_i \ln(\sigma(ax_i + b)) - (1 - y_i)\ln(1 - \sigma(ax_i + b))
$$

che è **convessa** in $a, b$ (al contrario della MSE con sigmoide) e differenziabile. Vedi [[Regressione logistica]].

## Uso nelle reti neurali

Nei [[Multi-Layer Perceptron|MLP]] la sigmoide è una delle possibili funzioni di attivazione $\sigma$ tra i layer. Rispetto alla **ReLU** ($\max(0, x)$):
- La sigmoide satura per valori grandi → può causare *vanishing gradient*.
- La ReLU è lineare per $x > 0$ e non satura → preferita nella pratica per layer nascosti.

## Teorema di approssimazione universale

Per $\sigma$ sigmoide: lo spazio $\{\sigma(Wx + b)\}$ è **denso** in $C(\Omega)$ per ogni compatto $\Omega \subset \mathbb{R}^p$. Vedi [[Teorema di approssimazione universale]].

## Derivata via regola della catena

$$
\frac{\partial}{\partial a} \ln(\sigma(ax_i + b)) = (1 - \sigma(ax_i + b)) \cdot x_i
$$

Questo rende il gradiente della log loss calcolabile in forma chiusa, ma l'equazione $\nabla_\Theta \ell = 0$ è **trascendente** (non ha soluzione analitica) — si risolve iterativamente con [[Discesa del gradiente]].

## Collegamenti

- Applicazione classificazione: [[Regressione logistica]]
- Come attivazione reti: [[Multi-Layer Perceptron]]
- Alternativa principale: ReLU (in [[Multi-Layer Perceptron]])
- Loss associata: [[Cross-entropy]]
- Discusso in: [[Machine Learning]] (§3.3, §5)

## Fonti

- [[Dispense Machine Learning — Galletti]] (§3.3, pp. 10-12; §5, pp. 15-17)
