---
tipo: concetto
titolo: Stimatore
tag: [statistica, inferenza, fondamenti]
cluster: probabilistica
fonti: 2
ultima-modifica: 2026-05-06
---

# Stimatore

Uno **stimatore** di un parametro $\theta$ è una **funzione del campione** $\hat\theta = T(X_1, \ldots, X_n)$, dove $X_i$ sono [[Variabile aleatoria|variabili aleatorie]] i.i.d. dalla distribuzione $f(\cdot \mid \theta)$. Lo stimatore è esso stesso una variabile aleatoria, con una propria distribuzione (chiamata **distribuzione campionaria**).

## Tre proprietà fondamentali

### 1. Distorsione (bias)

$$
\mathrm{bias}(\hat\theta) = E[\hat\theta] - \theta
$$

Lo stimatore è **non distorto** (unbiased) se $\mathrm{bias}(\hat\theta) = 0$ per ogni $\theta$.

**Esempi:**
- $\bar X_n = \frac{1}{n}\sum X_i$ è non distorto per $\mu = E[X]$: $E[\bar X_n] = \mu$.
- $S^2 = \frac{1}{n-1}\sum (X_i - \bar X_n)^2$ è non distorto per $\sigma^2$.
- $\hat\sigma^2_{\text{ML}} = \frac{1}{n}\sum (X_i - \bar X_n)^2$ è **distorto**: $E[\hat\sigma^2_{\text{ML}}] = \frac{n-1}{n}\sigma^2$. Bias $= -\sigma^2/n$ → 0 per $n \to \infty$.

### 2. Varianza
$$
\mathrm{Var}(\hat\theta) = E[(\hat\theta - E[\hat\theta])^2]
$$
Misura la dispersione dello stimatore attorno alla sua media. Cramér-Rao dà il **lower bound**:
$$
\mathrm{Var}(\hat\theta) \geq \frac{1}{n\, I(\theta)}
$$
dove $I(\theta) = E[(\partial_\theta \log f)^2]$ è la **informazione di Fisher**. Stimatori che raggiungono il bound sono detti **efficienti**.

### 3. Errore quadratico medio (MSE)

$$
\mathrm{MSE}(\hat\theta) = E[(\hat\theta - \theta)^2] = \mathrm{Var}(\hat\theta) + \mathrm{bias}(\hat\theta)^2
$$

**Decomposizione bias-varianza** — è la stessa identità che governa il [[Bias-Variance trade-off]] in apprendimento statistico.

## Consistenza

Uno stimatore è **consistente** se converge in probabilità al vero valore al crescere di $n$:
$$
\hat\theta_n \xrightarrow{P} \theta \qquad \text{per } n \to \infty
$$

Condizione sufficiente: $\mathrm{MSE}(\hat\theta_n) \to 0$ (combinazione di bias asintoticamente nullo e varianza decrescente).

**Esempio:** $\bar X_n \to \mu$ per la [[Legge dei Grandi Numeri]].

## Tradeoff bias-varianza

Tra stimatori unbiased, si preferisce quello a varianza minima (UMVUE). Ma a volte uno stimatore **distorto** ha MSE inferiore:

| Stimatore di $\sigma^2$ | Bias | Varianza | MSE (gauss.) |
|---|---|---|---|
| $S^2 = \frac{1}{n-1}\sum (X_i - \bar X)^2$ | 0 | $\frac{2\sigma^4}{n-1}$ | $\frac{2\sigma^4}{n-1}$ |
| $\hat\sigma^2_{ML} = \frac{1}{n}\sum (X_i - \bar X)^2$ | $-\frac{\sigma^2}{n}$ | $\frac{2(n-1)\sigma^4}{n^2}$ | $\frac{(2n-1)\sigma^4}{n^2}$ |

Per $n$ piccolo, $\hat\sigma^2_{ML}$ ha MSE inferiore nonostante sia distorto.

## Sufficienza

Una statistica $T(X_1, \ldots, X_n)$ è **sufficiente** per $\theta$ se la distribuzione condizionata di $\mathbf{X}$ dato $T$ non dipende da $\theta$. Equivalente: $T$ contiene tutta l'informazione su $\theta$.

**Teorema di fattorizzazione (Fisher-Neyman):** $T$ è sufficiente sse $f(\mathbf{x} \mid \theta) = h(\mathbf{x})\, g(T(\mathbf{x}), \theta)$.

**Rao-Blackwell:** se $\hat\theta$ è non distorto e $T$ sufficiente, allora $\hat\theta' = E[\hat\theta \mid T]$ è non distorto e ha varianza $\leq$ originale. La sufficienza permette di "ridurre" lo stimatore migliorandolo (cfr. [[Attesa condizionata]]).

## Costruzione di stimatori

Tre strategie standard:

| Metodo | Stimatore |
|---|---|
| **Metodo dei momenti** | risolvi $\frac{1}{n}\sum X_i^k = E_\theta[X^k]$ per $k = 1, 2, \ldots$ |
| **[[Stima di Massima Verosimiglianza\|MLE]]** | $\hat\theta = \arg\max_\theta \prod_i f(x_i \mid \theta)$ |
| **[[Stima MAP]]** | $\hat\theta = \arg\max_\theta f(\mathbf{x} \mid \theta) g(\theta)$ |

MLE è asintoticamente unbiased, efficiente, e normale (sotto regolarità). Per $n$ piccolo MAP/Bayes possono battere MLE in MSE.

## Connessioni

- Estensione probabilistica: [[Variabile aleatoria]], [[Valore atteso]], [[Varianza e covarianza]]
- Decomposizione: [[Bias-Variance trade-off]] (versione "stimatore di funzione" in apprendimento)
- Paradigmi: [[Stima di Massima Verosimiglianza]], [[Stima MAP]], [[Apprendimento Bayesiano]]
- Convergenza: [[Legge dei Grandi Numeri]] (consistenza di $\bar X_n$)
- Indici: [[Media campionaria]], [[Varianza campionaria]]
- Applicazione: [[Statistica descrittiva]], [[Statistica inferenziale]]

## Persone

- **Ronald Fisher** ([[Fisher, Ronald]]): MLE, sufficienza, informazione di Fisher.
- **Cramér** e **Rao**: lower bound della varianza.
- **Lehmann-Scheffé:** UMVUE tramite sufficienza completa.

## Fonti

- [[Dispense ProbStat — Galletti]] (§4, pp. 31-33)
- [[Dispense MatML — Galletti]] (§2 — MLE, MAP, framework)
