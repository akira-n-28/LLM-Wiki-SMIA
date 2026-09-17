---
tipo: concetto
titolo: Minimum Spanning Tree
tag: [algoritmi, grafi, greedy]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Minimum Spanning Tree (MST)

Dato un grafo `G = (V, E)` **connesso, indiretto** con funzione di peso `c: E → ℝ` (pesi distinti), un **Minimum Spanning Tree** è un sottoinsieme `T ⊆ E` tale che:
- `T` connette tutti i nodi (spanning tree)
- `Σ_{e∈T} c(e)` è minimale

Un MST ha esattamente `n-1` archi.

## Teorema fondamentale (cut property)

Sia `S ⊂ V` non banale e sia `e ∈ ∂(S)` l'arco di peso minimo che attraversa il taglio `∂(S)`. Allora `e ∈ T*` per ogni MST `T*`.

**Dimostrazione per scambio**: se `e ∉ T*`, esiste un altro arco `e'` nel taglio che è in `T*`. Sostituendo `e'` con `e` si ottiene un albero con costo minore — contraddizione.

## Algoritmo di Prim

Greedy che cresce l'MST da un nodo arbitrario, aggiungendo a ogni passo l'arco di peso minimo che esce dall'insieme corrente `S`:

```
S = {v_arbitrario}; T = {}
while S ≠ V:
  e = argmin{ c(e) : e ∈ ∂(S) }
  T = T ∪ {e}; S = S ∪ {endpoint di e in V\S}
```

**Complessità**: `O(nm)` naive; `O(m log n)` con min-heap (analogo a Dijkstra).

## Algoritmo di Kruskal

Greedy che ordina tutti gli archi per peso crescente e aggiunge un arco se non forma un ciclo:

```
Ordina E per peso; T = {}
for e in E:
  if T ∪ {e} non ha cicli:
    T = T ∪ {e}
```

**Complessità**: `O(m log m)` per l'ordinamento + `O(m log n)` per le operazioni Union-Find.

### Union-Find

Struttura dati per verificare in tempo quasi-costante se due nodi appartengono alla stessa componente connessa:
- `find(v)`: restituisce il rappresentante della componente di `v`
- `union(u, v)`: unisce le componenti di `u` e `v`

**Ottimizzazione**: sempre unire la componente più piccola alla più grande. Costo di `k` union consecutive: `O(k log k)` — ogni nodo cambia componente al più `O(log k)` volte perché la nuova componente è almeno il doppio.

## Confronto Prim vs Kruskal

| | Prim | Kruskal |
|-|------|---------|
| Struttura | Cresce un albero | Cresce una foresta |
| Buono per | Grafi densi | Grafi sparsi |
| Complessità (con heap/UF) | O(m log n) | O(m log n) |

## Connessione con i corsi

- [[Tecniche di Programmazione]]: §6.5, con dimostrazione di correttezza tramite cut property.
- [[BFS e DFS]]: Prim è strutturalmente simile a Dijkstra (greedy su costo arco vs distanza).

## Persone

[[Prim, Robert]] (1957) e [[Kruskal, Joseph]] (1956).

## Fonti

- [[Dispense TecProg — Galletti]] (§6.5, pp. 43-46)
