---
tipo: concetto
titolo: Distribuzione t-Student
tag: [statistica, distribuzioni]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-04-30
---

# Distribuzione t-Student

Distribuzione di probabilità per la statistica della media campionaria quando la varianza della popolazione `σ²` è ignota e viene stimata dai dati.

## Definizione

Per `X₁,…,Xₙ ∼ i.i.d. N(μ, σ²)`, con [[Media campionaria]] `x̄` e [[Varianza campionaria]] `s²`:

$$
T = \frac{\bar{x} - \mu}{s/\sqrt{n}} \sim t_{n-1}
$$

dove `n-1` è il numero di **gradi di libertà**.

## Proprietà

- Simmetrica attorno a 0, code più pesanti della normale standard.
- Per `ν = n-1 → ∞`, `tᵥ → N(0,1)` (perché `s → σ`).
- Già a `ν = 30` la differenza con la normale è trascurabile.

## Costruzione formale

Se `Z ∼ N(0,1)` e `V ∼ χ²ᵥ` indipendenti:

$$
T = \frac{Z}{\sqrt{V/\nu}} \sim t_\nu
$$

## Usi

- [[Intervallo di confidenza]] per la media con varianza ignota.
- [[Test di ipotesi]] sulla media (test t).
- Emerge come **posterior marginale** per `μ` in [[Apprendimento Bayesiano]] di un modello gaussiano con prior improprio (con `n-1` gdl).

## Collegamenti

- Costruita da: [[Distribuzione chi-quadro]] (al denominatore)
- Tende a: normale standard `N(0,1)` per ν grande
- Ricomp. in: [[Apprendimento Bayesiano]] (modello normale, prior improprio)

## Fonti

- [[Dispense MatML — Galletti]] (def. 1.7, p. 5; ricomp. p. 40)
