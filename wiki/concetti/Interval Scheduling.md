---
tipo: concetto
titolo: Interval Scheduling
tag: [algoritmi, greedy, ottimizzazione]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-05
---

# Interval Scheduling

## Problema

Dati $n$ job, ognuno con tempo di inizio $s_i$ e di fine $f_i$. Due job sono **compatibili** se non si sovrappongono ($\min(f_i, f_j) \leq \max(s_i, s_j)$). Trovare il sottoinsieme compatibile di cardinalità massima.

## Algoritmo greedy ottimo

**Regola $M^*$:** ad ogni passo scegli il job con il **tempo di fine più piccolo** tra quelli compatibili con la selezione corrente.

Complessità: $O(n \log n)$ (ordinamento per $f_i$).

## Dimostrazione di ottimalità (scambio)

Sia $O = \{J_1, \ldots, J_m\}$ ottimo ordinato per fine, e $S = \{I_1, \ldots, I_k\}$ greedy.

**Invariante:** $f(I_r) \leq f(J_r)$ per ogni $r$ (dimostrato per induzione). La soluzione greedy "non è mai in ritardo" rispetto all'ottimo.

Raggiunto $O_k = \{I_1, \ldots, I_k, J_{k+1}, \ldots, J_m\}$: poiché $M^*$ si ferma quando nessun job è compatibile, nessun $J_{k+1}, \ldots, J_m$ può sopravvivere, dunque $k = m$.

## Regole non ottime

- "Intervallo più corto": non ottimo in generale.
- "Meno conflitti": non ottimo in generale.

## Weighted Interval Scheduling

Con pesi $w_j \geq 0$ per ogni job, l'approccio greedy non funziona: richiede [[Programmazione dinamica]]. (cfr. [[Weighted Interval Scheduling]])

## Connessioni

- Paradigma: [[Algoritmo greedy]]
- Versione pesata: [[Weighted Interval Scheduling]]
- Partitioning: [[Interval Partitioning]]
- Discusso in: [[Algoritmi e Complessità]], [[Tecniche di Programmazione]]

## Fonti

- [[Dispense Algoritmi — Galletti]] (§2.1, pp. 9-10)
