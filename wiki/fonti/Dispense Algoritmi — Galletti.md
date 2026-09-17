---
tipo: fonte
titolo: Dispense Algoritmi — Galletti
autori: [Marco Galletti]
docente-corso: [Alessandro Panconesi, Flavio Chierichetti]
anno-accademico: 2024/2025
data-ingest: 2026-05-05
file-raw: raw/appunti/algoritmi.pdf
pagine: 44
ultima-modifica: 2026-05-05
tag: [algoritmi, complessità, cs]
---

# Dispense di Algoritmi e Complessità — Galletti

**Riferimento file raw:** `raw/appunti/algoritmi.pdf`
**Corso:** [[Algoritmi e Complessità]] (proff. Alessandro Panconesi + Flavio Chierichetti, A.A. 2024/2025, SMIA Sapienza)
**Autore appunti:** [[Galletti, Marco]]

## Riassunto in 5 punti

1. **Algoritmi classici**: Stable Matching (Gale-Shapley, $O(n^2)$) e notazioni asintotiche $O$/$\Omega$/$\Theta$.
2. **Paradigma greedy**: Interval Scheduling (earliest-finish, ottimo per scambio), Interval Partitioning (profondità, heap), Algoritmo di Huffman (prefix-code, ABL minima, $O(n \log n)$).
3. **Programmazione dinamica**: Weighted Interval Scheduling ($\mathrm{OPT}(j) = \max(w_j + \mathrm{OPT}(p(j)), \mathrm{OPT}(j-1))$) e Subset Sum / Knapsack ($O(nW)$, pseudopolinomiale).
4. **Online learning**: Problema degli esperti, Weighted Majority ($m \leq 2{,}41(m^* + \log n)$), Randomized WM ($\mathbb{E}[m] \leq (1+\varepsilon)m^* + \frac{\ln n}{\varepsilon}$), lower bound per deterministici, clustering e LSH.
5. **Teoria della complessità**: P, NP, NP-completo (Cook-Levin); catena di riduzioni SAT≤Clique≤IS≤VC≤SubsetSum≤Partition≤Knapsack; 3-SAT, 3-Coloring; Macchina di Turing, Halting Problem, decidibilità, $\mathrm{HP} \leq_T A \leq_T F \leq_T E \leq_T \mathrm{EQ}$.

## Argomenti trattati

### §1 Introduzione (pp. 1-8)
- [[Stable Matching]] — Gale-Shapley, best(a)/worst(b), $O(n^2)$
- [[Complessità computazionale]] — notazioni $O$, $\Omega$, $\Theta$

### §2 Algoritmi Greedy (pp. 9-20)
- [[Algoritmo greedy]] — paradigma, tecnica di scambio
- [[Interval Scheduling]] — earliest finish time, dimostrazione ottimalità
- [[Interval Partitioning]] — profondità, heap $O(n \log n)$
- [[Algoritmo di Huffman]] — prefix-code, ABL, greedy ricorsivo

### §3 Programmazione Dinamica (pp. 21-22)
- [[Weighted Interval Scheduling]] — ricorrenza, memoizzazione, $p(j)$
- [[Programmazione dinamica]] — Subset Sum / Knapsack: $\mathrm{OPT}(i,V) = \max(\mathrm{OPT}(i-1,V), w_i + \mathrm{OPT}(i-1,V-w_i))$

### §4 Machine Learning (pp. 23-28)
- [[Problema degli esperti]] — Dimezzamento, Weighted Majority, Randomized WM, lower bound
- [[Locality Sensitive Hashing]] — similarità di Jaccard, Single Linkage, LSH

### §5 Fondamenti di complessità (pp. 29-39)
- [[NP-completezza]] — P, NP, NP-c, Cook-Levin, riduzioni, catena completa

### §6-7 Macchina di Turing (pp. 40-44)
- [[Macchina di Turing]] — definizione, Halting, decidibilità, TM non-det, riduzioni

## Note di lettura

- Tono intermedio tra algoritmico (Chierichetti) e teorico (Panconesi). I §1-4 sono più operativi; §5-7 sono teoria pura.
- §4 "Machine Learning" tratta algoritmi online: più affine a [[Problema degli esperti]] e online learning che al ML statistico di altri corsi.
- Il §3 copre solo 2 pp. di DP: va integrato con [[Programmazione dinamica]] (TecProg) per una trattazione completa.

## Pagine wiki aggiornate da questa ingest

**Ingest profondo (2026-05-05):**

*Create — concetti (10):*
- [[Stable Matching]] (nuova)
- [[Algoritmo greedy]] (nuova)
- [[Interval Scheduling]] (nuova — era link rotto da TecProg)
- [[Interval Partitioning]] (nuova)
- [[Algoritmo di Huffman]] (nuova)
- [[Weighted Interval Scheduling]] (nuova — era link rotto da TecProg)
- [[Problema degli esperti]] (nuova)
- [[NP-completezza]] (nuova)
- [[Macchina di Turing]] (nuova)
- [[Locality Sensitive Hashing]] (nuova)

*Aggiornata — concetto esistente (1):*
- [[Complessità computazionale]] — aggiunta sezione P/NP/NP-c, link a NP-completezza e Macchina di Turing

*Aggiornata — infrastruttura:*
- [[Algoritmi e Complessità]] (corso) — da 🟡 a 🟢

## Fonti
- `raw/appunti/algoritmi.pdf`
