---
tipo: concetto
titolo: Formula di Bayes
tag: [probabilità, statistica, bayesiano, matematica]
cluster: probabilistica
fonti: 2
ultima-modifica: 2026-05-06
---

# Formula di Bayes

## Enunciato

Dati due eventi $A$ e $B$ con $P(B) > 0$:

$$P(A \mid B) = \frac{P(B \mid A) \cdot P(A)}{P(B)}$$

In forma estesa (con partizione $\{A_i\}$ dello spazio campione):

$$P(A_i \mid B) = \frac{P(B \mid A_i) \cdot P(A_i)}{\sum_j P(B \mid A_j) \cdot P(A_j)}$$

## Terminologia bayesiana

| Termine | Simbolo | Significato |
|---|---|---|
| **Prior** | $P(A)$ | probabilità di $A$ prima di osservare $B$ |
| **Likelihood** | $P(B \mid A)$ | quanto è probabile osservare $B$ dato che $A$ è vero |
| **Posterior** | $P(A \mid B)$ | probabilità di $A$ dopo aver osservato $B$ |
| **Evidenza** | $P(B)$ | probabilità marginale dell'osservazione |

## Derivazione

Segue direttamente dalla definizione di probabilità condizionata:
$$P(A \mid B) = \frac{P(A \cap B)}{P(B)}, \quad P(B \mid A) = \frac{P(A \cap B)}{P(A)}$$

Moltiplicando la seconda per $P(A)$ e sostituendo nella prima si ottiene la formula.

## Connessioni

- Fondamento dell'[[Apprendimento Bayesiano]] (prior + likelihood → posterior)
- Usata in: [[Probabilità condizionata]], [[Spazio di probabilità]]
- Stima Bayesiana: [[Stima MAP]] (massimizza la posterior), [[Intervalli di credibilità]]
- Corsi: [[Probabilità e Statistica]], [[Matematica per il Machine Learning]]
- Persona: [[Bayes, Thomas]]

## Fonti

- [[Dispense ProbStat — Galletti]] (probabilità condizionata, teorema di Bayes)
- [[Dispense MatML — Galletti]] (§2.10-2.11, Bayesiano)
