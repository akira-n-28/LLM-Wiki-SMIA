---
tipo: concetto
titolo: Algoritmo di Strassen
tag: [algoritmi, divide-et-impera, cs, matrici]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-06
---

# Algoritmo di Strassen

Algoritmo di [[Divide et Impera]] per la moltiplicazione di matrici $n \times n$ in $O(n^{\log_2 7}) \approx O(n^{2.807})$, più veloce del metodo classico $O(n^3)$.

## Idea

La moltiplicazione di matrici $2 \times 2$ richiede normalmente 8 moltiplicazioni scalari. Strassen mostra che bastano **7 moltiplicazioni** (con più addizioni), sostituendo una moltiplicazione (costosa) con addizioni (economiche).

Per matrici di taglia $n$: si divide ogni matrice in 4 blocchi $n/2 \times n/2$, si applicano le 7 moltiplicazioni di Strassen ricorsivamente.

**Ricorrenza:** $T(n) = 7T(n/2) + O(n^2)$ → per il [[Master Theorem]]: $T(n) = O(n^{\log_2 7})$.

## Connessioni

- Paradigma: [[Divide et Impera]]
- Complessità: [[Master Theorem]], [[Complessità computazionale]]
- Confronto: [[Algoritmo di Karatsuba]] (stesso principio per gli interi)
- Applicazione numerica: [[Sistemi lineari — metodi diretti]], [[Singular Value Decomposition]]
- Persona: [[Strassen, Volker]]
- Corso: [[Tecniche di Programmazione]]

## Fonti

- [[Dispense TecProg — Galletti]] (§7)
