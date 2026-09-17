---
tipo: concetto
titolo: Stochastic Neighbor Embedding
tag: [ml, dimensionality-reduction]
cluster: ml
ultima-modifica: 2026-04-30
---

# Stochastic Neighbor Embedding (SNE)

Predecessore di [[t-SNE]]. Idea: invece di preservare distanze euclidee, preservare **similarità locali** misurate come probabilità.

## Probabilità di vicinato

Per ogni punto $x_i$, si definisce una distribuzione su tutti gli altri punti $x_j$ basata su un kernel gaussiano:

$$
p_{ij} = \frac{\exp\!\left(-\frac{\|x_i - x_j\|^2}{2\sigma_i^2}\right)}{\sum_{k \neq i} \exp\!\left(-\frac{\|x_i - x_k\|^2}{2\sigma_i^2}\right)}
$$

L'iperparametro **perplessità** controlla $\sigma_i$ — quanti vicini effettivi vogliamo per ogni punto. Tipico: 5-50.

Nello spazio target di dimensione $k$ si definisce analogamente $q_{ij}$ a partire dai $z_i$.

## Loss: divergenza KL

Si minimizza la [[Divergenza di Kullback-Leibler]]:

$$
D_{KL}(P \| Q) = \sum_{i,j} p_{ij} \log \frac{p_{ij}}{q_{ij}}
$$

L'asimmetria della KL produce un comportamento utile: se $p_{ij}$ è grande e $q_{ij}$ è piccolo (vicini originali finiti lontani nell'embedding) la penalità è alta; viceversa la penalità è bassa. Si premia la **conservazione dei vicinati locali**.

## Limite di SNE e nascita di t-SNE

Nello spazio target lontano (gaussiana con coda corta) i punti distanti diventano "indistinguibili" — collasso visivo dei cluster. La soluzione: usare una distribuzione a code lunghe nello spazio target. Vedi [[t-SNE]].

## Collegamenti

- Migliorato da: [[t-SNE]]
- Loss: [[Divergenza di Kullback-Leibler]]
- Confronta con: [[Multidimensional Scaling]]
- Discusso in: [[Machine Learning]]

## Fonti

- [[Dispense Machine Learning — Galletti]] (§7.3, p. 24)
