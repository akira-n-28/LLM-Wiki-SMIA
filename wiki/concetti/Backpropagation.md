---
tipo: concetto
titolo: Backpropagation
tag: [reti-neurali, deep-learning, ml]
cluster: ml
ultima-modifica: 2026-04-30
---

# Backpropagation

Algoritmo per calcolare in modo efficiente il gradiente della loss rispetto a tutti i parametri di una rete profonda ([[Multi-Layer Perceptron|MLP]]). È **differenziazione automatica in reverse mode** applicata al [[Grafo computazionale]] della rete.

## Forward mode vs reverse mode

Nel grafo computazionale di $f$, ogni nodo è una variabile, ogni arco un'operazione.

- **Forward mode:** si percorre il grafo sinistra→destra accumulando $\partial \cdot / \partial x$ rispetto a un input fisso. Costo $\propto$ numero di **input**.
- **Reverse mode:** si fa prima un *forward pass* per calcolare i valori intermedi, poi un *backward pass* destra→sinistra accumulando $\partial f / \partial \cdot$. Costo $\propto$ numero di **output**.

In ML tipicamente $\#\text{output} \ll \#\text{input}$ (un solo numero, la loss, dipende da milioni di pesi): il reverse mode è esponenzialmente più conveniente.

## Cosa NON è

> ⚠️ La differenziazione automatica **non** è differenziazione simbolica: non manipola espressioni algebriche, accumula valori numerici durante il pass.

## Struttura tipica

```
forward:  loss = f(W_n, ..., W_1, x)
backward: per l = n, n-1, ..., 1:
    ∂loss / ∂W_l = (∂loss / ∂x_{l+1}) · (∂x_{l+1} / ∂W_l)
    ∂loss / ∂x_l = (∂loss / ∂x_{l+1}) · (∂x_{l+1} / ∂x_l)
```

Le derivate dei layer si propagano **all'indietro** moltiplicandosi per la regola della catena.

## Collegamenti

- Definito su: [[Grafo computazionale]]
- Applicato a: [[Multi-Layer Perceptron]]
- Combinato con: [[Stochastic Gradient Descent]] per l'addestramento.
- Discusso in: [[Machine Learning]], [[Informatica per il Machine Learning]] (RNN: BPTT — backprop through time, da ingerire).

## Fonti

- [[Dispense Machine Learning — Galletti]] (§5.1, pp. 17-18)
