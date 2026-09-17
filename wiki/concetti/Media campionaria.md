---
tipo: concetto
titolo: Media campionaria
tag: [statistica, fondamenti]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-04-30
---

# Media campionaria

Media aritmetica dei valori osservati in un campione `x₁, …, xₙ`:

$$
\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_i
$$

È uno **stimatore non distorto** della media della popolazione `μ` quando il campione è i.i.d.: `E[X̄] = μ`. La sua varianza è `Var(X̄) = σ²/n`, dove `σ²` è la varianza della popolazione.

## Proprietà chiave

- Linearità: `E[X̄] = μ` (non distorto).
- `Var(X̄) = σ²/n` decresce come `1/n` (errore standard `σ/√n`).
- Per popolazione gaussiana: `X̄ ~ N(μ, σ²/n)`.
- Sotto ipotesi normale e con `s` come stima di `σ`: `(X̄ - μ)/(s/√n) ~ tₙ₋₁` ([[Distribuzione t-Student]]).

## Collegamenti

- Definita insieme a: [[Varianza campionaria]] (che ha `n-1` al denominatore proprio per via di X̄)
- Usata in: [[Intervallo di confidenza]], [[Test di ipotesi]]
- Generalizzata in [[Stima di Massima Verosimiglianza]] (per il modello esponenziale `θ̂_ML = 1/x̄`)

## Fonti

- [[Dispense MatML — Galletti]] (def. 1.3, p. 2)
