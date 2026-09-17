---
tipo: concetto
titolo: Passeggiata aleatoria
aliases: ["Random Walk", "Rovina del giocatore"]
tag: [probabilità, processi-stocastici, catene-di-markov]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-06
---

# Passeggiata aleatoria (Random Walk)

Processo stocastico `Xₙ` su `ℤ` dove, a ogni passo, il processo si muove di `+1` (con probabilità `p`) o `-1` (con probabilità `q = 1-p`):

$$
X_n = X_0 + \sum_{i=1}^n Y_i, \quad Y_i \overset{\text{i.i.d.}}{\sim} \{+1 \text{ con prob. } p,\; -1 \text{ con prob. } q\}
$$

## Momenti

$$
E[X_n] = n(p - q), \qquad \mathrm{Var}[X_n] = n \cdot \mathrm{Var}[Y_1] = n(1 - (p-q)^2)
$$

Per `p = q = 1/2` (caso simmetrico): `E[Xₙ] = 0`, il cammino non ha deriva.

## Rovina del giocatore

**Problema**: un giocatore parte con `m` monete, vuole raggiungere `N`, e si rovina se arriva a `0`. Trova `fₙ(m) = P(rovina | X₀ = m)`.

**Soluzione**: risolvendo il sistema `fₙ(m) = p·fₙ(m+1) + q·fₙ(m-1)` con condizioni al bordo `fₙ(0)=1`, `fₙ(N)=0`:

$$
f_N(m) = \frac{\left(\frac{q}{p}\right)^m - \left(\frac{q}{p}\right)^N}{1 - \left(\frac{q}{p}\right)^N} \quad (p \neq q), \qquad f_N(m) = \frac{N - m}{N} \quad (p = q)
$$

## Durata media del gioco

Il tempo medio `hₙ(m) = E[T₀,ₙ | X₀ = m]` soddisfa un'equazione alle differenze:

$$
h(m) = 1 + p\,h(m+1) + q\,h(m-1), \quad h(0) = h(N) = 0
$$

Soluzione per `p ≠ q`: `h(m) = C₁ + C₂(q/p)^m + m/(q-p)`.

## Ricorrenza per p = q

Per `p = q = 1/2`, la passeggiata su `ℤ` è **ricorrente**: ritorna all'origine con probabilità 1. La probabilità di essere in `0` al tempo `2n` è:

$$
P(X_{2n} = 0 \mid X_0 = 0) = \binom{2n}{n} 2^{-2n} \approx \frac{1}{\sqrt{\pi n}} \to 0
$$

Per `p ≠ q`, la passeggiata è **transiente** (va a `±∞` con probabilità 1, per la LGN).

## Connessione con i corsi

- [[Processi Stocastici]]: §3, caso studio principale per la teoria delle catene di Markov.
- [[Legge dei Grandi Numeri]]: `P(|Xₙ/n - (p-q)| > ε) → 0`, la LGN descrive il comportamento asintotico.
- [[Catena di Markov]]: la passeggiata aleatoria è la catena di Markov più semplice su `ℤ`.

## Fonti

- [[Dispense Processi Stocastici — Galletti]] (§3, pp. 6-13)
