---
tipo: concetto
titolo: Merge Sort
tag: [algoritmi, ordinamento, divide-et-impera]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Merge Sort

Merge Sort è un algoritmo di ordinamento [[Divide et Impera]] che divide l'array a metà, ordina ricorsivamente ciascuna metà, e fonde le due metà ordinate.

## Ricorrenza e complessità

$$
T(n) = 2T\!\left(\frac{n}{2}\right) + \Theta(n) \xrightarrow{\text{MT caso 2}} T(n) \in \Theta(n \log n)
$$

Il merge di due array ordinati di taglia `n/2` ciascuno costa `Θ(n)` (scansione lineare).

## Complessità: confronto con Quick Sort

| Proprietà | Merge Sort | Quick Sort |
|-----------|-----------|------------|
| Caso peggiore | Θ(n log n) | Θ(n²) |
| Caso medio | Θ(n log n) | Θ(n log n) |
| Spazio aggiuntivo | O(n) | O(log n) |
| Stabile | Sì | No |
| In-place | No | Sì |

Merge Sort è preferibile quando la stabilità è richiesta o l'input può essere adversariale; Quick Sort in pratica è spesso più veloce per la locality of reference.

## Algoritmo

```
MergeSort(A, p, r):
  se p < r:
    q = (p + r) / 2
    MergeSort(A, p, q)
    MergeSort(A, q+1, r)
    Merge(A, p, q, r)
```

`Merge(A, p, q, r)` copia i due sottoarray in array ausiliari `L`, `R` e poi li fonde in `A[p..r]` con un confronto elemento per elemento.

## Lower bound per l'ordinamento

Qualunque algoritmo basato su confronti richiede `Ω(n log n)` confronti nel caso peggiore (dimostrazione via albero di decisione con `n!` foglie). Merge Sort raggiunge questo bound ed è quindi **ottimale**.

## Connessione con i corsi

- [[Tecniche di Programmazione]]: §2.4, primo esempio concreto di D&C con analisi via MT.
- [[Divide et Impera]]: caso paradigmatico del pattern divide-combina.

## Fonti

- [[Dispense TecProg — Galletti]] (§2.4, pp. 11-15)
