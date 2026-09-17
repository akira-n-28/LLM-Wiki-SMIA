---
tipo: concetto
titolo: Complessità computazionale
tag: [algoritmi, complessità, fondamenti]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Complessità computazionale

La **complessità** di un algoritmo misura le risorse (tempo, spazio) necessarie in funzione della dimensione dell'input `n`. Si usa il modello **Random Access Machine (RAM)**: ogni operazione elementare ha costo costante, le operazioni sono sequenziali.

## Notazioni asintotiche

| Notazione | Significato | Formale |
|-----------|-------------|---------|
| `f(n) ∈ O(g(n))` | f cresce **al più** come g | ∃c>0, n₀: f(n) ≤ c·g(n) ∀n≥n₀ |
| `f(n) ∈ Ω(g(n))` | f cresce **almeno** come g | ∃c>0, n₀: f(n) ≥ c·g(n) ∀n≥n₀ |
| `f(n) ∈ Θ(g(n))` | f cresce **esattamente** come g | f ∈ O(g) e f ∈ Ω(g) |

`Θ` è il bound stretto; `O` e `Ω` sono bound asintotici uno-sided.

## Casi di analisi

- **Best case**: input favorevole (es. array già ordinato per Insertion Sort → Θ(n))
- **Worst case**: input avverso (es. array inverso per Insertion Sort → Θ(n²))
- **Average case** / **caso atteso**: media su tutti gli input, o su scelte randomizzate

## Complessità di algoritmi fondamentali

| Algoritmo | Best | Average | Worst | Spazio |
|-----------|------|---------|-------|--------|
| Insertion Sort | Θ(n) | Θ(n²) | Θ(n²) | O(1) |
| Merge Sort | Θ(n log n) | Θ(n log n) | Θ(n log n) | O(n) |
| Quick Sort | Θ(n log n) | Θ(n log n) | Θ(n²) | O(log n) |
| Heap Sort | Θ(n log n) | Θ(n log n) | Θ(n log n) | O(1) |
| Binary Search | O(1) | O(log n) | O(log n) | O(1) |
| Dijkstra (heap) | — | — | O(m log n) | O(n) |
| Bellman-Ford | — | — | O(n³) | O(n²) |

## Lower bound per l'ordinamento

**Teorema**: qualunque algoritmo di ordinamento basato su confronti richiede `Ω(n log n)` confronti nel caso peggiore.

**Dimostrazione via albero di decisione**: un albero binario con `n!` foglie ha altezza ≥ `log₂(n!) ∈ Ω(n log n)` per la formula di Stirling.

## Invariante di ciclo

Strumento per dimostrare la **correttezza** di un algoritmo iterativo:
1. **Inizializzazione**: vera prima della prima iterazione
2. **Mantenimento**: se vera all'inizio dell'iterazione `i`, è vera all'inizio dell'iterazione `i+1`
3. **Terminazione**: alla fine del ciclo implica la correttezza dell'output

## Classi di complessità (cenni)

- **P**: problemi decisionali risolvibili in tempo polinomiale.
- **NP**: soluzioni "sì" verificabili in tempo polinomiale.
- **NP-completo**: in NP e ogni problema NP si riduce a esso.

Trattamento approfondito (riduzioni, SAT, Clique, IS, VC, Knapsack, Macchina di Turing): [[NP-completezza]], [[Macchina di Turing]].

## Connessioni

- [[Tecniche di Programmazione]]: §1-2, analisi algoritmi di ordinamento.
- [[NP-completezza]]: P vs NP, riduzioni, catena SAT≤Clique≤IS≤VC≤Knapsack.
- [[Macchina di Turing]]: modello formale, decidibilità, problema dell'Halting.
- [[Matematica per il Machine Learning]]: scalabilità algoritmi ML.

## Fonti

- [[Dispense TecProg — Galletti]] (§1-2, pp. 3-15)
- [[Dispense Algoritmi — Galletti]] (§1.2, §5-7, pp. 6-8, 29-44)
