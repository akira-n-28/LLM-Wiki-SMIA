---
tipo: concetto
titolo: Campionamento di Gibbs
tag: [probabilità, statistica-computazionale, mcmc]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Campionamento di Gibbs (Gibbs Sampler)

Metodo MCMC per campionare da una distribuzione congiunta `f(x)` con `x = [x_1, …, x_n]^T` **aggiornando una componente alla volta** dalla sua distribuzione condizionata esatta (**full conditional**).

## Requisito

Si deve saper campionare da ciascuna full conditional:

$$
f(x_i \mid x_1, \ldots, x_{i-1}, x_{i+1}, \ldots, x_n)
$$

## Algoritmo (Systematic Scan)

```
Dato x⁰, per t = 0, 1, …, N-1:
  Per i = 1, …, n:
    yᵢ ∼ f(yᵢ | y₁, …, yᵢ₋₁, xₜ,ᵢ₊₁, …, xₜ,ₙ)
    (usa i valori yⱼ con j < i già aggiornati, xₜ,ⱼ con j > i ancora vecchi)
  xₜ₊₁ ← y
```

## Probabilità di accettazione = 1

Poiché ogni `y_i` viene estratto **esattamente** dalla full conditional di `f`, il candidato è già distribuito secondo la target: non serve alcuna correzione. `α = 1` sempre.

## Strategie di aggiornamento

| Strategia | Proprietà |
|---|---|
| **Scan sistematico** | Ciclo fisso `i = 1, …, n`. Non soddisfa il BD, ma converge per Hammersley-Clifford. |
| **Scan casuale (random scan)** | Indice `i ∼ U{1,…,n}` a ogni step. Soddisfa il [[Bilancio dettagliato]]. |
| **Block Gibbs** | Aggiorna interi sottovettori dalla loro congiunta. Riduce l'autocorrelazione per variabili fortemente dipendenti. |

## Esempio: modello normale Bayesiano

Target: `g(µ, σ²|x)` per modello `x_i ∼ N(µ, σ²)` con prior `g(µ, σ²) ∝ 1/σ²`.

Full conditionals:

$$
\mu \mid \sigma^2, x \sim \mathcal{N}\!\left(\bar x, \frac{\sigma^2}{n}\right)
$$

$$
\sigma^2 \mid \mu, x \sim \mathrm{Inv\text{-}Gamma}\!\left(\frac{n}{2},\; \frac{1}{2}\sum_{i=1}^n (x_i - \mu)^2\right)
$$

Il campionamento si alterna: si estrae `µ` dalla normale, poi `σ²` dall'Inv-Gamma (via `Z ∼ Gamma` e `σ² = 1/Z`).

## Gibbs come caso speciale di Metropolis-Hastings

Il Gibbs sampler è un caso limite di [[Metropolis-Hastings]] in cui la proposta è la full conditional `q(y_i|x) = f(y_i|x_{-i})`. In questo caso:

$$
\alpha(x, y) = \min\!\left(\frac{f(y)\,q(x|y)}{f(x)\,q(y|x)}, 1\right) = 1
$$

## Burn-in e correlazione

Come tutti i metodi MCMC, i campioni iniziali dipendono da `x⁰` (burn-in). I campioni consecutivi sono correlati. Con scan sistematico la catena non è reversibile ma converge comunque.

## Quando preferirlo a Metropolis-Hastings

- Le full conditionals appartengono a famiglie standard (es. normale, gamma, beta).
- Alta dimensionalità: MH con proposta multivariata ha basso tasso di accettazione; Gibbs aggiorna una dimensione alla volta.

## Limitazione: "slow mixing"

Se le variabili sono fortemente correlate, Gibbs si muove lentamente nello spazio dei parametri (mixing lento). Block Gibbs o reparametrizzazione possono aiutare.

## Connessione con le distribuzioni coniugate

Il Gibbs sampler è particolarmente efficiente quando il prior e la likelihood sono [[Distribuzioni coniugate]]: le full conditionals sono allora in forma chiusa e facilmente campionabili.

## Connessione con la fisica

Negli spin models, il Gibbs sampler aggiorna uno spin alla volta dalla sua distribuzione condizionata (distribuzione di Boltzmann-Gibbs locale). Equivale all'algoritmo **heat bath** nella meccanica statistica.

## Persone

Il nome viene da [[Gibbs, J. Willard]] (fisico, termodinamica statistica), non dagli autori dell'algoritmo informatico ([[Geman, Stuart e Donald]], 1984).

## Connessione con i corsi

- [[Processi Stocastici]]: Gibbs è una catena di Markov; la full conditional è la distribuzione invariante della catena per singola componente.
- [[Modelli Matematici per la Fisica II]]: algoritmo heat bath per spin.

## Collegamenti

- Caso speciale di: [[Metropolis-Hastings]]
- Richiede: [[Distribuzioni coniugate]] (per full conditionals in forma chiusa)
- Soddisfa: [[Bilancio dettagliato]] (per random scan)
- Framework: [[Catena di Markov]], [[Metodi Monte Carlo]]
- Usato in: [[Apprendimento Bayesiano]] (campionamento da posterior)

## Fonti

- [[Dispense MatML — Galletti]] (§3.10, esempi 3.9, pp. 52-55)
