---
tipo: concetto
titolo: BIC
tag: [ml, statistica, selezione-modelli]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# BIC (Bayesian Information Criterion)

Criterio per la **selezione del modello** che penalizza la complessità in modo proporzionale a `log n`. Derivato dall'approssimazione di Laplace dell'evidenza Bayesiana:

$$
\mathrm{BIC} := -2\log g(T_n | \hat\theta_n) + d \log n
$$

dove `d` è il numero di **parametri liberi** del modello e `n` la taglia del training set.

Si preferisce il modello con **BIC più piccolo**: fit migliore ↔ log-likelihood più alta; complessità penalizzata ↔ termine `d log n`.

## Derivazione: approssimazione di Laplace

Nel framework [[Apprendimento Bayesiano|Bayesiano]], l'evidenza è `g(T_n) = ∫ g(T_n|θ) g(θ) dθ`. Per `n → ∞` (sotto ipotesi di regolarità), l'espansione al secondo ordine della log-posterior attorno alla stima MAP `θ̄_n ≈ θ̂_n` dà:

$$
\log g(T_n) \approx \log g(T_n|\hat\theta_n) - \frac{d}{2}\log n
$$

Equivalentemente:

$$
-2\log g(T_n) \approx \underbrace{-2\log g(T_n|\hat\theta_n)}_{\text{deviance}} + d\log n = \mathrm{BIC}
$$

## Selezione tra modelli

Per una famiglia di modelli indicizzata da `k ∈ {1, …, m}` (es. grado polinomiale), con prior uniforme `g(k) = 1/m`:

$$
g(k|T_n) \propto g(T_n|k) \approx C\exp\!\left(-\frac{\mathrm{BIC}(k)}{2}\right)
$$

Scegliere il modello con BIC minimo equivale (circa) a scegliere quello con evidenza massima.

## Procedura pratica

1. Stima `θ̂_n` (MLE o MAP).
2. Valuta la log-likelihood `log g(T_n|θ̂_n)`.
3. Calcola `BIC = -2 log g(T_n|θ̂_n) + d log n`.
4. Scegli il modello con BIC più piccolo.

## Esempio: modello lineare normale

`Y ∼ N(Xβ, σ² I_n)`, parametri `θ = (β, σ²)` con `d = p + 1` gradi di libertà. La log-likelihood massimizzata vale:

$$
\log g(T_n|\hat\theta_n) = -\frac{n}{2}\log\hat\sigma^2_{ML} + \mathrm{const}
$$

quindi:

$$
\mathrm{BIC}(p) = n\log\hat\sigma^2_{ML} + (p+1)\log n
$$

All'aumentare di `p`:
- `σ̂²_ML` diminuisce (fit migliore): contributo negativo al BIC.
- `(p+1) log n` aumenta: penalità cresce logaritmicamente.

Il minimo del BIC identifica il grado ottimale.

## Confronto con altri criteri

| Criterio | Penalità | Note |
|---|---|---|
| **BIC** | `d log n` | Consistente: seleziona il modello vero per `n → ∞` |
| **AIC** | `2d` | Minimizza l'errore di previsione, non consistente |
| **[[Cross-validation]]** | Empirica | Generale, costosa computazionalmente |
| **[[Ottimismo]]** | `2ℓ*p/n` | Solo per OLS, richiede stima di `ℓ*` |

BIC penalizza più fortemente di AIC per `n > 7` (poiché `log n > 2`).

## Collegamento con l'ottimismo

BIC e [[Ottimismo]] sono due modi di correggere il bias della training loss:
- Ottimismo: correzione analitica diretta `ℓ_in ≈ ℓ_τ + 2ℓ*p/n`
- BIC: correzione via log-verosimiglianza penalizzata

Entrambi crescono con `p/n` e decrescono con `n`.

## Limiti del BIC

- Richiede un modello parametrico (non si applica direttamente a reti neurali con parametri impliciti).
- L'approssimazione di Laplace è valida solo per `n` grande e modello ben specificato.
- Non gestisce direttamente il bias di misspecification.

## Connessione con la consistenza

BIC è **consistente**: per `n → ∞`, seleziona il modello vero (se è nella famiglia considerata). AIC non è consistente ma ha errore di previsione minore per campioni piccoli.

## Collegamenti

- Derivato da: [[Apprendimento Bayesiano]] (approssimazione di Laplace)
- Stima usata: [[Stima di Massima Verosimiglianza]], [[Stima MAP]]
- Alternativa: [[Cross-validation]], [[Ottimismo]]
- Applicato a: [[Modello lineare normale]], [[Regressione polinomiale]]
- Fondamento: [[Disuguaglianza di Jensen]] (nel proof dell'evidenza)

## Fonti

- [[Dispense MatML — Galletti]] (§2.11, teorema 2.6, esempio 2.16, pp. 41-43)
