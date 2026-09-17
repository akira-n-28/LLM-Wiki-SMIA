---
tipo: concetto
titolo: Stima di Massima Verosimiglianza
tag: [ml, statistica, inferenza]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# Stima di Massima Verosimiglianza (MLE)

Dato un dataset `τ = {x_1, …, x_n}` i.i.d. da densità incognita `f`, e una classe parametrica `G_p = {g(·|θ), θ ∈ Θ}`, lo stimatore MLE è:

$$
\hat\theta_{ML} = \arg\max_{\theta \in \Theta} \prod_{i=1}^n g(x_i|\theta) = \arg\max_{\theta \in \Theta} \sum_{i=1}^n \log g(x_i|\theta)
$$

## Equivalenza con ERM su log-loss

Minimizzare il **rischio empirico** con loss logaritmica equivale a massimizzare la log-likelihood:

$$
\ell_\tau(\theta) = -\frac{1}{n}\sum_{i=1}^n \log g(x_i|\theta) + \frac{1}{n}\sum_{i=1}^n \log f(x_i) \quad \Longrightarrow \quad \hat\theta_{ML} = \arg\min_\theta \ell_\tau(\theta)
$$

Il secondo termine non dipende da `θ`.

## Equivalenza con minimizzazione della KL

Il rischio teorico con log-loss è la [[Divergenza di Kullback-Leibler]]:

$$
\ell(\theta) = \mathbb{E}_f\!\left[\log \frac{f(X)}{g(X|\theta)}\right] = D_{KL}(f \| g(\cdot|\theta)) + H(f)
$$

Quindi MLE minimizza `D_KL(f ‖ g(·|θ))` su tutte le realizzazioni possibili.

## Calcolo: equazione dello score

Se `log g(x|θ)` è concava in `θ`, lo stimatore si trova annullando lo **score**:

$$
\frac{1}{n}\sum_{i=1}^n \frac{\partial \log g(x_i|\theta)}{\partial \theta}\Bigg|_{\hat\theta} = 0
$$

## Esempio: distribuzione esponenziale

`g(x|θ) = θ e^{-θx}`, `x > 0`. La log-likelihood è `n log θ - θ n x̄_n`. Annullando lo score:

$$
\hat\theta_{ML} = \frac{1}{\bar x_n}
$$

## Equivalenza con OLS per il modello lineare normale

Per il [[Modello lineare normale]] `Y = Xβ + σZ`, `Z ∼ N(0, I_n)`:

$$
\hat\beta_{ML} = \hat\beta_{LS} = (X^T X)^{-1} X^T y
$$

(massimizzare la gaussiana rispetto a `β` equivale a minimizzare `‖y - Xβ‖²`).

## Limite della convergenza Bayesiana

Nel framework [[Apprendimento Bayesiano|Bayesiano]], iterando l'aggiornamento `w_t ∝ w_{t-1} · g(τ|θ)`, la densità converge per `t → ∞` a una delta di Dirac centrata in `θ̂_ML`.

## Distorsione dello stimatore della varianza

Per il modello lineare, `σ̂²_ML = ‖y - Xβ̂‖²/n` è **biased**: divide per `n` invece di `n-p`. Lo stimatore corretto è `σ̂² = ‖y - Xβ̂‖²/(n-p)`.

## Connessione con la stima MAP

Con prior uniforme, [[Stima MAP]] = MLE. Con prior informativo, MAP aggiunge un termine di regolarizzazione.

## NLL e Cross-Entropy

Per un modello di classificazione con distribuzione categorica (softmax), la NLL (Negative Log-Likelihood) diventa la **cross-entropy loss**:

$$\text{NLL}(\theta) = -\sum_{i=1}^n \log P(y_i | x_i; \theta) = -\sum_{i=1}^n \sum_{c=1}^C \mathbf{1}[y_i = c] \log \hat{p}_{i,c}$$

dove $\hat{p}_{i,c} = \text{softmax}(f_\theta(x_i))_c$ (cfr. [[Softmax]]). Minimizzare la cross-entropy equivale a massimizzare la likelihood sul modello categorico — cioè MLE con distribuzione di Bernoulli (binaria) o categorica (multiclasse). La cross-entropy è il surrogato loss usato in pratica per la classificazione neurale (cfr. [[Cross-entropy]]).

## Connessione con la regressione logistica

Per la regressione logistica binaria con $P(y=1|x) = \sigma(w \cdot x)$:
$$\text{NLL}(w) = -\sum_i [y_i \log \sigma(w \cdot x_i) + (1-y_i)\log(1 - \sigma(w \cdot x_i))]$$
questa è la **binary cross-entropy loss** ottimizzata con discesa del gradiente.

## Collegamenti

- Equivalente a: [[ERM]] su log-loss
- Minimizza: [[Divergenza di Kullback-Leibler]]
- Caso lineare: [[Modello lineare normale]], [[Minimi quadrati]]
- Limite di: [[Apprendimento Bayesiano]]
- Alternativa Bayesiana: [[Stima MAP]]
- NLL per classificazione: [[Cross-entropy]], [[Softmax]]

## Fonti

- [[Dispense MatML — Galletti]] (esempi 2.8-2.9, §2.9, pp. 25-30)
