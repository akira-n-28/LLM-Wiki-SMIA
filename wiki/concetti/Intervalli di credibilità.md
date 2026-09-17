---
tipo: concetto
titolo: Intervalli di credibilità
tag: [statistica, bayesiano, inferenza]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Intervalli di credibilità

Nel framework [[Apprendimento Bayesiano|Bayesiano]], un intervallo di credibilità al livello `1-α` per il parametro `θ` è un intervallo `I` tale che:

$$
P(\theta \in I \mid \tau) = 1 - \alpha \quad \Longleftrightarrow \quad \int_I g(\theta|\tau)\,d\theta = 1 - \alpha
$$

## Differenza con l'intervallo di confidenza

| | [[Intervallo di confidenza]] (frequentista) | Intervallo di credibilità (Bayesiano) |
|---|---|---|
| **θ** | Parametro **fisso** sconosciuto | **Variabile aleatoria** con prior |
| **Interpretazione** | L'intervallo casuale copre θ con prob. 1-α | θ è in I con prob. 1-α dati i dati |
| **Lettura diretta** | Non si può dire "P(θ ∈ I) = 0.95" | Si può dire "P(θ ∈ I | τ) = 0.95" |

L'intervallo di credibilità ha l'interpretazione probabilistica "naturale" che spesso (erroneamente) si attribuisce agli intervalli di confidenza.

## Esempio: modello normale con prior improprio

Con `g(µ)` improprio e prior `g(σ²) ∝ 1/σ²`, la posterior per `µ` marginale rispetto a `σ²` è una **t di Student** con `n-1` gradi di libertà. L'intervallo di credibilità al 95% è:

$$
I = \left[\bar x_n - \frac{S_n}{\sqrt{n-1}}\,\gamma,\quad \bar x_n + \frac{S_n}{\sqrt{n-1}}\,\gamma\right]
$$

dove `γ` è il quantile 0.975 della t di Student con `n-1` gradi di libertà. Si ritrova la stessa formula dell'intervallo di confidenza frequentista — la coincidenza numerica non è un caso (prior improprio ↔ frequentista).

## Scelta dell'intervallo

Più intervalli possono avere la stessa probabilità `1-α`. I criteri comuni sono:
- **HDR** (Highest Density Region): la regione di densità più alta, cioè la più piccola con probabilità `1-α`.
- **Intervallo equicodato**: taglia `α/2` per ogni coda.

## Vantaggio rispetto alla stima puntuale

La [[Stima MAP]] restituisce solo il picco della posterior; l'intervallo di credibilità quantifica l'**incertezza** attorno alla stima.

## Esempio: mortalità neonatale

Con `n = 100`, `s = 0` decessi, prior `Unif(0,1)`:
- Posterior: `Beta(1, 101)`, media `1/102 ≈ 0.01`
- Intervallo di credibilità al 95%: `[0, 0.0297]` (calcolabile numericamente)

## Connessione con la distribuzione t

La posterior marginale per `µ` nel modello normale con entrambi i prior impropri è esattamente `t_{n-1}` (ritrovando il risultato frequentista). Vedi [[Distribuzione t-Student]].

## Collegamenti

- Framework: [[Apprendimento Bayesiano]]
- Prior e posterior: [[Distribuzioni coniugate]]
- Alternativa frequentista: [[Intervallo di confidenza]]
- Stima puntuale: [[Stima MAP]]
- Distribuzione usata: [[Distribuzione t-Student]]

## Fonti

- [[Dispense MatML — Galletti]] (§2.10, definizione 2.9, pp. 40-41)
