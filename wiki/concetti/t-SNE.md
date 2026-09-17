---
tipo: concetto
titolo: t-SNE
tag: [ml, dimensionality-reduction, visualizzazione]
cluster: ml
ultima-modifica: 2026-04-30
---

# t-SNE (t-distributed Stochastic Neighbor Embedding)

Variante migliorata di [[Stochastic Neighbor Embedding|SNE]] per **visualizzare dati ad alta dimensione** in 2 o 3 dimensioni. Differenza chiave: nello spazio target si usa una **distribuzione di Cauchy** (Student-t a 1 grado di libertà) al posto della gaussiana.

## Formulazione

**Spazio originale** — gaussiana (come SNE):
$$
p_{ij} \propto \exp\!\left(-\frac{\|x_i - x_j\|^2}{2\sigma_i^2}\right)
$$

**Spazio target** — Cauchy (code lunghe):
$$
q_{ij} \propto \frac{1}{1 + \|z_i - z_j\|^2}
$$

Si minimizza la [[Divergenza di Kullback-Leibler]] $D_{KL}(P \| Q)$.

## Perché Cauchy

La gaussiana decade molto velocemente: due punti lontani nello spazio target hanno $q_{ij}$ trascurabile, e distanze ulteriori non vengono penalizzate. La Cauchy ha **code pesanti**: anche distanze grandi mantengono $q_{ij}$ apprezzabile, evitando il collasso visivo dei cluster lontani.

## Gradiente

$$
\frac{\partial D_{KL}}{\partial z_i} = 4 \sum_j (p_{ij} - q_{ij})(z_i - z_j)(1 + \|z_i - z_j\|^2)^{-1}
$$

Da confrontare con SNE (gaussiana anche in target):
$$
\frac{\partial D_{KL}}{\partial z_i} = 2 \sum_j (p_{ij} - q_{ij} + p_{ji} - q_{ji})(z_i - z_j)
$$

## Pro e contro

✅ **Forte sui cluster**: separa visualmente strutture locali ben distinte.

⚠️ **Limiti**:
- Le distanze tra cluster nello spazio target **non sono interpretabili**.
- Sensibile alla perplessità (iperparametro).
- Non è una vera proiezione: ogni run produce embedding diversi.
- Non scala oltre $\sim 10^4$ punti senza approssimazioni (Barnes-Hut).

## Collegamenti

- Genitore: [[Stochastic Neighbor Embedding]]
- Loss: [[Divergenza di Kullback-Leibler]]
- Persona: [[Cauchy]] (distribuzione)
- Alternative: [[Multidimensional Scaling]], [[Principal Component Analysis]]
- Discusso in: [[Machine Learning]]

## Fonti

- [[Dispense Machine Learning — Galletti]] (§7.4, p. 25)
