---
tipo: concetto
titolo: Spazio di probabilità
tag: [probabilità, fondamenti]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Spazio di probabilità

Struttura formale per assegnare probabilità agli eventi. Una tripla `(S, P(S), P)` dove:
- `S` = spazio campionario (insieme degli esiti elementari)
- `P(S)` = σ-algebra degli eventi (sottoinsiemi di S)
- `P : P(S) → [0,1]` = funzione di probabilità

## Assiomi di Kolmogorov

1. `0 ≤ P(E) ≤ 1` per ogni `E ∈ P(S)`
2. `P(S) = 1` (certezza)
3. Se `E₁, E₂, …` sono eventi **disgiunti a due a due**, allora:

$$
P\!\left(\bigcup_{i=1}^n E_i\right) = \sum_{i=1}^n P(E_i)
$$

## Conseguenze degli assiomi

- `P(∅) = 0`
- `P(Aᶜ) = 1 - P(A)`
- Se `A ⊆ B` allora `P(A) ≤ P(B)`
- **Principio di inclusione-esclusione**:

$$
P(A \cup B) = P(A) + P(B) - P(A \cap B)
$$

Versione generale per `n` eventi:

$$
P\!\left(\bigcup_{i=1}^n A_i\right) = \sum_i P(A_i) - \sum_{i<j} P(A_i \cap A_j) + \sum_{i<j<k} P(A_i \cap A_j \cap A_k) - \cdots
$$

## Modello classico

Quando tutti gli esiti elementari sono **equiprobabili**:

$$
P(A) = \frac{|A|}{|S|} = \frac{\text{casi favorevoli}}{\text{casi possibili}}
$$

## Misura prodotto

Per spazi indipendenti `S = R × T`: `P(A_R × A_T) = P_R(A_R) · P_T(A_T)`. Base formale per la definizione di [[Variabile aleatoria]] indipendente.

## Connessione con i corsi

- [[Processi Stocastici]]: la stessa struttura viene estesa a spazi di misura generali e a sequenze di variabili aleatorie.
- [[Matematica per il Machine Learning]]: ogni distribuzione di probabilità usata (Normale, Bernoulli, Gamma) è una misura di probabilità su uno spazio opportuno.

## Persone

Assiomatizzazione formale di [[Kolmogorov, Andrey]] (1933, *Grundbegriffe der Wahrscheinlichkeitsrechnung*).

## Collegamenti

- Genera: [[Variabile aleatoria]], [[Valore atteso]]
- Usato in: [[Probabilità condizionata]], [[Formula di Bayes]]
- Esteso in: [[Processi Stocastici]] (filtrazioni, martingale)

## Fonti

- [[Dispense ProbStat — Galletti]] (§2, pp. 8-10)
