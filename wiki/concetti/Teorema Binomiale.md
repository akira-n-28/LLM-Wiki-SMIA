---
tipo: concetto
titolo: Teorema Binomiale
tag: [algebra, matematica, combinatoria]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Teorema Binomiale

Per $n \in \mathbb{N}$ e $x, y$ variabili (o elementi di un anello commutativo):

$$(x + y)^n = \sum_{k=0}^{n} \binom{n}{k} x^k y^{n-k}$$

dove il **coefficiente binomiale** è:

$$\binom{n}{k} = \frac{n!}{k!(n-k)!} \quad 0 \leq k \leq n$$

## Triangolo di Tartaglia

I coefficienti binomiali soddisfano la ricorsione:

$$\binom{n}{k} = \binom{n-1}{k-1} + \binom{n-1}{k}$$

(ogni elemento = somma dei due superiori). Le righe del triangolo forniscono i coefficienti di $(x+y)^n$.

## Proprietà fondamentali

| Proprietà | Formula |
|---|---|
| Simmetria | $\binom{n}{k} = \binom{n}{n-k}$ |
| Somma di una riga | $\sum_k \binom{n}{k} = 2^n$ |
| Somma a segni alterni | $\sum_k (-1)^k\binom{n}{k} = 0$ per $n > 0$ |
| Somma dei quadrati | $\sum_k \binom{n}{k}^2 = \binom{2n}{n}$ |

## In $\mathbb{Z}_p$ (applicazione)

Se $p$ è primo: $(x+y)^p \equiv x^p + y^p \pmod{p}$ perché $p \mid \binom{p}{k}$ per $0 < k < p$.

## Connessioni

- Si collega a: [[Permutazione]], [[Aritmetica modulare]]
- Applicazione combinatoria: counting, prove per induzione
- Discusso in: [[Strutture Algebriche]]

## Fonti

- [[Dispense StrAlg — Galletti]] (§2.2-2.3, pp. 77-79)
