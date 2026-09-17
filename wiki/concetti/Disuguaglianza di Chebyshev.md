---
tipo: concetto
titolo: Disuguaglianza di Chebyshev
tag: [probabilità, disuguaglianze, concentrazione]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Disuguaglianza di Chebyshev

Sia `X` una [[Variabile aleatoria]] con `E[X] = µ` e `Var(X) = σ² < ∞`. Allora per ogni `t > 0`:

$$
P(|X - \mu| \geq t) \leq \frac{\mathrm{Var}(X)}{t^2}
$$

## Dimostrazione

$$
P(|X - \mu| \geq t) = P\!\left((X - \mu)^2 \geq t^2\right) \leq \frac{E\!\left[(X-\mu)^2\right]}{t^2} = \frac{\mathrm{Var}(X)}{t^2}
$$

dove l'ultimo passo usa la [[Disuguaglianza di Markov]] applicata alla v.a. non negativa `(X - µ)²`.

## Esempio quantitativo

Lancio di una moneta con `p = P(T)`. Sia `Yₙ = #teste` in `n` lanci, con `E[Yₙ/n] = p` e `Var(Yₙ/n) = p(1-p)/n`. Affinché:

$$
P\!\left(\left|\frac{Y_n}{n} - p\right| \leq \frac{1}{10}\right) \geq \frac{99}{100}
$$

basta `n > 10000·p(1-p)`. Nel caso peggiore (`p = 1/2`): `n > 2500`.

## Confronto: Chebyshev vs bound esponenziale

Chebyshev dà `P(|Ȳ - p| > ε) ≤ Var(X)/(nε²)` — **polinomiale** in `n`. La disuguaglianza di Hoeffding (via tecnica momento esponenziale) dà `P ≤ 2e^{-nε²/2}` — **esponenziale** in `n`. Chebyshev è più debole ma richiede solo la varianza finita.

## Come passo della LGN

La [[Legge dei Grandi Numeri]] (versione debole) si dimostra direttamente con Chebyshev:

$$
P\!\left(\left|\frac{1}{n}\sum_{i=1}^n X_i - \mu\right| \geq \varepsilon\right) \leq \frac{\mathrm{Var}(X_1)}{n\varepsilon^2} \xrightarrow{n\to\infty} 0
$$

## Connessione con i corsi

- [[Probabilità e Statistica]]: §8.2, collegata a LGN e stima di `n` per convergenza.
- [[Matematica per il Machine Learning]]: bound sulla generalizzazione e stabilità degli stimatori.

## Persone

[[Chebyshev, Pafnuty]] (1867) — anche noto come Čebyšëv o Tchebycheff.

## Fonti

- [[Dispense ProbStat — Galletti]] (§8.2, pp. 45-46)
