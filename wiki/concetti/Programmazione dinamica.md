---
tipo: concetto
titolo: Programmazione dinamica
tag: [algoritmi, paradigmi, ottimizzazione]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Programmazione dinamica

La **programmazione dinamica** (DP) risolve problemi con **sottostruttura ottimale** e **sottoproblemi sovrapposti**: invece di ricalcolare, memorizza le soluzioni ai sottoproblemi (**memoization** o **bottom-up**).

**Differenza rispetto a [[Divide et Impera]]**: in D&C i sottoproblemi sono disgiunti; in DP si sovrappongono.

## Principio

1. Definire la **funzione di valore** `opt(i)` come soluzione ottima per il sottoproblema di taglia `i`
2. Trovare la **ricorrenza** che esprime `opt(i)` in termini di sottoproblemi minori
3. Risolvere bottom-up (tabella) o top-down (memoization)

## Esempi fondamentali

### Fibonacci

`f(n) = f(n-1) + f(n-2)`: ricorsione naive `O(2ⁿ)`, DP `O(n)` (tenendo solo gli ultimi due valori).

### Interval Scheduling

**Problema**: dati `n` job con intervalli `[sᵢ, fᵢ]` e pesi `wᵢ`, trovare il sottoinsieme di job compatibili (non sovrapposti) con peso massimo.

Definisco `p(j)` = indice del job più a destra compatibile con `j`. Ricorrenza:

$$
OPT(j) = \max\{w_j + OPT(p(j)),\; OPT(j-1)\}
$$

Complessità: `O(n log n)` (ordinamento + ricerca binaria per `p(j)`).

### Knapsack Problem

**Zaino 0/1**: dati oggetti con peso `wᵢ` e valore `vᵢ`, capacità `W`. Ricorrenza:

$$
OPT(i, w) = \max\{OPT(i-1, w),\; v_i + OPT(i-1, w-w_i)\}
$$

Complessità: `O(nW)` — **pseudopolinomiale** (dipende dal valore di `W`, non solo dalla sua rappresentazione).

### Bellman-Ford (shortest path con DP)

`φ(i, v)` = costo cammino minimo da `v` a `t` con ≤ `i` archi. Vedi [[Algoritmo di Bellman-Ford]].

## Caratteristiche necessarie

- **Sottostruttura ottimale**: la soluzione ottima del problema contiene le soluzioni ottime dei sottoproblemi.
- **Sottoproblemi sovrapposti**: gli stessi sottoproblemi vengono risolti più volte (altrimenti D&C è sufficiente).

## Connessione con i corsi

- [[Tecniche di Programmazione]]: §5, esempi Fibonacci, Interval Scheduling, KnapSack.
- [[Processi Stocastici]]: l'equazione di Bellman in teoria del controllo è la DP stocastica.

## Fonti

- [[Dispense TecProg — Galletti]] (§5, pp. 32-36)
