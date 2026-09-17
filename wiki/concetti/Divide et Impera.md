---
tipo: concetto
titolo: Divide et Impera
tag: [algoritmi, paradigmi, ricorrenze]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Divide et Impera

**Divide et Impera** (D&C) è un paradigma di progettazione algoritmica che risolve un problema suddividendolo in sottoproblemi più piccoli della stessa natura, risolvendo ciascuno ricorsivamente, e combinando le soluzioni.

Struttura generale:
1. **Divide**: suddividi l'input in `a` sottoproblemi di taglia `n/b`
2. **Conquer**: risolvi ogni sottoproblema ricorsivamente
3. **Combine**: unisci le soluzioni in tempo `f(n)`

La complessità si analizza con il [[Master Theorem]]: `T(n) = aT(n/b) + f(n)`.

## Esempi principali

### Merge Sort
Divide a metà, riordina ricorsivamente, poi merge in `O(n)`: `T(n) = 2T(n/2) + O(n)` → `O(n log n)`. Vedi [[Merge Sort]].

### Quick Sort (randomizzato)
Divide attorno a un pivot casuale: `E[T(n)] = O(n log n)`. Vedi [[Quick Sort]].

### Binary Search
Divide a metà, cerca in un lato: `T(n) = T(n/2) + O(1)` → `O(log n)`.

### Karatsuba (moltiplicazione di interi)
Moltiplica `n`-bit integers con 3 anziché 4 moltiplicazioni ricorsive:
- `x = 10^{n/2}·a + b`, `y = 10^{n/2}·c + d`
- `xy = 10^n·ac + 10^{n/2}·[(a+b)(c+d) - ac - bd] + bd`
- Solo 3 moltiplicazioni di taglia `n/2`: `T(n) = 3T(n/2) + O(n)` → `Θ(n^{log₂3}) ≈ Θ(n^{1.585})`

Vs. algoritmo ingenuo `O(n²)`.

### Strassen (moltiplicazione di matrici)
7 anziché 8 moltiplicazioni di sottomatrici `n/2 × n/2`: `T(n) = 7T(n/2) + O(n²)` → `Θ(n^{log₂7}) ≈ Θ(n^{2.807})`. Vedi [[Singular Value Decomposition]] per contesto ML.

### 2-Sum Problem
Dato un array ordinato di `n` interi e un target `k`, trovare due elementi che sommano a `k`. Binary search per ogni elemento: `O(n log n)`.

## Quando usare D&C

- Il problema ha **sottostruttura ricorsiva** (sottoproblemi della stessa forma)
- La divisione e combinazione costano meno della soluzione diretta
- I sottoproblemi sono **indipendenti** (se si sovrappongono, usare [[Programmazione dinamica]])

## Connessione con i corsi

- [[Tecniche di Programmazione]]: §2.3, §7 — paradigma principale per gli algoritmi del corso.
- [[Matematica per il Machine Learning]]: Strassen riduce la complessità della moltiplicazione matriciale, critica per reti neurali.

## Fonti

- [[Dispense TecProg — Galletti]] (§2.3, §7, pp. 11-15, 47-50)
