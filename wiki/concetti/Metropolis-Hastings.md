---
tipo: concetto
titolo: Metropolis-Hastings
tag: [probabilità, statistica-computazionale, mcmc]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Algoritmo di Metropolis-Hastings

Metodo MCMC (Markov Chain Monte Carlo) per campionare da una densità target `f(x)` **nota a meno di costante di normalizzazione**. Costruisce una [[Catena di Markov]] la cui distribuzione limite è esattamente `f`.

## Ingredienti

- **Target** `f(x)` (si può usare `f̃(x) = Z f(x)` — la costante `Z` si elide nel rapporto).
- **Proposta** `q(y|x)`: densità da cui è facile campionare un candidato `y` dato lo stato attuale `x`.

## Probabilità di accettazione

$$
\alpha(x, y) = \min\!\left(\frac{f(y)\,q(x|y)}{f(x)\,q(y|x)},\; 1\right)
$$

## Algoritmo

```
Dato X₀, per t = 0, 1, …, N-1:
  1. Estrai Y ∼ q(·|Xₜ)
  2. Calcola α = α(Xₜ, Y)
  3. Estrai U ∼ U(0,1)
  4. Se U ≤ α: Xₜ₊₁ ← Y   (accetta)
     Altrimenti: Xₜ₊₁ ← Xₜ (rifiuta)
```

## Perché funziona

La transizione effettiva `q̃(y|x) = q(y|x) α(x,y)` soddisfa il [[Bilancio dettagliato]]:

$$
f(x)\,\tilde q(y|x) = f(y)\,\tilde q(x|y)
$$

Combinato con irriducibilità e aperiodicità (garantite da una proposta opportuna), la catena converge a `f`.

## Proprietà chiave

- `Z` incognita: nel rapporto `f(y)/f(x)` la costante di normalizzazione si elide.
- Se `f(y) ≥ f(x)`: accettazione certa (`α = 1`) — mosse verso zone di densità maggiore sempre accettate.
- Se `f(y) < f(x)`: accettazione con probabilità `f(y)/f(x)` — mosse "in salita" accettate con prob. inferiore a 1.

## Varianti della proposta

| Proposta                                     | Formula α                        |                               |                     |
| -------------------------------------------- | -------------------------------- | ----------------------------- | ------------------- |
| **Simmetrica** `q(y                          | x) = q(x                         | y)`                           | `min(f(y)/f(x), 1)` |
| **Random Walk** `y = x + z`, `z ∼ N(0, σ²I)` | `min(f(y)/f(x), 1)` (simmetrica) |                               |                     |
| **Campionatore indipendente** `q(y           | x) = g(y)`                       | `min(f(y)g(x)/(f(x)g(y)), 1)` |                     |

Il parametro `σ²` del random walk va calibrato: troppo piccolo → esplorazione lenta; troppo grande → alta probabilità di rifiuto.

## Applicazione: Distribuzione di Boltzmann-Gibbs

Target: `f(σ) = e^{-βH(σ)}/Z`. Con proposta simmetrica:

$$
\alpha(\sigma, \sigma') = \min\!\left(e^{-\beta[H(\sigma') - H(\sigma)]}, 1\right) = \min(e^{-\beta \Delta E}, 1)
$$

Se `ΔE ≤ 0` (energia diminuisce): accetta sempre. Se `ΔE > 0`: accetta con prob. `e^{-βΔE}`. Questo è il **criterio di Metropolis** classico della meccanica statistica.

## Burn-in e correlazione

I campioni `X_1, …, X_N` sono **correlati** (non i.i.d.). Si scartano i primi `B` campioni (burn-in). Per ridurre la correlazione residua si può fare **thinning**: tenere solo ogni `k`-esimo campione.

## Confronto con Gibbs

| | Metropolis-Hastings | [[Campionamento di Gibbs]] |
|---|---|---|
| Proposta | Arbitraria | Condizionate esatte |
| Prob. accettazione | `α < 1` (rifiuti possibili) | Sempre 1 |
| Applicabilità | Molto generale | Richiede full conditionals |
| Efficienza | Dipende dalla proposta | Alta (nessun rifiuto) |

## Convergenza: condizioni

1. **Irriducibilità**: il supporto di `q(y|x)` copre tutto il supporto di `f`.
2. **Aperiodicità**: la proposta non crea cicli periodici (soddisfatta per random walk continuo).
3. **Bilancio dettagliato**: garantito dalla costruzione di `α`.

## Connessioni

- Generalizza [[Metodo accept-reject]] al caso sequenziale (MCMC).
- È il caso generale di cui [[Campionamento di Gibbs]] è un caso limite (`α = 1`).
- Fondamentale in [[Apprendimento Bayesiano]] quando la posterior non è coniugata.

## Persone

[[Metropolis, Nicholas]] et al. (1953); generalizzato da [[Hastings, W.K.]] (1970).

## Connessione con i corsi

Catene di Markov irriducibili e aperiodiche: vedi [[Processi Stocastici]] per la teoria completa (equazioni di Chapman-Kolmogorov, mixing time).

## Collegamenti

- Fondamento: [[Catena di Markov]], [[Bilancio dettagliato]]
- Caso speciale: [[Campionamento di Gibbs]]
- Generalizza: [[Metodo accept-reject]]
- Applicato a: [[Apprendimento Bayesiano]] (campionamento da posterior), fisica statistica

## Fonti

- [[Dispense MatML — Galletti]] (§3.9, pp. 49-53)
