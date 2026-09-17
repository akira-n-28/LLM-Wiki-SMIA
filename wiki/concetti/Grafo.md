---
tipo: concetto
titolo: Grafo
tag: [algoritmi, grafi, strutture-dati]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Grafo

Un **grafo** `G = (V, E)` è composto da un insieme di **vertici** (nodi) `V` e un insieme di **archi** `E ⊆ V × V`. Con `n = |V|` e `m = |E|`.

## Tipologie

- **Diretto (orientato)**: gli archi hanno direzione `(u, v) ≠ (v, u)`
- **Indiretto**: gli archi sono non orientati `{u, v}`
- **Pesato**: ogni arco `e` ha un costo `c(e) ∈ ℝ`

## Rappresentazioni

| | Lista di adiacenza | Matrice di adiacenza |
|-|--------------------|----------------------|
| Spazio | O(n + m) | O(n²) |
| Verifica arco | O(deg(v)) | O(1) |
| Iterare vicini | O(deg(v)) | O(n) |
| Uso preferito | Grafi sparsi | Grafi densi |

## Concetti fondamentali

- **Cammino**: sequenza di nodi `v₁, v₂, …, vₖ` dove `(vᵢ, vᵢ₊₁) ∈ E`
- **Ciclo**: cammino che parte e termina nello stesso nodo
- **Albero**: grafo connesso aciclico (ha `n-1` archi)
- **Connesso**: esiste un cammino tra ogni coppia di nodi
- **Componente connessa**: sottoinsieme massimale di nodi mutualmente raggiungibili
- **Grado `deg(v)`**: numero di archi incidenti in `v`
- **Frontiera `∂(S)`**: archi con un estremo in `S` e l'altro in `V\S`

## Algoritmi principali

- Visita: [[BFS e DFS]]
- Cammini minimi: [[Algoritmo di Dijkstra]], [[Algoritmo di Bellman-Ford]]
- Albero di copertura minimo: [[Minimum Spanning Tree]]

## Connessione con i corsi

- [[Tecniche di Programmazione]]: §6, argomento centrale della seconda metà del corso.
- [[Processi Stocastici]]: [[Catena di Markov]] è un grafo orientato con probabilità di transizione sugli archi.

## Fonti

- [[Dispense TecProg — Galletti]] (§6.1, pp. 36-38)
