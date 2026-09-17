---
tipo: fonte
titolo: Dispense TecProg — Galletti
autori: [Marco Galletti]
docente-corso: Giovanni Trappolini, Federico Fusco
anno-accademico: 2024/2025
data-ingest: 2026-05-04
file-raw: raw/appunti/tecniche-programmazione.pdf
pagine: 50
ultima-modifica: 2026-05-04
tag: [informatica, algoritmi, strutture-dati]
---

# Dispense di Tecniche di Programmazione — Galletti

**Riferimento file raw:** `raw/appunti/tecniche-programmazione.pdf`
**Corso:** [[Tecniche di Programmazione]] (prof. Giovanni Trappolini + Federico Fusco, A.A. 2024/2025, SMIA Sapienza)
**Autore appunti:** [[Galletti, Marco]]

## Riassunto in 5 punti

1. **Notazioni asintotiche**: Big-O (upper bound), Omega (lower bound), Theta (tight), o-piccolo, omega-piccolo; modello RAM; analisi worst-case/average-case.
2. **Divide et Impera e ordinamento**: Merge Sort O(n log n), dimostrazione lower bound Ω(n log n) per comparison sort (albero di decisione); Quick Sort con analisi probabilistica del caso atteso.
3. **Strutture dati**: array, stack, queue, linked list, direct address table, hash table (concatenamento, h(k)=k mod m).
4. **Programmazione dinamica**: Fibonacci iterativo; Interval Scheduling greedy (Greedy Stays Ahead); Weighted Interval Scheduling (equazione di Bellman); Knapsack (φ(i,b)).
5. **Grafi**: BFS e DFS O(m); Dijkstra O(m log n) con min-heap; Bellman-Ford O(n³) per archi negativi; MST con Prim e Kruskal; Karatsuba e Strassen per moltiplicazione; Master Theorem.

## Argomenti trattati

### §1 Introduzione agli algoritmi (pp. 3-7)
- Insertion Sort — invariante di ciclo, analisi del costo (best/worst)
- Binary Search — O(log n), dimostrazione ricorsiva
- Modello RAM

### §2 Notazioni asintotiche (pp. 8-15)
- [[Complessità computazionale]] — Big-O, Omega, Theta, o, omega (definizioni formali)
- [[Divide et Impera]]
- [[Merge Sort]] — analisi T(n)=O(n log n); lower bound Ω(n log n)
- 2-Sum Problem — O(n) con hash map

### §3 Strutture dati (pp. 16-20)
- Array, Lista, Matrici, Stack (LIFO), Queue (FIFO), Linked List
- [[Tabella hash]] — collisioni, concatenamento

### §4 Algoritmi di ordinamento (pp. 20-31)
- [[Albero binario di ricerca]] (BST) — inorder walk, search, insert, remove
- [[Quick Sort]] — analisi probabilistica caso atteso O(n log n)
- [[Heap Sort]] — Max-Heap, Build-Max-Heap O(n), Heap-Sort O(n log n)
- [[Quick Select]] — O(n) atteso

### §5 Programmazione Dinamica (pp. 32-36)
- Fibonacci dinamico
- [[Interval Scheduling]] greedy — lemma "Greedy Stays Ahead"
- [[Weighted Interval Scheduling]] — equazione di Bellman φ(n)=max{w(n)+φ(p(n)), φ(n-1)}
- [[Programmazione dinamica]] — φ(i,b), O(nB)

### §6 Grafi (pp. 36-46)
- Definizioni: grafi diretti/indiretti, pesati, connessione, cicli
- Rappresentazioni: lista adiacenza, matrice adiacenza
- [[BFS e DFS]] — O(m)
- [[Algoritmo di Dijkstra]] — O(m log n) con coda di priorità
- [[Algoritmo di Bellman-Ford]] — O(n³), archi negativi
- [[Minimum Spanning Tree]] — [[Algoritmo di Prim]] O(m log n), [[Algoritmo di Kruskal]]

### §7 Algoritmi di moltiplicazione e MT (pp. 47-50)
- [[Algoritmo di Karatsuba]] — O(n^log₂3) ≈ O(n^1.585)
- [[Algoritmo di Strassen]] — moltiplicazione matriciale O(n^log₂7) ≈ O(n^2.807)
- [[Master Theorem]] — T(n)=aT(n/b)+f(n)

## Citazioni chiave

> "Ogni algoritmo di ordinamento basato su confronti ha un running time nel caso peggiore Ω(n log n). [Dimostrazione via albero di decisione con n! foglie.]" — Teorema 3, §2

> "R-QuickSort ha complessità attesa O(n log n) con probabilità 1 - 1/n." — Teorema 4, §4

## Note di lettura

- Le dispense sono orientate alla **dimostrazione formale**: quasi ogni complessità è dimostrata (non solo enunciata).
- La struttura algoritmo → pseudocodice → Python code → dimostrazione è ripetuta sistematicamente.
- Il capitolo sui grafi (§6) è il più denso (~10 pp.) e copre quasi tutto ciò che serve per applicazioni ML (Dijkstra, MST).

## Pagine wiki aggiornate da questa ingest

**Primo ingest (2026-05-04, profondo):**
- [[Tecniche di Programmazione]] — corso creato (🟢).
- Create: [[Complessità computazionale]], [[Divide et Impera]], [[Merge Sort]], [[Tabella hash]], [[Albero binario di ricerca]], [[Quick Sort]], [[Heap Sort]], [[Programmazione dinamica]], [[BFS e DFS]], [[Algoritmo di Dijkstra]], [[Algoritmo di Bellman-Ford]], [[Minimum Spanning Tree]], [[Master Theorem]]

## Fonti
- `raw/appunti/tecniche-programmazione.pdf`
