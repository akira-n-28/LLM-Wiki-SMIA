---
tipo: concetto
titolo: Catena di Markov
tag: [probabilità, processi-stocastici, statistica-computazionale]
cluster: probabilistica
fonti: 2
ultima-modifica: 2026-05-04
---

# Catena di Markov

Processo stocastico `{X_t}_{t ≥ 0}` che soddisfa la **proprietà markoviana** (assenza di memoria): la distribuzione del prossimo stato dipende solo dallo stato attuale, non dalla storia passata.

$$
f(x_t | x_1, x_2, \ldots, x_{t-1}) = q(x_t | x_{t-1})
$$

dove `q(·|·)` è la **densità di transizione** (omogenea nel tempo).

## Definizione formale

**Catena di Markov Omogenea**: `q(x_t | x_{t-1})` non dipende da `t`. Il campionamento procede:

```
x₀ ∼ f₀     (distribuzione iniziale)
xₜ ∼ q(·|xₜ₋₁)   per t = 1, 2, …
```

## Distribuzione stazionaria

Una distribuzione `π` è **stazionaria** per la catena se è invariante sotto la transizione:

$$
\pi(y) = \int \pi(x)\, q(y|x)\,dx \quad \text{(caso continuo)}
$$

oppure `π(j) = Σ_i π(i) q(j|i)` (caso discreto).

## Distribuzione limite

Una distribuzione `π` è **limite** se, per qualsiasi stato iniziale `i`:

$$
\lim_{t\to\infty} P(X_t = j | X_0 = i) = \pi(j) \quad \forall j
$$

Se esiste la distribuzione limite, essa coincide con l'unica distribuzione stazionaria.

## Ergodicità

Una catena è **ergodica** (converge all'unica distribuzione stazionaria indipendentemente dallo stato iniziale) se è:

- **Irriducibile**: ogni stato è raggiungibile da ogni altro.
- **Aperiodica**: non esistono cicli fissi di transizione.

## Bilancio dettagliato → sufficiente per stazionarietà

Il [[Bilancio dettagliato]] `f(x) q(y|x) = f(y) q(x|y)` è una condizione **sufficiente** (non necessaria) affinché `f` sia stazionaria. È più forte del semplice bilancio globale, ma più semplice da verificare.

**Schema delle condizioni per MCMC:**

$$
\text{Irriducibilità} + \text{Aperiodicità} + \text{Bilancio dettagliato} \implies \text{convergenza a } f(x)
$$

## Burn-in (termalizzazione)

I primi campioni generati dalla catena dipendono fortemente dallo stato iniziale `x_0` e non riflettono la distribuzione target. La fase di **burn-in** identifica il numero di passi da scartare prima che la catena raggiunga la distribuzione stazionaria.

## Catena di Markov come strumento MCMC

L'obiettivo dei metodi [[Metodi Monte Carlo|MCMC]] (Markov Chain Monte Carlo) è costruire una catena la cui distribuzione stazionaria coincida con la densità target `f(x)`. Dopo il burn-in, si usa la traiettoria come approssimazione di campioni i.i.d. da `f`.

Campioni consecutivi sono **correlati** (a differenza di accept-reject), ma la correlazione decresce all'aumentare del gap temporale.

## Random Walk su grafo

Esempio canonico: `q(j|i) = 1/deg(i)` per archi `(i,j)` del grafo. La distribuzione stazionaria è proporzionale al grado dei nodi.

## Teoria formale (tempo discreto)

**Matrice stocastica**: `P = {pᵢⱼ}` con `pᵢⱼ ≥ 0` e `Σⱼ pᵢⱼ = 1` per ogni `i`. La distribuzione al tempo `n` è `ρₙ = Pⁿ ρ₀`.

**Accessibilità**: `i → j` se `∃n: (Pⁿ)ᵢⱼ > 0`. Se `i → j` e `j → i` allora `i ↔ j` (comunicazione, relazione di equivalenza). Le classi di equivalenza si dicono **classi comunicanti**.

**Irriducibilità**: la catena è irriducibile se ha una sola classe comunicante (tutti gli stati comunicano tra loro).

**Ricorrenza**: lo stato `i` è ricorrente se `P(Tᵣᵢ < ∞ | X₀ = i) = 1`, cioè il processo ritorna a `i` con probabilità 1. Criterio: `i` è ricorrente ⟺ `Σₙ (Pⁿ)ᵢᵢ = ∞`. Se la catena ha spazio di stati finito, almeno uno stato è ricorrente.

**Ricorrente positivo vs nullo**: `i` è ricorrente positivo se `E[Tᵣᵢ | X₀ = i] < ∞`, nullo se `= ∞`.

**Periodicità**: `i` è aperiodico se `∃n̄: (Pⁿ)ᵢᵢ > 0 ∀n ≥ n̄`. È periodico se `(Pⁿ)ᵢᵢ > 0 ⟺ n = k·m` per qualche `m ∈ ℕ`.

**Teorema ergodico**: se la catena è irriducibile, aperiodica e positivamente ricorrente allora:

$$
\lim_{n\to\infty} P(X_n = j \mid X_0 = i) = \pi_j = \frac{1}{\mu_j(j)} \quad \forall i, j
$$

dove `µⱼ(j) = E[Tᵣⱼ | X₀ = j]` è il tempo medio di ritorno. La distribuzione stazionaria è **autovettore sinistro** di `P` con autovalore 1: `π = πP`.

## Connessione con i Processi Stocastici

Le catene di Markov a tempo discreto si generalizzano a tempo continuo tramite il [[Generatore infinitesimale]] `Q`: `P(t) = e^{Qt}`, con equazioni di Kolmogorov `P'(t) = P(t)Q`. Vedi [[Processi Stocastici]].

## Connessione con la fisica

La distribuzione di Boltzmann-Gibbs `P(σ) ∝ e^{-βH(σ)}` è la distribuzione stazionaria della catena di Markov costruita da [[Metropolis-Hastings]]. La dinamica della catena simula l'evoluzione del sistema fisico verso l'equilibrio termico.

## Connessione con l'apprendimento Bayesiano

Il ciclo di aggiornamento Bayesiano `w_t ∝ w_{t-1} · g(τ|θ)` è anch'esso una catena di Markov sullo spazio delle densità — converge alla distribuzione `δ(θ - θ̂_ML)`.

## Esempio: modello degli spin

Partendo da una configurazione iniziale `σ^(0)`, la catena genera `σ^(0) → σ^(1) → … → σ^(k)`. Per `k ≫ 1` (dopo il burn-in):

$$
P(\sigma = \sigma^{(k)}) \approx \frac{e^{-\beta H(\sigma^{(k)})}}{Z}
$$

La magnetizzazione attesa si stima come media temporale: `⟨m⟩ ≈ (1/K) Σ_k m^(k)`.

## Collegamento con i corsi

- [[Processi Stocastici]]: teoria completa delle catene di Markov, equazione di Chapman-Kolmogorov.
- [[Metodi Numerici]]: aspetti computazionali.

## Collegamenti

- Algoritmi basati su: [[Metropolis-Hastings]], [[Campionamento di Gibbs]]
- Proprietà: [[Bilancio dettagliato]]
- Framework: [[Metodi Monte Carlo]]
- Alternativa non-MCMC: [[Metodo accept-reject]] (campioni indipendenti)

## Fonti

- [[Dispense MatML — Galletti]] (§3.6, §3.8, §3.9, pp. 47-52)
- [[Dispense Processi Stocastici — Galletti]] (§3, §5, pp. 4-17)
