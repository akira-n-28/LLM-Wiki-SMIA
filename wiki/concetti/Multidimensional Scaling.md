---
tipo: concetto
titolo: Multidimensional Scaling
tag: [ml, dimensionality-reduction]
cluster: ml
ultima-modifica: 2026-04-30
---

# Multidimensional Scaling (MDS)

Algoritmo di [[Embedding isometrico|quasi-embedding]] che cerca una rappresentazione $z_i \in \mathbb{R}^k$ dei punti $x_i \in \mathcal{X}$ minimizzando lo **stress quadratico** delle distanze:

$$
Z^* = \arg\min_{Z \in \mathbb{R}^{n \times k}} \sum_{i > j} \left| d_\mathcal{X}(x_i, x_j) - \|z_i - z_j\|_2 \right|^2
$$

Le distanze nello spazio target sono euclidee; quelle nello spazio originale possono usare qualunque [[Spazio metrico|metrica]].

## Caratteristiche

- **Globale**: cerca di preservare *tutte* le distanze, non solo quelle locali.
- **Differenziabile**: si ottimizza con [[Discesa del gradiente]] o varianti (ma anche soluzione spettrale chiusa nel caso classico).
- È meno efficace di [[t-SNE]] su strutture **a manifold** dove le distanze euclidee globali non sono significative (es. dati su una "spirale" 3D — MDS non smonta la spirale).

## Collegamenti

- Confronta con: [[t-SNE]], [[Stochastic Neighbor Embedding]]
- Spazio formale: [[Spazio metrico]], [[Embedding isometrico]]
- Discusso in: [[Machine Learning]]

## Fonti

- [[Dispense Machine Learning — Galletti]] (§7.2, p. 24)
