---
tipo: concetto
titolo: Distribuzione esponenziale
tag: [probabilità, distribuzioni, processi-stocastici]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Distribuzione esponenziale

La [[Variabile aleatoria]] `T ∼ Exp(λ)` con `λ > 0` descrive i **tempi di attesa** continui:

$$
F(t) = P(T \leq t) = 1 - e^{-\lambda t}, \qquad f(t) = \lambda e^{-\lambda t} \cdot \mathbf{1}_{t \geq 0}
$$

## Momenti

$$
E[T] = \frac{1}{\lambda}, \qquad \mathrm{Var}(T) = \frac{1}{\lambda^2}
$$

## Proprietà di assenza di memoria

$$
P(T > s + t \mid T > t) = P(T > s)
$$

Equivalente a richiedere `F̂(s+t) = F̂(s) F̂(t)` dove `F̂(t) = P(T > t) = e^{-λt}`. È l'**unica** distribuzione continua con questa proprietà (analogamente alla [[Distribuzione geometrica]] nel discreto).

**Dimostrazione**: imponendo `F̂'(s)/F̂(s) = costante = -λ`, si ottiene `F̂(t) = e^{-λt}`.

## Minimo di esponenziali

Se `Tλ ∼ Exp(λ)` e `Tµ ∼ Exp(µ)` indipendenti:

$$
T = \min(T_\lambda, T_\mu) \sim \mathrm{Exp}(\lambda + \mu)
$$

e `P(T = Tλ) = λ/(λ+µ)`. Generalizzazione: `min(T₁,…,Tₙ) ∼ Exp(Σλᵢ)`.

## Connessione con i processi di Poisson

I tempi tra eventi successivi di un [[Processo di nascita e morte|processo di Poisson]] a intensità `λ` sono i.i.d. `Exp(λ)`. Il collegamento fonda la teoria delle catene di Markov a tempo continuo.

## Connessione con i corsi

- [[Processi Stocastici]]: §5, fondamento per le catene di Markov a tempo continuo.
- [[Distribuzione di Poisson]]: il processo di Poisson come processo di conteggio con inter-arrivi Exp(λ).
- [[Distribuzione geometrica]]: analogo discreto con la stessa proprietà di assenza di memoria.

## Fonti

- [[Dispense Processi Stocastici — Galletti]] (§5.1, pp. 19-20)
