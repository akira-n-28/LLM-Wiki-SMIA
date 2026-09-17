---
tipo: concetto
titolo: Problema degli esperti
tag: [algoritmi, machine-learning, online-learning, probabilità]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-05
---

# Problema degli esperti

## Modello

$n$ esperti fanno previsioni binarie $y_{it} \in \{0,1\}$ ad ogni round $t$. L'algoritmo sceglie $z_t \in \{0,1\}$, poi si osserva la realtà $x_t \in \{0,1\}$. Se $z_t \neq x_t$: errore. Obiettivo: minimizzare gli errori rispetto al miglior esperto.

## Algoritmo del dimezzamento

```
S ← {1,...,n}
for t = 1 to T:
    z_t ← voto di maggioranza degli esperti in S
    osserva x_t
    S ← S \ {i | y_{it} ≠ x_t}
```

**Teorema:** se esiste un esperto perfetto (0 errori), il dimezzamento fa al più $\lceil \log_2 n \rceil$ errori (ogni errore elimina almeno metà degli esperti).

## Weighted Majority (WM)

Pesi $w_i^{(0)} = 1$. Ad ogni round: predici 1 se $\sum_{i: y_{it}=1} w_i \geq \sum_{i: y_{it}=0} w_i$, altrimenti 0. Se $y_{it} \neq x_t$: $w_i \leftarrow w_i/2$.

**Teorema:**
$$m \leq 2{,}41\,(m^* + \log_2 n)$$
dove $m^*$ è il numero di errori del miglior esperto.

*Dimostrazione via potenziale $W^t = \sum_i w_i^t$: se l'algoritmo sbaglia, almeno metà del peso sbaglia, dunque $W^{t+1} \leq \frac{3}{4} W^{t-1}$. Si conclude con $W^T \geq 2^{-m^*}$ e $W^T \leq (3/4)^m \cdot n$.*

## Lower bound per algoritmi deterministici

**Teorema:** nessun algoritmo deterministico può garantire $m < 2m^*$ (costruzione avversariale: due esperti opposti, realtà sempre contraria all'algoritmo).

## Randomized Weighted Majority (RWM$_\varepsilon$)

Pesi aggiornati con fattore $(1-\varepsilon)$. Ad ogni round si campiona un esperto dalla distribuzione proporzionale ai pesi.

**Teorema:** per $0 < \varepsilon < 1/2$:
$$\mathbb{E}[m] \leq (1+\varepsilon)m^* + \frac{1}{\varepsilon}\ln n$$

Scegliendo $\varepsilon = \sqrt{(\ln n)/T}$ si ottiene il bound ottimo $O(\sqrt{T \ln n})$.

## Connessioni

- Paradigma online learning: [[Apprendimento statistico]], [[Discesa del gradiente]]
- Randomizzazione: [[Metodi Monte Carlo]]
- Clustering e LSH: [[Locality Sensitive Hashing]]
- Discusso in: [[Algoritmi e Complessità]]

## Fonti

- [[Dispense Algoritmi — Galletti]] (§4, pp. 23-28)
