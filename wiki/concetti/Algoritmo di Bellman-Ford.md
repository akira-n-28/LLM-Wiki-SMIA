---
tipo: concetto
titolo: Algoritmo di Bellman-Ford
tag: [algoritmi, grafi, shortest-path, programmazione-dinamica]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Algoritmo di Bellman-Ford

Algoritmo di **programmazione dinamica** per il shortest path che gestisce **archi con pesi negativi** (ma non cicli negativi).

## Idea

**Lemma**: in un grafo `G` senza cicli negativi, il cammino minimo tra due nodi usa al più `n-1` archi.

Definisco la funzione DP:

$$
\varphi(i, v) = \text{costo del cammino minimo da } v \text{ a } t \text{ con al più } i \text{ archi}
$$

**Ricorrenza**:

$$
\varphi(i, v) = \min\left\{ \varphi(i-1, v),\quad \min_{(v,u) \in E}\left[\varphi(i-1, u) + c(v, u)\right] \right\}
$$

**Condizioni iniziali**: `φ(0, t) = 0`, `φ(0, v) = +∞` per `v ≠ t`, `φ(i, t) = 0` per ogni `i`.

## Complessità

- **Temporale**: `O(n · m)` — `n` iterazioni, `m` archi per iterazione. Con `m ≤ n²`: `O(n³)`.
- **Spaziale**: `O(n²)` per la tabella `φ(i,v)`; riducibile a `O(n)` tenendo solo due righe consecutive (ma si perde la capacità di ricostruire il cammino).

## Rilevamento di cicli negativi

Se `φ(n, v) < φ(n-1, v)` per qualche `v`, allora esiste un **ciclo negativo**: il cammino minimo non è ben definito.

## Confronto con Dijkstra

| | Dijkstra | Bellman-Ford |
|-|---------|-------------|
| Pesi negativi | No | Sì |
| Cicli negativi | — | Rilevati |
| Complessità | O(m log n) | O(nm) |
| Paradigma | Greedy | DP |

## Connessione con i corsi

- [[Tecniche di Programmazione]]: §6.4, come caso applicativo di [[Programmazione dinamica]] ai grafi.
- [[Programmazione dinamica]]: φ(i,v) è la quintessenza della ricorrenza DP.

## Persone

[[Bellman, Richard]] e [[Ford, Lester]] (indipendentemente, anni '50-'60).

## Fonti

- [[Dispense TecProg — Galletti]] (§6.4, pp. 42-43)
