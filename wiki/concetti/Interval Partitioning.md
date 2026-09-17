---
tipo: concetto
titolo: Interval Partitioning
tag: [algoritmi, greedy, scheduling]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-05
---

# Interval Partitioning

## Problema

Dati $n$ intervalli, assegnarli a **risorse** (aule, processori, …) in modo che intervalli sovrapposti usino risorse diverse, minimizzando il numero di risorse.

## Profondità

$$\mathrm{Depth}(I) = \max_{t \in \mathbb{R}} |\{I_i \in I : t \in I_i\}|$$

È un lower bound: $\mathrm{Opt}(I) \geq \mathrm{Depth}(I)$ (al picco di profondità servono almeno $\mathrm{Depth}(I)$ risorse contemporaneamente).

## Algoritmo greedy

1. Calcola $d = \mathrm{Depth}(I)$.
2. Ordina per start time: $s_1 \leq s_2 \leq \cdots \leq s_n$.
3. Per ogni $j$: assegna un'etichetta libera (non usata da nessun intervallo attivo a $s_j$).

**Lemma:** l'algoritmo non fallisce mai (l'insieme $S_j$ degli intervalli attivi soddisfa $|S_j| \leq d-1$, quindi resta sempre almeno un'etichetta libera).

**Teorema:** l'algoritmo restituisce un assegnamento ottimo con $d$ risorse. Complessità: $O(n^2)$ naive; $O(n \log n)$ con due heap (occupied e available).

## Implementazione ottimizzata (Heap)

- `occupied_heap`: min-heap per $f_i$ degli intervalli attivi.
- `available_heap`: min-heap delle risorse libere.
- Ad ogni nuovo intervallo $j$: libera le risorse con $f_i \leq s_j$, poi assegna la risorsa con indice minimo.

## Connessioni

- Paradigma: [[Algoritmo greedy]]
- Problema analogo non pesato: [[Interval Scheduling]]
- Strutture dati: [[Heap Sort]] (priority queue)
- Discusso in: [[Algoritmi e Complessità]]

## Fonti

- [[Dispense Algoritmi — Galletti]] (§2.2, pp. 10-12)
