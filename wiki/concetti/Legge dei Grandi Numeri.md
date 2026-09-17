---
tipo: concetto
titolo: Legge dei Grandi Numeri
tag: [probabilità, convergenza, fondamenti]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Legge dei Grandi Numeri

Siano `X₁, X₂, …` variabili aleatorie i.i.d. con `E[Xᵢ] = µ` e `Var(Xᵢ) < ∞`. Allora per ogni `ε > 0`:

$$
P\!\left(\left|\frac{1}{n}\sum_{i=1}^n X_i - \mu\right| \geq \varepsilon\right) \xrightarrow{n\to\infty} 0
$$

Cioè la media campionaria **converge in probabilità** a `µ`.

## Dimostrazione via Chebyshev

$$
P\!\left(\left|\bar{X}_n - \mu\right| \geq \varepsilon\right) \leq \frac{\mathrm{Var}(\bar{X}_n)}{\varepsilon^2} = \frac{\mathrm{Var}(X_1)}{n\,\varepsilon^2} \xrightarrow{n\to\infty} 0
$$

Il passaggio chiave: `Var(X̄ₙ) = Var(X₁)/n` perché le `Xᵢ` sono **indipendenti** (la varianza della somma di v.a. indipendenti è la somma delle varianze).

## Dimostrazione via bound esponenziale (più forte)

Per `Xᵢ ∼ Ber(p)` con `Sₙ = Σ Xᵢ`, si ha anche il bound:

$$
P\!\left(\frac{S_n}{n} \geq p + \varepsilon\right) \leq e^{-\frac{1}{4}n\varepsilon^2}
$$

dimostrato tramite la tecnica del momento esponenziale (Chernoff). Questo bound è esponenzialmente più stretto di Chebyshev.

## LGN forte vs debole

- **LGN debole** (Khinchin): convergenza in probabilità — dimostrata sopra.
- **LGN forte** (Kolmogorov): `P(X̄ₙ → µ) = 1` — convergenza quasi certa, richiede solo `E[|X|] < ∞`.

## Connessione con Monte Carlo

La stima Monte Carlo `ȳ_N = (1/N)Σ H(xᵢ) → µ = E[H(X)]` è esattamente la LGN applicata alla successione `H(X₁), H(X₂), …` i.i.d. Vedi [[Metodi Monte Carlo]].

## Connessione con la frequenza relativa

L'interpretazione frequentista della probabilità: la frequenza relativa di un evento in `n` prove i.i.d. converge alla probabilità. È la LGN applicata alle indicatrici `Iₐ(Xᵢ)`.

## Connessione con i corsi

- [[Probabilità e Statistica]]: §8, dimostrazione via Chebyshev + bound esponenziale per Bernoulli.
- [[Matematica per il Machine Learning]]: la convergenza della media empirica al rischio teorico (giustifica l'ERM).
- [[Processi Stocastici]]: legge ergodica per catene di Markov ergodiche (generalizzazione).

## Persone

[[Bernoulli, Jakob]] (caso Bernoulli, 1713). Forma generale: [[Khinchin, Aleksandr]] (LGN debole, 1929) e [[Kolmogorov, Andrey]] (LGN forte).

## Fonti

- [[Dispense ProbStat — Galletti]] (§8, pp. 44-46)
