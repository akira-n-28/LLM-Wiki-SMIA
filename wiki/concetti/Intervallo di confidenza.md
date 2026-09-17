---
tipo: concetto
titolo: Intervallo di confidenza
tag: [statistica, inferenza]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-04-30
---

# Intervallo di confidenza

Intervallo `[θ₁, θ₂]` calcolato dai dati che ha probabilità `1-α` di contenere il vero valore del parametro `θ`:

$$
P(\theta_1 < \theta < \theta_2) = 1 - \alpha
$$

## Caso media (popolazione normale)

Se `X₁,…,Xₙ ∼ N(μ, σ²)` con `σ` ignota, usando la statistica `T = (X̄ - μ)/(s/√n) ∼ tₙ₋₁`:

$$
\text{IC}_{1-\alpha}(\mu) = \left[ \bar{x} - t_{1-\alpha/2,\,n-1}\frac{s}{\sqrt{n}},\; \bar{x} + t_{1-\alpha/2,\,n-1}\frac{s}{\sqrt{n}} \right]
$$

dove `t_{1-α/2, n-1}` è il quantile della [[Distribuzione t-Student]].

## Interpretazione

⚠️ L'intervallo è una variabile aleatoria (dipende dal campione), `μ` è fisso. La probabilità `1-α` si riferisce alla **procedura**: se ripetessimo il campionamento molte volte, il `(1-α)·100%` degli intervalli costruiti conterrebbe il vero `μ`.

Distinto dall'[[Intervalli di credibilità|intervallo di credibilità]] (Bayesiano), dove il parametro è la variabile aleatoria.

## Collegamenti

- Strumento di: [[Statistica inferenziale]]
- Affiancato da: [[Test di ipotesi]] (dualità)
- Controparte Bayesiana: [[Intervalli di credibilità]]

## Fonti

- [[Dispense MatML — Galletti]] (def. 1.6, p. 5; oss. confronto credibilità p. 40)
