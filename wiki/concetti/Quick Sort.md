---
tipo: concetto
titolo: Quick Sort
tag: [algoritmi, ordinamento, randomizzato]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Quick Sort

Quick Sort è un algoritmo di ordinamento in-place basato su un **pivot**: partiziona l'array attorno al pivot (elementi minori a sinistra, maggiori a destra) e ordina ricorsivamente le due parti.

## Versione randomizzata (R-QuickSort)

Il pivot viene scelto **uniformemente a caso** tra gli elementi: evita il caso peggiore su input avversi (es. array già ordinato con pivot fisso all'ultimo elemento).

## Analisi del caso atteso: O(n log n)

Definisco la variabile indicatrice `Xᵢⱼ = 1` se gli elementi `Zᵢ` e `Zⱼ` (i-esimo e j-esimo dell'array ordinato) vengono confrontati. Due elementi si confrontano solo se uno dei due è il primo pivot scelto nell'intervallo `[i, j]`:

$$
P(X_{ij} = 1) = \frac{2}{j - i + 1}
$$

Il numero totale atteso di confronti è:

$$
E[X] = \sum_{i=1}^{n-1}\sum_{j=i+1}^{n} \frac{2}{j-i+1} = \sum_{i=1}^{n-1} \sum_{k=1}^{n-i} \frac{2}{k+1} \leq \sum_{i=1}^{n-1} O(\log n) = O(n \log n)
$$

**Con probabilità `1 - 1/n`, R-QuickSort impiega O(n log n).**

## Quick Select

Variante che trova il k-esimo elemento più piccolo (senza ordinare tutto): complessità attesa `O(n)`, dimostrata tramite analisi per gruppi Gⱼ con `|Sₜ| ≤ (3/4)ʲn`.

## Complessità spaziale

O(log n) in media per lo stack delle chiamate ricorsive; O(n) nel caso peggiore (partizione sempre sbilanciata).

## Confronto con Merge Sort

→ Vedi [[Merge Sort]] per la tabella di confronto completa.

## Connessione con i corsi

- [[Tecniche di Programmazione]]: §4.3-4.4, analisi via indicatori + linearità dell'attesa.
- [[Valore atteso]]: la dimostrazione usa la linearità di E[·] in modo fondamentale.

## Fonti

- [[Dispense TecProg — Galletti]] (§4.3-4.4, pp. 24-27)
