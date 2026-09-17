---
tipo: concetto
titolo: Metodo Cross-Entropy
tag: [ottimizzazione, statistica-computazionale, ml]
cluster: ottimizzazione
fonti: 1
ultima-modifica: 2026-05-04
---

# Metodo Cross-Entropy (CE method)

Algoritmo per **stima e ottimizzazione** basato sul [[Importance Sampling]]. Minimizza una funzione di costo `S(x)`, `x ∈ X`, aggiornando iterativamente una famiglia parametrica `{f(·|v), v ∈ V}` in modo che si concentri progressivamente sugli stati di costo basso.

## Idea

1. Campiona `x₁, …, x_N ∼ f(·|v_t)`.
2. Seleziona l'"**élite**": la frazione `ρ` con costo più basso.
3. Aggiorna `v` tramite **MLE sull'élite** + smoothing.

## Fondamento: minimizzazione della KL

L'obiettivo ideale è campionare da `f*(x) = f(x | S(X) ≤ γ)` — la distribuzione condizionata sui "buoni candidati". Poiché `f*` è incognita, si cerca il parametro `v` che minimizza la [[Divergenza di Kullback-Leibler]]:

$$
v' = \arg\min_{v \in V} D_{KL}(f^* \| f(\cdot|v)) = \arg\max_{v \in V} \mathbb{E}_{f^*}[\log f(X|v)]
$$

Approssimando `E_{f*}[·]` con la media sul campione élite `ξ_t`:

$$
v' = \arg\max_{v \in V} \sum_{x \in \xi_t} \log f(x|v)
$$

**Questo è esattamente il MLE sull'élite!**

## Algoritmo

```
Input: famiglia {f(·|v)}, v₀, rarità ρ ∈ (0,1), smoothing α ∈ (0,1), dimensione N
Per t = 0, 1, …:
  1. Campiona x₁,…,xₙ ∼ iid f(·|vₜ)
  2. Calcola S(xᵢ) per ogni campione
  3. Soglia: γₜ = quantile di ordine ρ di {S(x₁),…,S(xₙ)}
  4. Élite: ξₜ = {xᵢ : S(xᵢ) ≤ γₜ}   (top ρ × N campioni)
  5. v' ← argmax_v Σ_{x ∈ ξₜ} log f(x|v)   (MLE sull'élite)
  6. vₜ₊₁ ← α v' + (1-α) vₜ             (smoothing)
Restituisce: x* = argmin_{x ∈ ξₜ} S(x)
```

Parametri tipici: `ρ = 0.1` (top 10%) oppure `ρ = 0.01` (top 1%).

## Stime in forma chiusa: famiglia normale

Per `x ∼ N(µ, diag(σ²))`, il MLE sull'élite si riduce alle **statistiche campionarie** dell'élite:
- `µ̂ᵢ` = media componente `i` sull'élite
- `σ̂²ᵢ` = varianza componente `i` sull'élite

## Stime in forma chiusa: famiglia Bernoulli

Per ottimizzazione su stringhe binarie `x ∈ {0,1}^m` con `Xᵢ ∼ Ber(pᵢ)`:
- Parametro: `v = p = [p₁, …, p_m]`
- MLE sull'élite: `p̂ᵢ = (# volte bit i = 1 nell'élite) / |ξ_t|`

L'algoritmo converge a `p*` = stringa vera (`0` o `1` per ogni componente).

## Smoothing

Il parametro `α ∈ (0,1)` controlla la velocità di aggiornamento: `v_{t+1} = α v' + (1-α) v_t`. Evita oscillazioni bruschi per campioni piccoli o quando l'élite è poco rappresentativa.

## Connessione con Cross-entropy e MLE

Il nome "Cross-Entropy method" viene dall'aggiornamento:

$$
v' = \arg\max_v \underbrace{\mathbb{E}_{f^*}[\log f(X|v)]}_{= -H(f^*, f(\cdot|v)) + H(f^*)} = \arg\min_v H(f^*, f(\cdot|v))
$$

dove `H(f*, f(·|v))` è la [[Cross-entropy]] tra `f*` e `f(·|v)`. Il metodo **minimizza la cross-entropy** tra la distribuzione target e la famiglia parametrica.

## Connessione con Simulated Annealing

Entrambi concentrano la distribuzione sui buoni candidati:
- [[Simulated Annealing]]: parametro di concentrazione = `1/T` (temperatura)
- CE method: parametro di concentrazione = `v` (aggiornato via MLE)

SA usa M-H per campionare da `f_T`; CE campiona direttamente da `f(·|v)`.

## Connessione con Importance Sampling

Il campionamento da `f(·|v_t)` invece di `f` è un passo di IS. Il peso IS `f*(x)/f(x|v_t)` viene approssimato dall'indicatore dell'élite `1[S(x) ≤ γ_t]`. L'aggiornamento MLE è il [[Metodo del corrispondente stocastico]] applicato alla massimizzazione della log-likelihood.

## Connessione con l'apprendimento Bayesiano

L'aggiornamento `f(·|v_{t+1}) ← MLE(élite)` è analogo all'aggiornamento Bayesiano con likelihood = indicatore dell'élite. Con prior uniforme, MAP = MLE.

## Convergenza

La sequenza `(γ_t, v_t)` converge (approssimativamente) al minimo globale di `S` e `f(·|v_t)` converge a una distribuzione degenere concentrata sui minimizzatori.

## Applicazioni

- Ottimizzazione combinatoria (TSP, scheduling, bin packing).
- Reti neurali: ottimizzazione di architetture (NAS).
- Giochi (backgammon, poker): apprendimento di strategie.
- **Ottimizzazione con oracolo rumoroso**: basta valutare `Ŝ(x)` invece di `S(x)`.

## Connessione con i corsi SMIA

- [[Ottimizzazione]]: metodo alternativo a gradient descent per funzioni non differenziabili.
- [[Machine Learning]]: CE come alternativa a SGD per ottimizzazione globale.
- [[Processi Stocastici]]: la sequenza `v_t` è una catena di Markov sullo spazio dei parametri.

## ⚠️ Attenzione alla notazione

"Cross-Entropy method" (questo articolo) ≠ [[Cross-entropy]] come loss di classificazione. Il CE method **usa** la cross-entropy come criterio di aggiornamento di `v`, ma è un algoritmo di ottimizzazione generale.

## Persone

Proposto da [[Rubinstein, Reuven]] (1997-1999), originariamente per la stima di probabilità di eventi rari.

## Collegamenti

- Fondamento: [[Importance Sampling]], [[Divergenza di Kullback-Leibler]]
- Aggiornamento via: [[Metodo del corrispondente stocastico]], [[Stima di Massima Verosimiglianza]]
- Alternativa: [[Simulated Annealing]], [[Approssimazione stocastica]]
- Ottimizzazione deterministica: [[Discesa del gradiente]], [[Stochastic Gradient Descent]]
- Collegamento con: [[Cross-entropy]] (come loss, non come algoritmo)

## Fonti

- [[Dispense MatML — Galletti]] (§3.16, algoritmo 9, esempi 3.15-3.16, pp. 66-68)
