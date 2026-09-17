---
tipo: concetto
titolo: Algoritmo di Dijkstra
tag: [algoritmi, grafi, shortest-path, greedy]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Algoritmo di Dijkstra

Algoritmo **greedy** per il problema del **shortest path** su grafi pesati con **pesi non negativi**. Trovare `d(s, v)` per ogni nodo `v` a partire da una sorgente `s`.

## Algoritmo

```
Dijkstra(G, s):
  d[s] = 0; d[v] = +∞ per v ≠ s
  S = {s}
  while S ≠ V:
    u = argmin{ d'(v) : v ∉ S }   // d'(v) = min_{w∈S} {d[w] + c(w,v)}
    d[u] = d'(u)
    S = S ∪ {u}
```

A ogni passo estrae il nodo con distanza stimata minima tra quelli non ancora esplorati.

## Complessità

- **Implementazione naive**: O(n²) (ricerca del minimo in O(n) per n nodi)
- **Con min-heap**: `O(m log n)` — ogni arco aggiorna al più una distanza, e l'aggiornamento nel heap costa `O(log n)`

Operazioni heap:
- `FIND-MIN`: O(1)
- `DELETE-MIN`: O(log n)
- `DECREASE-KEY`: O(log n)

## Correttezza

**Teorema**: con pesi `c(e) ≥ 0`, Dijkstra restituisce le distanze minime esatte.

**Dimostrazione per induzione** su `|S|`: quando si aggiunge `u` ad `S`, non esiste cammino più corto che passi per nodi in `V\S` (perché tutti i pesi futuri sono non negativi, quindi il cammino non può migliorare uscendo da `S`).

## Limite: archi negativi

Dijkstra **fallisce** con archi negativi: potrebbe non terminare o dare risultati errati. Per archi negativi: [[Algoritmo di Bellman-Ford]].

## Esempio

Sul grafo della dispensa (nodo `t` come sorgente): `d = [1_a, 2_b, 3_c, e+2_d, 4_e, ∞_f, 0_t]`.

## Connessione con i corsi

- [[Tecniche di Programmazione]]: §6.3.1, con dimostrazione di correttezza e analisi complessità.
- [[Heap Sort]]: il min-heap usato in Dijkstra è la stessa struttura del max-heap in Heap Sort.

## Persone

[[Dijkstra, Edsger]] (1959) — algoritmo pubblicato su *Numerische Mathematik*.

## Fonti

- [[Dispense TecProg — Galletti]] (§6.3.1, pp. 40-42)
