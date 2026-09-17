---
tipo: moc
titolo: MOC — Algoritmi
cluster: algoritmi
ultima-modifica: 2026-05-06
---

# MOC — Algoritmi

**Map of Content** del cluster `algoritmi` (41 concetti). Pagina di **navigazione tematica** per studio.

> **Corsi coinvolti:** [[Tecniche di Programmazione]] (Trappolini + Fusco, 24/25), [[Algoritmi e Complessità]] (Panconesi + Chierichetti, 24/25), [[Fondamenti di Intelligenza Artificiale]] (Baccini, 24/25).

---

## 🎯 Da dove iniziare

Se è la prima volta:

1. [[Complessità computazionale]] — Big-O, Omega, Theta
2. [[Strutture dati]] — array, lista, stack, queue
3. [[Divide et Impera]] — paradigma centrale
4. [[Master Theorem]] — analisi delle ricorrenze
5. [[Merge Sort]] — esempio canonico (O(n log n))
6. [[BFS e DFS]] — visita di grafi (O(m))

## 📊 Complessità & paradigmi

**Misure:**
- [[Complessità computazionale]] — Big-O, Omega, Theta, o-piccolo
- [[Master Theorem]] — $T(n) = aT(n/b) + f(n)$

**Paradigmi:**
- [[Divide et Impera]] — Merge Sort, FFT, Karatsuba
- [[Programmazione dinamica]] — bottom-up, memoization
- [[Algoritmo greedy]] — "stays ahead", scambio

## 📑 Strutture dati

- [[Strutture dati]] — overview
- [[Tabella hash]] — accesso O(1) atteso
- [[Albero binario di ricerca]] (BST) — ricerca/inserimento O(log n)
- *(Heap implicita in [[Heap Sort]])*

## 🔢 Sorting & selection

- [[Merge Sort]] — divide et impera, O(n log n)
- [[Quick Sort]] — pivot, atteso O(n log n)
- [[Heap Sort]] — Max-Heap, O(n log n)
- [[Quick Select]] — selezione k-esimo, O(n) atteso

## ➗ Aritmetica veloce

- [[Algoritmo di Karatsuba]] — moltiplicazione O(n^{1.585})
- [[Algoritmo di Strassen]] — matrici O(n^{2.807})

## 📈 DP & Greedy

**Problemi DP:**
- [[Weighted Interval Scheduling]] — equazione di Bellman
- [[Knapsack]] — φ(i,b), pseudo-polinomiale

**Problemi Greedy:**
- [[Interval Scheduling]] — earliest finish
- [[Interval Partitioning]] — depth, heap O(n log n)
- [[Algoritmo di Huffman]] — codici prefix-free

## 🌐 Grafi

**Definizioni:**
- [[Grafo]] — V, E, rappresentazioni

**Visita:**
- [[BFS e DFS]] — O(m), connessione, sort topologico

**Cammini minimi:**
- [[Algoritmo di Dijkstra]] — pesi non negativi, O(m log n)
- [[Algoritmo di Bellman-Ford]] — pesi negativi, O(nm)

**Spanning tree:**
- [[Minimum Spanning Tree]] — definizione, cut property
- [[Algoritmo di Prim]] — vertex-by-vertex
- [[Algoritmo di Kruskal]] — edge-by-edge, Union-Find

## 🧠 Logica & AI

**Agenti & ricerca:**
- [[Agente intelligente]] — PEAS, tipi
- [[Ricerca A*]] — $f(n) = g(n) + h(n)$, ammissibilità

**Logica proposizionale:**
- [[Logica proposizionale]] — sintassi, semantica
- [[Conseguenza logica]] — model checking
- [[Alberi di Beth]] — refutazione automatica
- [[Sistema Hilbertiano]] — derivazione, correttezza/completezza

**Risoluzione:**
- [[Risoluzione (RES)]] — CNF, clausola vuota
- [[Clausole di Horn]] — definite, fatti, regole
- [[Concatenazione in avanti e all'indietro]] — PL-CA

**Logica del primo ordine:**
- [[Logica del primo ordine]] — quantificatori, unificazione

## 🏆 Algoritmi specifici notevoli

- [[Stable Matching]] — Gale-Shapley, $O(n^2)$
- [[Problema degli esperti]] — WM, Randomized WM
- [[Locality Sensitive Hashing]] — Jaccard, ricerca approssimata

## 🚫 NP-completezza & decidibilità

- [[NP-completezza]] — P/NP, riduzioni, SAT≤Clique≤IS≤VC≤Knapsack
- [[Macchina di Turing]] — definizione, Halting, decidibilità

## 🔗 Argomenti trasversali

- [[Grafi e ricerca]] — sintesi 5 corsi (TecProg/AlgComp/FondAI/ML/Processi)
- [[Ottimizzazione iterativa]] — algoritmi iterativi su problemi continui
- [[SVD e decomposizione spettrale]] — autovalori del Laplaciano per spectral graph theory

## 📚 Per esame

**TecProg (Trappolini + Fusco, 24/25):** sorting + DP + grafi → [[Tecniche di Programmazione]]
**AlgComp (Panconesi + Chierichetti, 24/25):** greedy + DP + NP + Turing → [[Algoritmi e Complessità]]
**FondAI (Baccini, 24/25):** A* + logica prop. + FOL + risoluzione → [[Fondamenti di Intelligenza Artificiale]]
