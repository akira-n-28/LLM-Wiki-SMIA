---
tipo: concetto
titolo: Algoritmo di Prim
tag: [algoritmi, grafi, cs, mst]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-06
---

# Algoritmo di Prim

Algoritmo greedy per il [[Minimum Spanning Tree]] (MST) di un grafo pesato, che cresce l'albero un vertice alla volta.

## Algoritmo

1. Inizia da un vertice arbitrario.
2. Ad ogni passo, aggiungi l'arco di peso minimo che connette un vertice già nell'albero a uno non ancora incluso.
3. Ripeti fino a includere tutti i vertici.

**Implementazione efficiente:** min-heap per trovare l'arco minimo → $O(m \log n)$.

**Correttezza:** proprietà del taglio: l'arco minimo che esce dall'insieme corrente appartiene all'MST.

## Connessioni

- Problema: [[Minimum Spanning Tree]]
- Alternativa: [[Algoritmo di Kruskal]]
- Analogo a: [[Algoritmo di Dijkstra]] (stessa struttura, diversa funzione di priorità)
- Persona: [[Prim, Robert]]
- Corso: [[Tecniche di Programmazione]]

## Fonti

- [[Dispense TecProg — Galletti]] (§6)
