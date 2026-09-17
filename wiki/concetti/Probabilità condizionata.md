---
tipo: concetto
titolo: Probabilità condizionata
tag: [probabilità, fondamenti]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Probabilità condizionata

La **probabilità condizionata** di `A` dato `B` (con `P(B) > 0`) è:

$$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}
$$

Intuitivamente: restringiamo lo spazio campionario a `B` e ricalcoliamo la probabilità di `A` in questo spazio ridotto.

## Indipendenza

Due eventi `A` e `B` si dicono **indipendenti** se:

$$
P(A \mid B) = P(A) \quad \Longleftrightarrow \quad P(A \cap B) = P(A) \cdot P(B)
$$

Per tre eventi `A, B, C` l'indipendenza richiede che valgano tutte e quattro le fattorizzazioni (a coppie e a tripla).

**Attenzione:** indipendenza ≠ disgiunzione. Due eventi disgiunti con P>0 sono negativamente correlati, non indipendenti.

## Teorema della probabilità totale

Se `{Aᵢ}` è una **partizione** di `S` (eventi disgiunti con unione = S), allora:

$$
P(B) = \sum_i P(B \mid A_i) \cdot P(A_i)
$$

## Formula di Bayes

$$
P(A \mid B) = \frac{P(B \mid A) \cdot P(A)}{P(B)}
$$

Applicazione classica: diagnostica (P(malato | positivo) dato P(positivo | malato) e P(malato)).

## Esempi notevoli

**Problema di Monty Hall:** P(vincere cambiando porta) = 2/3 ≠ 1/2. La probabilità condizionata alla porta aperta dal conduttore modifica il calcolo.

**Problema dei compleanni:** P(nessun compleanno uguale in n persone) = 365·364·⋯·(365-n+1)/365ⁿ. Per n=23 supera il 50%.

## Connessione con l'apprendimento Bayesiano

In [[Apprendimento Bayesiano]], `P(θ | dati) ∝ P(dati | θ) · P(θ)` è esattamente la formula di Bayes con:
- `P(θ)` = prior
- `P(dati | θ)` = likelihood
- `P(θ | dati)` = posterior

## Connessione con Importance Sampling

Il peso IS `f(x)/g(x)` è il rapporto di densità condizionato usato in [[Importance Sampling]] per correggere il campionamento da `g` invece di `f`.

## Connessione con i corsi

- [[Probabilità e Statistica]]: fondamento per variabili aleatorie condizionate e indipendenza.
- [[Matematica per il Machine Learning]]: [[Formula di Bayes]] è il cuore dell'[[Apprendimento Bayesiano]].

## Collegamenti

- Dipende da: [[Spazio di probabilità]]
- Formula derivata: [[Formula di Bayes]]
- Usata in: [[Apprendimento Bayesiano]], [[Distribuzioni coniugate]]

## Fonti

- [[Dispense ProbStat — Galletti]] (§2.1, pp. 9-15)
