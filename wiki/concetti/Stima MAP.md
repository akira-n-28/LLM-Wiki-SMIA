---
tipo: concetto
titolo: Stima MAP
tag: [ml, statistica, bayesiano]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# Stima MAP (Maximum A Posteriori)

Stima puntuale nel framework [[Apprendimento Bayesiano|Bayesiano]]: si sceglie il valore di `θ` che massimizza la **distribuzione a posteriori**:

$$
\bar\theta_n = \arg\max_\theta\, g(\theta|\tau) = \arg\max_\theta\, \bigl[g(\tau|\theta)\, g(\theta)\bigr]
$$

## Relazione con MLE

- **Prior uniforme**: `g(θ) = const` → MAP = [[Stima di Massima Verosimiglianza|MLE]].
- **Prior informativo**: MAP aggiunge un termine di regolarizzazione: `log g(θ|τ) = log g(τ|θ) + log g(θ) + const`.

## Relazione con la regressione regolarizzata

Con prior gaussiano `g(β|σ²) = N(0, σ² D)`:

$$
\bar\beta = \arg\max_\beta \left[-\frac{1}{2\sigma^2}\|y - X\beta\|^2 - \frac{1}{2\sigma^2}\beta^T D^{-1}\beta\right]
$$

che equivale a minimizzare `‖y - Xβ‖² + β^T D^{-1} β`. Per `D = λI` si ottiene la [[Regolarizzazione di Tikhonov|regressione ridge]].

## Soluzione analitica per il modello lineare normale

Con prior `g(β|σ²) = N(0, σ²D)` e `g(σ²) ∝ 1/σ²`, la stima MAP è:

$$
\bar\beta = \Sigma X^T y, \qquad \Sigma = (X^T X + D^{-1})^{-1}
$$

(cfr. [[Dispense MatML — Galletti]], §2.11).

## Convergenza a MLE per n → ∞

Sotto ipotesi di regolarità e con prior non degenere:

$$
\bar\theta_n \xrightarrow{n\to\infty} \hat\theta_{ML} \quad \text{quasi certamente}
$$

Il contributo del prior `(1/n) \log g(θ)` diventa trascurabile rispetto alla log-likelihood media.

## Differenza con la stima Bayesiana completa

La MAP è una stima **puntuale**: restituisce un singolo valore `θ̄`, perdendo l'informazione sulla forma completa della posterior. La stima Bayesiana completa usa l'intera posterior per la predizione:

$$
g_\tau(x) = \int g(x|\theta)\, g(\theta|\tau)\,d\theta \neq g(x|\bar\theta)
$$

La MAP è utile quando l'integrale è intrattabile ma la moda della posterior è approssimabile (es. tramite approssimazione di [[Laplace, Pierre-Simon|Laplace]] → [[BIC]]).

## Intervalli vs credibilità

La MAP non fornisce direttamente [[Intervalli di credibilità]], che invece richiedono l'intera posterior.

## Uso nel BIC

La [[BIC|approssimazione di Laplace]] usa `θ̄_n` (spesso approssimato con MLE per `n` grande) come punto attorno a cui espandere la log-posterior:

$$
\log g(T_n) \approx \log g(T_n|\hat\theta_n) - \frac{d}{2}\log n
$$

## Esempi

- **Beta–Binomiale**: con prior `Beta(a, b)` e `s` successi su `n`:
  - MAP = `(a+s-1)/(a+b+n-2)` (moda della Beta a posteriori)
  - Per `a = b = 1` (prior uniforme): MAP = MLE = `s/n`

## Collegamenti

- Framework: [[Apprendimento Bayesiano]]
- Limite con prior uniforme: [[Stima di Massima Verosimiglianza]]
- Regolarizzazione: [[Regolarizzazione di Tikhonov]]
- Approssimazione: [[BIC]]
- Alternativa con distribuzione completa: [[Intervalli di credibilità]]

## Fonti

- [[Dispense MatML — Galletti]] (§2.10-2.11, pp. 40-42)
