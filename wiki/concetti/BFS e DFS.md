---
tipo: concetto
titolo: BFS e DFS
tag: [algoritmi, grafi, visite]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# BFS e DFS

**BFS** (Breadth-First Search) e **DFS** (Depth-First Search) sono i due algoritmi fondamentali per visitare tutti i nodi di un [[Grafo]].

## Rappresentazione dei grafi

**Lista di adiacenza**: per ogni nodo `v`, lista dei vicini. Spazio `O(n + m)`. Efficiente per grafi sparsi.

**Matrice di adiacenza**: `A[i][j] = 1` se esiste l'arco `(i,j)`. Spazio `O(n²)`. Efficiente per grafi densi, verifica arco in O(1).

Con `n = |V|`, `m = |E|`.

## BFS (Breadth-First Search)

Visita i nodi per livelli di distanza crescente dalla sorgente `s`. Usa una **coda** (FIFO).

```
BFS(G, s):
  inizializza d[s]=0, d[v]=∞ per v≠s
  Q = coda con solo s
  while Q non vuota:
    u = dequeue(Q)
    per ogni vicino v di u:
      se d[v] = ∞:
        d[v] = d[u] + 1
        enqueue(Q, v)
```

**Complessità**: `O(n + m)`.  
**Proprietà**: trova il **cammino più breve** (in numero di archi) in grafi non pesati.

## DFS (Depth-First Search)

Visita il più in profondità possibile prima di tornare indietro. Usa uno **stack** (LIFO) o ricorsione.

**Complessità**: `O(n + m)`.  
**Proprietà**: individua componenti connesse, ordine topologico, cicli, componenti fortemente connesse.

## Applicazioni

| Problema | Algoritmo |
|---------|-----------|
| Shortest path (non pesato) | BFS |
| Componenti connesse | BFS o DFS |
| Cicli | DFS |
| Ordine topologico | DFS |
| Shortest path (pesato, archi ≥0) | [[Algoritmo di Dijkstra]] |
| Shortest path (archi negativi) | [[Algoritmo di Bellman-Ford]] |
| Minimum Spanning Tree | [[Minimum Spanning Tree]] |

## Connessione con i corsi

- [[Tecniche di Programmazione]]: §6.1-6.2, base per tutti gli algoritmi su grafi.
- [[Catena di Markov]]: struttura di grafo orientato, raggiungibilità = comunicazione tra stati.

## Fonti

- [[Dispense TecProg — Galletti]] (§6.1-6.2, pp. 37-39)
