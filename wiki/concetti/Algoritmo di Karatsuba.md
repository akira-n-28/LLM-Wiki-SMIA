---
tipo: concetto
titolo: Algoritmo di Karatsuba
tag: [algoritmi, divide-et-impera, cs, moltiplicazione]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-06
---

# Algoritmo di Karatsuba

Algoritmo di [[Divide et Impera]] per la moltiplicazione di interi a $n$ cifre in $O(n^{\log_2 3}) \approx O(n^{1.585})$, più veloce del metodo classico $O(n^2)$.

## Idea

Per moltiplicare $x \cdot y$ con $x = x_H \cdot B^{n/2} + x_L$ e $y = y_H \cdot B^{n/2} + y_L$:

$$x \cdot y = x_H y_H \cdot B^n + (x_H y_L + x_L y_H) \cdot B^{n/2} + x_L y_L$$

L'osservazione chiave: il termine centrale si calcola con **una sola moltiplicazione** invece di due:
$$x_H y_L + x_L y_H = (x_H + x_L)(y_H + y_L) - x_H y_H - x_L y_L$$

Quindi servono 3 moltiplicazioni ricorsive di taglia $n/2$ invece di 4.

**Ricorrenza:** $T(n) = 3T(n/2) + O(n)$ → per il [[Master Theorem]]: $T(n) = O(n^{\log_2 3})$.

## Connessioni

- Paradigma: [[Divide et Impera]]
- Complessità: [[Master Theorem]], [[Complessità computazionale]]
- Confronto: [[Algoritmo di Strassen]] (stesso principio applicato alle matrici)
- Persona: [[Karatsuba, Anatoly]]
- Corso: [[Tecniche di Programmazione]]

## Fonti

- [[Dispense TecProg — Galletti]] (§7)
