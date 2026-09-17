---
tipo: concetto
titolo: Embedding isometrico
tag: [topologia, ml, dimensionality-reduction]
cluster: analisi
ultima-modifica: 2026-04-30
---

# Embedding isometrico

Mappa $f : X \to Z$ tra due [[Spazio metrico|spazi metrici]] che **preserva esattamente** le distanze:

$$
d_Z(f(x), f(y)) = d_X(x, y) \quad \forall x, y \in X
$$

Se $f$ è anche biettiva si parla di **isometria** — relazione di equivalenza fra spazi metrici (spazi isometrici sono "lo stesso spazio").

## Quasi isometrie e distorsione

Trovare un embedding isometrico esatto in dimensione bassa è raro. Si rilassa il vincolo cercando una mappa che preservi le distanze *approssimativamente*:

- **Distorsione relativa**:
  $$
  \frac{d_Y(f(x_1), f(x_2))}{d_X(x_1, x_2)} \approx 1
  $$
- **Distorsione assoluta**:
  $$
  |d_Y(f(x_1), f(x_2)) - d_X(x_1, x_2)| \approx 0
  $$

La metrica di distorsione si sceglie a seconda del problema. Quando $d_Y = \|\cdot\|_2$, l'immagine $f(X)$ è la **forma canonica** di $X$.

## Algoritmi che ne sono istanze

- [[Multidimensional Scaling]] (MDS): minimizza la distorsione assoluta quadratica globale.
- [[Stochastic Neighbor Embedding]] / [[t-SNE]]: preservano le **similarità locali** invece delle distanze esatte (preferiscono distorcere le distanze grandi per preservare quelle piccole).

## Collegamenti

- Spazio dove vivono: [[Spazio metrico]]
- Implementazioni: [[Multidimensional Scaling]], [[t-SNE]]
- Discusso in: [[Machine Learning]]

## Fonti

- [[Dispense Machine Learning — Galletti]] (§7.1, pp. 23-24)
