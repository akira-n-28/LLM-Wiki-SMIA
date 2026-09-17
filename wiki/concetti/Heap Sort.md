---
tipo: concetto
titolo: Heap Sort
tag: [algoritmi, ordinamento, strutture-dati]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Heap Sort

Heap Sort è un algoritmo di ordinamento in-place basato sulla struttura dati **max-heap**: un albero binario completo in cui ogni nodo è ≥ dei suoi figli.

## Struttura heap come array

Un heap di `n` elementi è rappresentato come array con indicizzazione 1-based:
- `parent(i) = ⌊i/2⌋`
- `left(i) = 2i`
- `right(i) = 2i+1`

**Proprietà max-heap**: `A[parent(i)] ≥ A[i]` per ogni `i`.

## Algoritmi componenti

**Max-Heapify(A, i)** — ripristina la proprietà heap verso il basso: `O(log n)`.

**Build-Max-Heap(A)** — costruisce un max-heap da un array non ordinato partendo dalle foglie:

$$
T_{\text{build}} \leq \sum_{i=1}^{\lfloor n/2 \rfloor} \log\frac{n}{i} \leq \int_1^{n/2} \log\frac{n}{x}\,dx \leq \frac{3n}{2} \in O(n)
$$

**Heap-Sort(A)**:
1. `Build-Max-Heap(A)` — `O(n)`
2. Per `i = n` downto `2`: scambia `A[1]` con `A[i]`, decrementa heap-size, `Max-Heapify(A, 1)` — `O(log n)` per `n-1` iterazioni

Totale: `O(n) + O(n log n) = O(n log n)` nel caso peggiore.

## Confronto con gli altri algoritmi

| | Merge Sort | Quick Sort | Heap Sort |
|-|-----------|-----------|-----------|
| Caso peggiore | Θ(n log n) | Θ(n²) | Θ(n log n) |
| In-place | No | Sì | Sì |
| Stabile | Sì | No | No |
| Spazio | O(n) | O(log n) | O(1) |

Heap Sort è l'unico algoritmo O(n log n) nel caso peggiore **e** O(1) di spazio aggiuntivo.

## Connessione con i corsi

- [[Tecniche di Programmazione]]: §4.6, con dimostrazione di correttezza Build-Max-Heap per induzione.
- [[Algoritmo di Dijkstra]]: usa un min-heap per ottenere O(m log n) anziché O(nm).

## Fonti

- [[Dispense TecProg — Galletti]] (§4.6, pp. 27-31)
