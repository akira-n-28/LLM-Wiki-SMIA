---
tipo: concetto
titolo: Weighted Interval Scheduling
tag: [algoritmi, programmazione-dinamica, ottimizzazione]
cluster: algoritmi
fonti: 2
ultima-modifica: 2026-05-05
---

# Weighted Interval Scheduling

## Problema

Dati $m$ intervalli $(s_j, f_j)$ con pesi $w_j \geq 0$, trovare il sottoinsieme compatibile (non sovrapposto) di peso totale massimo. Il greedy non funziona: richiede programmazione dinamica.

## Struttura del sottoproblema

Ordina per tempo di fine: $f_1 \leq f_2 \leq \cdots \leq f_m$.

**$p(j)$:** il massimo indice $i < j$ tale che $i$ e $j$ sono disgiunti (0 se non esiste).

**$\mathrm{OPT}(j)$:** valore ottimo usando solo i primi $j$ intervalli.

## Ricorrenza

$$\mathrm{OPT}(j) = \max\bigl(w_j + \mathrm{OPT}(p(j)),\; \mathrm{OPT}(j-1)\bigr)$$

- Se $j \in O_j$: il peso è $w_j$ + ottimo sui compatibili con $j$ (cioè $\{1,\ldots,p(j)\}$).
- Se $j \notin O_j$: ottimo sui primi $j-1$ intervalli.

Base: $\mathrm{OPT}(0) = 0$.

## Algoritmo memoizzato (M-Compute-Opt)

```
M-compute-Opt(j):
  if j ∈ memo: return memo[j]
  if j = 0: memo[0] = 0
  else: memo[j] = max(w_j + M-compute-Opt(p(j)), M-compute-Opt(j-1))
  return memo[j]
```

**Complessità:** $O(m)$ (ogni sottoproblema risolto una volta) + $O(m \log m)$ per il calcolo dei $p(j)$ (ricerca binaria).

## Confronto con Interval Scheduling non pesato

| Aspetto | Interval Scheduling | Weighted IS |
|---|---|---|
| Obiettivo | Massimo numero di job | Massimo peso totale |
| Algoritmo | Greedy earliest-finish | Programmazione dinamica |
| Complessità | $O(n \log n)$ | $O(n \log n)$ |

## Connessioni

- Paradigma: [[Programmazione dinamica]]
- Versione non pesata: [[Interval Scheduling]]
- Prerequisito: [[Algoritmo greedy]] (perché greedy non basta)
- Discusso in: [[Algoritmi e Complessità]], [[Tecniche di Programmazione]]

## Fonti

- [[Dispense Algoritmi — Galletti]] (§3.1, pp. 21-22)
- [[Dispense TecProg — Galletti]] (§ programmazione dinamica)
