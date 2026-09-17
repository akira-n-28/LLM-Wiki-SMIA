---
tipo: concetto
titolo: Quick Select
tag: [algoritmi, selezione, cs, randomized]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-06
---

# Quick Select

Algoritmo per trovare il $k$-esimo elemento più piccolo in un array non ordinato, in $O(n)$ atteso.

## Algoritmo

Basato sulla stessa idea di [[Quick Sort]]:
1. Scegli un pivot (casuale o deterministico).
2. Partiziona l'array attorno al pivot.
3. Se l'indice del pivot è $k$: restituisci il pivot.
4. Se l'indice del pivot è $> k$: ricorri sulla parte sinistra.
5. Se l'indice del pivot è $< k$: ricorri sulla parte destra.

**Complessità:**
- Caso atteso (pivot casuale): $O(n)$.
- Caso peggiore: $O(n^2)$ (evitabile con Median of Medians → $O(n)$ nel caso peggiore).

## Connessioni

- Paradigma: [[Divide et Impera]]
- Correlato: [[Quick Sort]] (stessa partizione, diversa ricorsione)
- Complessità: [[Complessità computazionale]]
- Corso: [[Tecniche di Programmazione]]

## Fonti

- [[Dispense TecProg — Galletti]] (§4)
