---
tipo: corso
titolo: Algoritmi e Complessità
docente: [Alessandro Panconesi, Flavio Chierichetti]
anno-accademico: 2024/2025
codice-breve: algoritmi
ultima-modifica: 2026-05-05
tag: [algoritmi, complessità, cs, smia]
---

# Algoritmi e Complessità

Corso tenuto dai proff. **Flavio Chierichetti** (parte algoritmi) e **Alessandro Panconesi** (parte complessità), A.A. 2024/2025, SMIA Sapienza. Dispense redatte da [[Galletti, Marco]].

## Programma

### §1 Introduzione (pp. 1-8)
1.1 [[Stable Matching]] — Gale-Shapley, best/worst, $O(n^2)$
1.2 [[Complessità computazionale]] — notazioni $O$, $\Omega$, $\Theta$

### §2 Algoritmi Greedy (pp. 9-20)
2.1 [[Interval Scheduling]] — regola earliest-finish, ottimalità per scambio
2.2 [[Interval Partitioning]] — profondità, heap $O(n \log n)$
2.3-2.4 [[Algoritmo di Huffman]] — prefix-code, ABL, greedy ricorsivo

### §3 Programmazione Dinamica (pp. 21-22)
3.1 [[Weighted Interval Scheduling]] — ricorrenza $\mathrm{OPT}(j)$, memoizzazione
3.2 [[Programmazione dinamica]] — Subset Sum, Knapsack $O(nW)$

### §4 Machine Learning (pp. 23-28)
4.1 [[Problema degli esperti]] — WM, Randomized WM, lower bound
4.2 [[Locality Sensitive Hashing]] — Jaccard, Single Linkage, LSH

### §5 Fondamenti di complessità (pp. 29-39)
5.1 [[NP-completezza]] — P/NP/NP-c, Cook-Levin, SAT≤Clique≤IS≤VC≤Knapsack, 3-SAT, 3-Coloring

### §6-7 Macchina di Turing (pp. 40-44)
6-7. [[Macchina di Turing]] — definizione, Halting Problem, decidibilità, $\mathrm{HP} \leq_T A \leq_T E \leq_T \mathrm{EQ}$

## Concetti centrali

| Concetto | Sezione | Collegato a |
|---|---|---|
| [[Stable Matching]] | §1 | [[Algoritmo greedy]] |
| [[Algoritmo greedy]] | §2 | [[Interval Scheduling]], [[Algoritmo di Huffman]] |
| [[Weighted Interval Scheduling]] | §3 | [[Programmazione dinamica]] |
| [[Problema degli esperti]] | §4 | [[Apprendimento statistico]] |
| [[NP-completezza]] | §5 | [[Complessità computazionale]], [[Macchina di Turing]] |
| [[Macchina di Turing]] | §6-7 | [[NP-completezza]], [[Logica del primo ordine]] |

## Fonti del corso

- [[Dispense Algoritmi — Galletti]] — 44 pp., A.A. 2024/2025 (ingest profondo 2026-05-05)

## Stato della wiki per questo corso

🟢 **Completo** — ingest profondo eseguito (2026-05-05). 10 nuove pagine + 1 aggiornamento.

## Connessioni trasversali con altri corsi

| Concetto | Corso collegato |
|---|---|
| Greedy, DP, ordinamento | [[Tecniche di Programmazione]] |
| P/NP, SAT, Halting | [[Fondamenti di Intelligenza Artificiale]] (SAT, clausole di Horn) |
| Online learning, esperti | [[Matematica per il Machine Learning]], [[Machine Learning]] |
| Complessità, Turing | [[Strutture Algebriche]] (basi algebriche) |
