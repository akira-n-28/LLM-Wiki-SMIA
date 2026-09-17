---
tipo: corso
titolo: Tecniche di Programmazione
docente: Giovanni Trappolini, Federico Fusco
anno-accademico: 2024/2025
codice-breve: TecProg
ultima-modifica: 2026-05-04
tag: [informatica, algoritmi, smia]
---

# Tecniche di Programmazione

Corso di **Tecniche di Programmazione** tenuto dai proff. **[[Trappolini, Giovanni]]** (fino agli algoritmi di ordinamento) e **[[Fusco, Federico]]** nell'A.A. 2024/2025, corso di laurea SMIA, Sapienza. Dispense redatte da [[Galletti, Marco]].

## Programma

### 1. Introduzione agli algoritmi
1.1 Insertion Sort — invariante di ciclo, analisi del costo
1.2 Binary Search — T(n) = O(log n), dimostrazione ricorsiva
1.3 Modello RAM

### 2. Notazioni asintotiche
2.1 Big-O, Omega, Theta, o-piccolo, omega-piccolo — definizioni formali
2.2 [[Divide et Impera]] — paradigma ricorsivo
2.3 [[Merge Sort]] — T(n) = O(n log n), lower bound Ω(n log n) per comparison sort

### 3. Strutture dati
3.1 Array, Lista, Matrici
3.2 Pila (Stack — LIFO), Coda (Queue — FIFO)
3.3 Lista concatenata
3.4 [[Tabella hash]] — funzione di hash, gestione collisioni

### 4. Algoritmi di ordinamento
4.1 [[Albero binario di ricerca]] (BST) — inorder walk, search, insert, remove
4.2 [[Quick Sort]] — pivot, Partition, Randomized QS — caso atteso O(n log n)
4.3 [[Heap Sort]] — Max-Heap, Build-Max-Heap, Max-Heapify
4.4 [[Quick Select]] — complessità attesa O(n)

### 5. Programmazione Dinamica
5.1 Fibonacci dinamico — memoization vs ricorsione
5.2 [[Interval Scheduling]] — algoritmo greedy, "Greedy Stays Ahead"
5.3 [[Weighted Interval Scheduling]] — equazione di Bellman, backtracking
5.4 [[Knapsack|Problema dello zaino (Knapsack)]] — φ(i,b), O(nB)

### 6. Grafi
6.1 Definizioni — grafo diretto/indiretto/pesato, connessione
6.2 Rappresentazioni: lista archi, lista adiacenza, matrice adiacenza
6.3 [[BFS e DFS]] — O(m); connessione del grafo
6.4 [[Algoritmo di Dijkstra]] — shortest path, O(m log n) con min-heap
6.5 [[Algoritmo di Bellman-Ford]] — archi negativi, O(n³)
6.6 [[Minimum Spanning Tree]] — [[Algoritmo di Prim]], [[Algoritmo di Kruskal]]

### 7. Algoritmi di moltiplicazione e MT
7.1 [[Algoritmo di Karatsuba]] — moltiplicazione in O(n^1.585)
7.2 [[Algoritmo di Strassen]] — moltiplicazione di matrici in O(n^2.807)
7.3 [[Master Theorem]] — T(n) = aT(n/b) + f(n)

## Concetti centrali
- [[Complessità computazionale]] (Big-O, Omega, Theta)
- [[Divide et Impera]] — [[Merge Sort]] — lower bound Ω(n log n)
- [[Strutture dati]] — [[Tabella hash]] — [[Albero binario di ricerca]]
- [[Quick Sort]] — [[Heap Sort]]
- [[Programmazione dinamica]] — [[Interval Scheduling]] — [[Knapsack]]
- [[Grafo]] — [[BFS e DFS]] — [[Algoritmo di Dijkstra]] — [[Minimum Spanning Tree]]
- [[Master Theorem]]

## Fonti del corso
- [[Dispense TecProg — Galletti]] — dispense, 50 pp., ingerite in profondità (2026-05-04)

## Stato della wiki per questo corso
🟢 **Completo** — ingest profondo completato (2026-05-04). ~12 pagine concettuali create.

## Connessioni trasversali con altri corsi

| Concetto TecProg | Corso collegato |
|---|---|
| Complessità, Big-O | [[Algoritmi e Complessità]] (Panconesi) |
| Grafi, BFS/DFS | [[Fondamenti di Intelligenza Artificiale]] (ricerca su grafo) |
| Shortest path, MST | [[Ottimizzazione]] |
| Programmazione dinamica | [[Machine Learning]] (DP per sequenze) |
| Hash table | [[Gestione dei Dati]] |
