---
tipo: concetto
titolo: Albero binario di ricerca
tag: [algoritmi, strutture-dati, alberi]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Albero binario di ricerca (BST)

Un **albero binario di ricerca** è un albero binario in cui per ogni nodo `v`:
- tutti i valori nel sottoalbero sinistro sono **< v**
- tutti i valori nel sottoalbero destro sono **≥ v**

## Operazioni

| Operazione | Complessità |
|------------|-------------|
| Search | O(h) |
| Insert | O(h) |
| Delete | O(h) |
| Min/Max | O(h) |
| Successor/Predecessor | O(h) |

dove `h` è l'**altezza** dell'albero. Per un BST bilanciato: `h = O(log n)`. Per un BST degenerato (input ordinato): `h = O(n)`.

## Interval Sorting con BST

**Problema**: dati `n` intervalli `[aᵢ, bᵢ]`, trovare il massimo numero di intervalli non sovrapposti. Algoritmo greedy:
1. Ordina per `bᵢ` crescente
2. Seleziona l'intervallo con `bᵢ` minimo compatibile con gli intervalli già selezionati

Il BST supporta l'operazione di trovare il successore in O(log n), utile in varianti del problema.

## BST bilanciati

Alberi AVL, Red-Black, B-tree mantengono `h = O(log n)` garantendo operazioni O(log n) anche nel caso peggiore.

## Connessione con i corsi

- [[Tecniche di Programmazione]]: §4.1-4.2, BST come struttura per ordinamento e ricerca.
- [[Heap Sort]]: il max-heap è una struttura ad albero con proprietà diverse (heap property vs BST property).

## Fonti

- [[Dispense TecProg — Galletti]] (§4.1-4.2, pp. 21-24)
