---
tipo: concetto
titolo: Importance Sampling
tag: [probabilità, statistica-computazionale]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Importance Sampling (Campionamento di Importanza)

Tecnica per stimare `µ = E_f[H(X)] = ∫ H(x) f(x) dx` campionando da una pdf alternativa `g` invece di `f`. Utile quando campionare da `f` è inefficiente (es. eventi rari, `H` concentrato in una regione a bassa probabilità sotto `f`).

## Idea

Moltiplicare e dividere per `g(x)`:

$$
\mu = \int H(x)\frac{f(x)}{g(x)}\,g(x)\,dx = \mathbb{E}_g\!\left[H(X)\frac{f(X)}{g(X)}\right]
$$

Il rapporto `w(x) = f(x)/g(x)` è detto **peso di importance sampling** (likelihood ratio).

## Stimatore

Dati `x_1, …, x_N ∼ g` i.i.d.:

$$
\hat\mu = \frac{1}{N}\sum_{i=1}^N H(x_i)\frac{f(x_i)}{g(x_i)}
$$

**Non distorto** per `µ`. Intervallo di confidenza asintotico via CLT.

## Algoritmo

```
Input: H, pdf nominale f, pdf IS g, dimensione N, livello 1-α
1. Estrai x₁,…,xₙ ∼ iid g
2. yᵢ ← H(xᵢ) f(xᵢ)/g(xᵢ)
3. µ̂ ← (1/N) Σyᵢ
4. S ← std campionaria di y₁,…,yₙ
5. I ← [µ̂ ± z_{1-α/2} S/√N]
```

## Scelta di g: la pdf ottimale

La varianza dello stimatore è `Var_g[H(X)f(X)/g(X)] / N`. La pdf `g` che minimizza la varianza è:

$$
g^*(x) = \frac{|H(x)|\,f(x)}{\int |H(x')|\,f(x')\,dx'} = \frac{|H(x)|\,f(x)}{\mu}
$$

Con `g = g*`, la varianza è **zero** (se `H ≥ 0`). Paradosso: per costruire `g*` serviva già conoscere `µ`. Benchmark teorico.

**Condizione pratica** per varianza finita:

$$
\mathrm{Var}_g[\hat\mu] = \frac{1}{N}\mathbb{E}_f\!\left[\frac{H^2(X)\,f(X)}{g(X)}\right] - \frac{\mu^2}{N} < \infty
$$

Le code di `g` non devono essere più leggere di `f`: se `g(x) → 0` più velocemente di `f(x)`, il rapporto `f/g` esplode e la varianza diverge.

## Esempio: area 2D con simmetria radiale

Target: `M(x₁,x₂) = C · e^{-r/4}(sin(2r)+1)`, `r = √(x₁²+x₂²)`.

Con `f = U([-b,b]²)` il MC grezzo è inefficiente (M si concentra sugli anelli circolari). Scelta IS: densità radiale `g(x) ∝ e^{-λr}` — campionamento in coordinate polari (`R ∼ Exp(λ)`, `Θ ∼ U(0,2π)`). Il parametro `λ` viene ottimizzato via [[Approssimazione stocastica]] o [[Metodo del corrispondente stocastico]].

## Connessione con la riduzione della varianza

IS è una delle tecniche di [[Riduzione della varianza]]: invece di correggere i campioni a posteriori (variabili di controllo), modifica la distribuzione di campionamento a priori.

## Connessione con l'apprendimento

In ML, IS compare in:
- **Importance weighting** per dataset sbilanciati o covariate shift: pesi `f_{test}/f_{train}`.
- **Policy gradient** in RL: stima di `E_π[R]` con campioni da `π₀`.
- **ELBO** in inferenza variazionale: peso `p(z|x)/q(z)`.
- **Metodo Cross-Entropy**: IS come punto di partenza per l'ottimizzazione della pdf `g` tramite minimizzazione della KL.

## Connessione con MLE

L'aggiornamento MLE sull'élite nel [[Metodo Cross-Entropy]] è equivalente a IS con `g = f(·|v)` e minimizzazione della KL rispetto a `f* = f(·|S ≤ γ)`.

## Connessione con KL

$$
D_{KL}(f \| g) = \mathbb{E}_f\!\left[\log\frac{f(X)}{g(X)}\right]
$$

Minimizzare la [[Divergenza di Kullback-Leibler]] `D_KL(f ‖ g)` sceglie la `g` più vicina a `f` nel senso IS — questo è esattamente ciò che fa il [[Metodo Cross-Entropy]].

## Connessione con Metropolis-Hastings

[[Metropolis-Hastings]] usa implicitamente IS: la probabilità di accettazione `α(x,y) = min(f(y)q(x|y)/(f(x)q(y|x)), 1)` è un rapporto di likelihood simile al peso IS, ma in un contesto MCMC.

## Limitazioni in alta dimensionalità

In `ℝ^d`, trovare una `g` con code non più leggere di `f` diventa difficile. Il peso `f/g` tende a degenerare (pochi campioni dominano). Per `d` grande si preferisce MCMC.

## Normalizzazione self-normalized

Quando `f` è nota a meno di costante (`f = Z f̃`), si usa lo stimatore normalizzato:

$$
\hat\mu_{SN} = \frac{\sum_i H(x_i) f(x_i)/g(x_i)}{\sum_i f(x_i)/g(x_i)}
$$

Distorto, ma consistente e spesso più stabile.

## Collegamenti

- Categoria: [[Metodi Monte Carlo]], [[Riduzione della varianza]]
- Connessa a: [[Divergenza di Kullback-Leibler]], [[Stima di Massima Verosimiglianza]]
- Usata in: [[Metodo Cross-Entropy]] (ottimizzazione della pdf IS)
- Ottimizzazione del parametro: [[Approssimazione stocastica]], [[Metodo del corrispondente stocastico]]

## Fonti
	
- [[Dispense MatML — Galletti]] (§3.13, esempio 3.13, pp. 61-62)
