---
tipo: concetto
titolo: Mappe lineari
tag: [algebra-lineare, matematica]
cluster: algebra
fonti: 2
ultima-modifica: 2026-05-05
---

# Mappe lineari (trasformazioni lineari)

Una **mappa lineare** $T : V \to W$ tra due [[Spazio vettoriale|spazi vettoriali]] è una funzione con le proprietà:

- **Additività**: $T(u + v) = T(u) + T(v) \quad \forall u, v \in V$
- **Omogeneità**: $T(\lambda v) = \lambda T(v) \quad \forall v \in V,\, \forall \lambda \in \mathbb{R}$

## Esempi

| Mappa | Spazio | Nota |
|---|---|---|
| Identità $I : V \to V$ | qualsiasi | $I(v) = v$ |
| Derivata $D : \mathcal{F}(\mathbb{R}) \to \mathcal{F}(\mathbb{R})$ | funzioni | $D(f) = f'$ |
| Integrale $T : \mathcal{F}(\mathbb{R}) \to \mathbb{R}$ | funzioni | $T(f) = \int_0^1 f(x)\,dx$ |
| Moltiplicazione per matrice $T(x) = Ax$ | $\mathbb{R}^n \to \mathbb{R}^m$ | caso finito-dimensionale |

## Rappresentazione matriciale

Data una base $v_1, \ldots, v_n$ di $V$ e $w_1, \ldots, w_m$ di $W$, la mappa $T$ è univocamente rappresentata da una matrice $m \times n$ con coefficienti $T_{i,j}$ tali che $T(v_j) = \sum_i T_{i,j} w_i$.

**Le mappe lineari formano a loro volta uno spazio vettoriale.**

## Nucleo e immagine

Data $T: V \to W$:

- **Nucleo**: $\ker T = \{v \in V : T(v) = 0_W\} \leq V$ — sottospazio di $V$.
- **Immagine**: $\mathrm{Im}(T) = \{T(v) : v \in V\} \leq W$ — sottospazio di $W$.

$T$ è iniettiva $\Leftrightarrow \ker T = \{0_V\}$; $T$ è suriettiva $\Leftrightarrow \mathrm{Im}(T) = W$.

Il [[Teorema della dimensione (algebra lineare)]] (rank-nullity) lega queste quantità: $\dim V = \dim \ker T + \dim \mathrm{Im}(T)$.

Vedi [[Applicazione lineare]] per la trattazione completa con cambio di base e similitudine.

## Prodotto di mappe

$(S \circ T)(v) = S(T(v))$, con proprietà: associatività, elemento neutro $I$, distributività.

## Trucchi matriciali utili

- $(BC)^\top = C^\top B^\top$
- $(BC)^{-1} = C^{-1} B^{-1}$
- Se $A$ è ortogonale: $A^\top = A^{-1}$, quindi $A^\top A = I$
- $\nabla_\Theta (\Theta^\top A \Theta) = (A + A^\top)\Theta$; se $A$ simmetrica $= 2A\Theta$

## Rilevanza per il ML

Ogni layer di un [[Multi-Layer Perceptron]] è la composizione di una mappa lineare $x \mapsto Wx + b$ con una non-linearità $\sigma$. La composizione di sole mappe lineari rimane lineare — da cui la necessità di $\sigma$.

## Connessioni

- Base: [[Spazio vettoriale]]
- Trattazione completa con cambio base: [[Applicazione lineare]]
- Teorema chiave: [[Teorema della dimensione (algebra lineare)]]
- Matrice dei dati in ML: [[Regressione lineare]]
- Composizione non lineare: [[Multi-Layer Perceptron]]
- Caso spettrale: [[Autovalori e autovettori]]
- Discusso in: [[Algebra Lineare]], [[Machine Learning]] (§2)

## Fonti

- [[Dispense Machine Learning — Galletti]] (§2, pp. 3-5)
- [[Dispense AlgLin — Galletti]]
