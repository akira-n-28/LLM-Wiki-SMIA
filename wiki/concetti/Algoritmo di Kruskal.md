---
tipo: concetto
titolo: Algoritmo di Kruskal
tag: [algoritmi, grafi, cs, mst]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-06
---

# Algoritmo di Kruskal

Algoritmo greedy per il [[Minimum Spanning Tree]] (MST) di un grafo pesato.

## Algoritmo

1. Ordina tutti gli archi per peso crescente.
2. Per ogni arco (in ordine), aggiungilo all'MST se non crea un ciclo (usa Union-Find per verificare).
3. Termina quando l'MST ha $n-1$ archi.

**Complessità:** $O(m \log m)$ dove $m$ = numero di archi (domina l'ordinamento).

**Correttezza:** proprietà del taglio (cut property): l'arco di peso minimo che attraversa un taglio appartiene all'MST.

## Connessioni

- Problema: [[Minimum Spanning Tree]]
- Alternativa: [[Algoritmo di Prim]]
- Struttura dati: Union-Find (Disjoint Set Union)
- Corso: [[Tecniche di Programmazione]]

## Fonti

- [[Dispense TecProg — Galletti]] (§6)
