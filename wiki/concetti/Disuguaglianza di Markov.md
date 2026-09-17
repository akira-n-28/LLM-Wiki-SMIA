---
tipo: concetto
titolo: Disuguaglianza di Markov
tag: [probabilità, disuguaglianze, concentrazione]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Disuguaglianza di Markov

Sia `X ≥ 0` una [[Variabile aleatoria]] non negativa e `t > 0`. Allora:

$$
P(X \geq t) \leq \frac{E[X]}{t}
$$

## Dimostrazione

Definisco la funzione indicatrice `I_{X≥t}` che vale 1 se `X ≥ t`, 0 altrimenti. Allora:

$$
X \geq t \cdot I_{X \geq t}
$$

Prendendo il valore atteso di entrambi i lati:

$$
E[X] \geq E[t \cdot I_{X \geq t}] = t \cdot P(X \geq t)
$$

Dividendo per `t` si ottiene il risultato.

## Interpretazione

La disuguaglianza dice: se il valore atteso di `X` è piccolo, `X` non può essere grande con probabilità alta. Formalmente bassa: `P(X ≥ 100·E[X]) ≤ 1/100`.

È la disuguaglianza più debole ma più generale: richiede solo `X ≥ 0` e `E[X] < ∞`.

## Come strumento per la LGN

Viene usata direttamente per dimostrare la [[Legge dei Grandi Numeri]] nella versione tramite [[Disuguaglianza di Chebyshev]]: si applica Markov a `(X - µ)²`.

## Connessione con i corsi

- [[Probabilità e Statistica]]: §8.1, base della catena Markov → Chebyshev → LGN.
- [[Matematica per il Machine Learning]]: appare implicitamente nel contesto della stima dell'errore generalizzazione.

## Persone

[[Markov, Andrey]] — ma questa disuguaglianza elementare era nota prima; il nome è convenzionale.

## Fonti

- [[Dispense ProbStat — Galletti]] (§8.1, p. 45)
