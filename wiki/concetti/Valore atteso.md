---
tipo: concetto
titolo: Valore atteso
tag: [probabilità, fondamenti]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Valore atteso

Il **valore atteso** di una [[Variabile aleatoria]] discreta `X` è la **media ponderata** dei suoi valori con i rispettivi pesi probabilistici:

$$
E[X] = \sum_{\omega \in S} X(\omega) \cdot P(\{\omega\}) = \sum_{x} x \cdot P(X = x)
$$

## Proprietà fondamentali

- **Linearità**: `E[aX + b] = a·E[X] + b` (vale sempre, indipendentemente da dipendenza)
- **Addittività**: `E[X + Y] = E[X] + E[Y]` (vale sempre)
- **Prodotto per indipendenti**: se X⊥Y allora `E[XY] = E[X]·E[Y]`
- **Composizione**: `E[f(X)] = Σ_x f(x)·P(X=x)` (legge dello statistico inconsapevole)

## Valori attesi notevoli

| Variabile | E[X] | E[X²] |
|-----------|------|-------|
| Ber(p) | p | p |
| B(n,p) | np | np(1-p) + n²p² |
| Geo(p) | 1/p | (2-p)/p² |
| Poi(λ) | λ | λ² + λ |

**Dimostrazione E[B(n,p)] = np:** usando l'identità `k·C(n,k) = n·C(n-1,k-1)` si ottiene `E[X] = np·Σ C(n-1,j)p^j(1-p)^{n-1-j} = np`.

## Interpretazione della linearità

La linearità vale anche per v.a. dipendenti. Esempio classico: X = n° persone sedute vicino al proprio partner in un tavolo da 20. Scrivendo `X = Σᵢ Iᵢ` (funzioni indicatrici), si ottiene `E[X] = 20·P(vicino al partner) = 40/19` senza bisogno di calcolare la distribuzione di X.

## Metodo probabilistico

Se `E[f(T)] > c` allora esiste almeno un esito `t ∈ S` tale che `f(t) > c`. Usato per dimostrare l'esistenza di strutture combinatorie (es. cammini Hamiltoniani in tornei, colorazioni di grafi).

## Connessione con il Rischio Teorico

In [[Apprendimento statistico]], il [[Rischio teorico]] è `ℓ(g) = E_{(X,Y)}[L(Y, g(X))]`, cioè il valore atteso della perdita sulla distribuzione generativa. L'[[ERM]] minimizza il corrispondente valore atteso empirico.

## Connessione con Monte Carlo

La stima Monte Carlo `ȳ_N = (1/N)Σ H(xᵢ)` converge a `µ = E_f[H(X)]` per la Legge dei Grandi Numeri. Vedere [[Metodi Monte Carlo]].

## Connessione con i corsi

- [[Probabilità e Statistica]]: definizione di base.
- [[Matematica per il Machine Learning]]: E[X] è il fondamento del rischio teorico.
- [[Processi Stocastici]]: E[X_t | X_s] = attesa condizionata, generalizzazione per martingale.

## Persone

[[Kolmogorov, Andrey]] (1933) — assiomatizzazione moderna. Radici storiche in Pascal, Fermat, Huygens (XVII sec.).

## Collegamenti

- Dipende da: [[Variabile aleatoria]], [[Spazio di probabilità]]
- Strumento: [[Varianza e covarianza]] (costruita su E[X²] - E[X]²)
- Usato in: [[Rischio teorico]], [[Metodi Monte Carlo]], [[Bootstrap]]

## Fonti

- [[Dispense ProbStat — Galletti]] (§2.3-2.4, pp. 19-24)
