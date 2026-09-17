---
tipo: concetto
titolo: Teoria delle grandi deviazioni
tag: [mmf, probabilità, statistica]
cluster: fisica
fonti: 1
ultima-modifica: 2026-05-06
---

# Teoria delle grandi deviazioni

Stima la probabilità di eventi **lontani dalla media** (molto al di là di ciò che il TLC descrive). Per $u_n = (X_1+\cdots+X_n)/n$ con $X_i$ i.i.d., $\mathbb{E}[u_n] = \mu$:

## Bound di Cramér

$$P(u_n \geq u) \leq e^{-n\Omega_X(u)}, \quad u > \mu$$

La **funzione di tasso** (o funzione di Cramér) è:

$$\Omega_X(u) = -\min_{\lambda \geq 0}\left[\log\zeta_X(\lambda) - \lambda u\right] = -\min_\lambda\left[K_X(\lambda) - \lambda u\right]$$

dove $\zeta_X(\lambda) = \mathbb{E}[e^{\lambda X}]$ è la MGF e $K_X(\lambda) = \log\zeta_X(\lambda)$ è la funzione generatrice dei cumulanti.

**Proprietà di $\Omega$:**
- $\Omega(\mu) = 0$, $\Omega'(\mu) = 0$
- $\Omega''(u) \leq 0$ (concava)
- $\Omega(u) \leq 0$ per $u \neq \mu$

Il bound è del tipo $P(u_n \geq u) \leq e^{nC}$ con $C < 0$.

**Collegamento con il TLC:** espandendo al second'ordine, $\Omega(u) \approx -\frac{(u-\mu)^2}{2\sigma^2}$, che ritrova la stima gaussiana.

## Distribuzioni dei valori estremi

Per il massimo $M_n = \max(X_1,\ldots,X_n)$, standardizzato come $\hat{M}_n = (M_n - a_n)/b_n$, ci sono tre famiglie limite universali:

### Distribuzione di Gumbel
Per variabili con code leggere ($\mathbb{E}[X]=\mu$, $\text{Var}(X)=\sigma^2 < \infty$):

$$G(x) = e^{-e^{-x}}, \quad a_n = \log n, \quad b_n = 1$$

$M_n \approx \log n + Z$ con $Z$ distribuita secondo Gumbel.

### Distribuzione di Fréchet
Per variabili con coda pesante (tipo Pareto $p(x) \sim \alpha x^{-\alpha-1}$ con $\alpha > 0$):

$$G_F(x) = e^{-x^{-\alpha}}, \quad b_n = n^{1/\alpha}$$

$M_n \sim n^{1/\alpha}\hat{M}$.

### Riepilogo

| Caso | $\mathbb{E}[X]$ | $\text{Var}(X)$ | Massimo $M_n$ | Somma $S_n$ |
|---|---|---|---|---|
| $\alpha > 2$ | $\mu$ | $\sigma^2 < \infty$ | $\ll \sqrt{n}$ (Gumbel) | $n\mu + \sqrt{n}\sigma Z$ |
| $1 < \alpha \leq 2$ | $\mu$ | $\infty$ | $\sim n^{1/\alpha}\hat{M}$ (Fréchet) | $n\mu + n^{1/\alpha}Y$ |
| $0 < \alpha \leq 1$ | $\infty$ | $\infty$ | $\sim n^{1/\alpha}\hat{M}$ | $\sim n^{1/\alpha}Y$ (Lévy) |

## Connessioni

- Prerequisiti: [[Funzione generatrice dei momenti]], [[Legge dei Grandi Numeri]]
- TLC: [[Spazio di probabilità]] (contesto generale)
- In fisica statistica: [[Modello di Ising]] (grandi deviazioni per la magnetizzazione)
- Corsi: [[Modelli Matematici per la Fisica II]]

## Fonti

- [[Dispense MMFII — Galletti]] (§1.3, pp. 12-18)
