---
tipo: concetto
titolo: Distribuzione geometrica
tag: [probabilità, distribuzioni]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Distribuzione geometrica

La [[Variabile aleatoria]] `X ∼ Geo(p)` conta il **numero di tentativi Bernoulli indipendenti** necessari per ottenere il primo successo (p = probabilità di successo):

$$
P(X = k) = (1-p)^{k-1}\,p, \quad k = 1, 2, 3, \ldots
$$

## Momenti

$$
E[X] = \frac{1}{p}, \qquad \mathrm{Var}(X) = \frac{1-p}{p^2}
$$

**Dimostrazione di E[X]:**

$$
E[X] = \sum_{k=1}^\infty k(1-p)^{k-1}p = p \cdot \frac{d}{dq}\sum_{k=1}^\infty q^k\bigg|_{q=1-p} = p \cdot \frac{1}{p^2} = \frac{1}{p}
$$

## Proprietà di assenza di memoria

$$
P(X > m + n \mid X > m) = P(X > n)
$$

La distribuzione geometrica è l'unica distribuzione discreta con questa proprietà. Corrisponde alla distribuzione esponenziale nel continuo.

## Funzione di ripartizione

$$
F(k) = P(X \leq k) = 1 - (1-p)^k
$$

## Connessione con la Distribuzione di Poisson

La Poisson è il limite della Binomiale per molti tentativi con piccola probabilità. La Geometrica descrive invece i **tempi di attesa** tra eventi Poisson: se gli eventi arrivano a tasso λ, il numero di tentativi fino al primo evento segue Geo(p) con p→0 in modo appropriato.

## Connessione con i processi stocastici

In [[Catena di Markov]], i **tempi di permanenza** in uno stato di una catena a tempo discreto con probabilità di uscita p seguono una distribuzione Geo(p). Questo è il punto di contatto con i processi di nascita-e-morte.

## Connessione con i corsi

- [[Probabilità e Statistica]]: §6, esempio di distribuzione discreta con calcolo esplicito dei momenti.
- [[Processi Stocastici]]: tempi di primo passaggio in catene di Markov.

## Persone

Storicamente legata a [[Bernoulli, Jakob]] (ripetizioni indipendenti di esperimenti Bernoulli).

## Fonti

- [[Dispense ProbStat — Galletti]] (§6, pp. 38-40)
