---
tipo: concetto
titolo: Grafo computazionale
tag: [reti-neurali, automazione, deep-learning]
cluster: ml
ultima-modifica: 2026-04-30
---

# Grafo computazionale

Rappresentazione di una funzione composta come **grafo diretto aciclico (DAG)**: ogni nodo è una variabile (input, intermedia o output), ogni arco un'operazione elementare. Lo stesso valore matematico può corrispondere a *più* grafi computazionali equivalenti — la scelta influenza il costo del calcolo del gradiente.

## Esempio

$f(x) = \log x + \sqrt{\log x}$:

```
x ──[log]──► y ──[√]──► z
              │         │
              ▼         ▼
              ╰────[+]──► f
```

Qui $\log x$ viene riusato (nodo $y$), evitando di ricalcolarlo.

## Perché è utile

- Permette il **forward pass** (valutare $f$).
- Permette il **backward pass** ([[Backpropagation]]) per calcolare $\partial f / \partial \cdot$ propagando dalla destra alla sinistra.
- Le librerie moderne (PyTorch, JAX, TensorFlow) costruiscono grafi computazionali implicitamente o esplicitamente.

## Differenziazione automatica

- **Forward mode:** propaga $\partial \cdot / \partial x$ in avanti. Buono se input pochi, output molti.
- **Reverse mode:** propaga $\partial f / \partial \cdot$ all'indietro. Buono se input molti, output pochi (caso ML).

## Collegamenti

- Strumento per: [[Backpropagation]]
- Su cui agisce: [[Multi-Layer Perceptron]]
- Discusso in: [[Machine Learning]]

## Fonti

- [[Dispense Machine Learning — Galletti]] (§5.1, pp. 17-18)
