---
tipo: concetto
titolo: Knapsack
tag: [algoritmi, programmazione-dinamica, np-completo, cs]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-06
---

# Problema dello zaino (Knapsack)

**Input:** $n$ oggetti con pesi $w_i$ e valori $v_i$; capacità $B$.
**Output:** sottoinsieme di oggetti con peso totale $\leq B$ e valore massimo.

## Soluzione con programmazione dinamica

Definisci $\phi(i, b)$ = valore massimo scegliendo tra i primi $i$ oggetti con capacità $b$:

$$\phi(i, b) = \max\bigl(\phi(i-1, b),\; v_i + \phi(i-1, b-w_i)\bigr)$$

Caso base: $\phi(0, b) = 0$ per ogni $b$.

**Complessità:** $O(nB)$ — pseudo-polinomiale (polinomiale in $n$ e $B$, ma esponenziale in $\log B$).

## Knapsack e NP-completezza

Il problema decisionale associato ("esiste una selezione di valore $\geq K$?") è **NP-completo**. È l'ultimo anello della catena di riduzione polinomiale:

$$\text{SAT} \leq_p \text{Clique} \leq_p \text{IS} \leq_p \text{VC} \leq_p \text{Knapsack}$$

## Connessioni

- [[Programmazione dinamica]]
- [[NP-completezza]] (problema NP-completo)
- Corso: [[Tecniche di Programmazione]], [[Algoritmi e Complessità]]

## Fonti

- [[Dispense TecProg — Galletti]] (§4 — programmazione dinamica)
