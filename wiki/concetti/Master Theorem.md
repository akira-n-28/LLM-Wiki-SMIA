---
tipo: concetto
titolo: Master Theorem
tag: [algoritmi, complessità, ricorrenze]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Master Theorem

Il Master Theorem fornisce la soluzione asintotica per ricorrenze della forma:

$$
T(n) = aT\!\left(\frac{n}{b}\right) + f(n), \quad a \geq 1,\; b > 1
$$

dove `a` = numero di sottoproblemi, `b` = fattore di riduzione, `f(n)` = lavoro extra.

## I tre casi

Confronta `f(n)` con `n^{log_b a}` (la complessità del caso ricorsivo puro):

| Caso | Condizione | Risultato |
|------|-----------|-----------|
| 1 | `f(n) ∈ O(n^{log_b a - ε})` per qualche `ε > 0` | `T(n) ∈ Θ(n^{log_b a})` |
| 2 | `f(n) ∈ Θ(n^{log_b a})` | `T(n) ∈ Θ(n^{log_b a} · log n)` |
| 3 | `f(n) ∈ Ω(n^{log_b a + ε})` e `a·f(n/b) ≤ k·f(n)` per `k<1` | `T(n) ∈ Θ(f(n))` |

**Caso 1**: il costo domina nel layer foglie → l'albero di ricorsione ha costo totale Θ(n^{log_b a}).  
**Caso 2**: costo bilanciato a ogni livello → `log n` livelli, tutti con stesso peso.  
**Caso 3**: il costo domina alla radice → `f(n)` assorbe la ricorsione.

## Esempi applicati

**Merge Sort**: `T(n) = 2T(n/2) + Θ(n)` → `a=2, b=2, log₂2=1`, `f(n)=Θ(n^1)` → **caso 2** → `T(n) ∈ Θ(n log n)`.

**Moltiplicazione classica matrici**: `T(n) = 4T(n/2) + O(n²)` → `log₂4=2`, `f(n)=O(n^{2-ε})` → **caso 1** → `T(n) ∈ Θ(n²)`.

**Karatsuba**: `T(n) = 3T(n/2) + O(n)` → `log₂3 ≈ 1.585`, `f(n)=O(n^{1.585-ε})` → **caso 1** → `T(n) ∈ Θ(n^{log₂3}) ≈ Θ(n^{1.585})`.

**Strassen**: `T(n) = 7T(n/2) + O(n²)` → `log₂7 ≈ 2.807`, `f(n)=O(n^{2.807-ε})` → **caso 1** → `T(n) ∈ Θ(n^{log₂7}) ≈ Θ(n^{2.807})`.

**Ricerca binaria**: `T(n) = T(n/2) + O(1)` → `a=1, b=2, log₂1=0`, `f(n)=Θ(1)` → **caso 2** → `T(n) ∈ Θ(log n)`.

## Intuizione: albero di ricorsione

Il costo totale `T(n)` è la somma dei costi di tutti i livelli. L'albero ha `log_b n` livelli; al livello `i` ci sono `aⁱ` sottoproblemi di taglia `n/bⁱ`. Il caso dominante (1, 2 o 3) dipende da dove si concentra il lavoro.

## Connessione con i corsi

- [[Tecniche di Programmazione]]: §7.3, applicato a Karatsuba e Strassen.
- [[Divide et Impera]]: MT è lo strumento principale per analizzare gli algoritmi D&C.

## Fonti

- [[Dispense TecProg — Galletti]] (§7.3, pp. 49-50)
