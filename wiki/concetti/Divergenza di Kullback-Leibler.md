---
tipo: concetto
titolo: Divergenza di Kullback-Leibler
tag: [probabilità, teoria-informazione, ml]
cluster: probabilistica
fonti: 2
ultima-modifica: 2026-05-04
---

# Divergenza di Kullback-Leibler

Misura "distanza" (in senso lato) tra due distribuzioni di probabilità $P$ e $Q$:

$$
D_{KL}(P \| Q) = \sum_x p(x) \log \frac{p(x)}{q(x)} \qquad \text{(discreto)}
$$

$$
D_{KL}(P \| Q) = \int p(x) \log \frac{p(x)}{q(x)}\, dx \qquad \text{(continuo)}
$$

## Proprietà fondamentali

- **Non negativa**: $D_{KL}(P \| Q) \geq 0$, con uguaglianza sse $P = Q$ (disuguaglianza di Gibbs).
- **NON simmetrica**: $D_{KL}(P \| Q) \neq D_{KL}(Q \| P)$. Per questo *non* è una metrica vera.
- **NON soddisfa la disuguaglianza triangolare**.

L'asimmetria è una **feature**, non un bug:

- $D_{KL}(P \| Q)$ grande quando esiste un evento con $p(x)$ alto ma $q(x)$ basso (trascurato dal modello).
- È piccola quando dove $p(x) \approx 0$ il valore di $q(x)$ può essere qualunque.

## Connessione con la cross-entropy

$$
D_{KL}(P \| Q) = H(P, Q) - H(P)
$$

dove $H(P, Q) = -\sum p \log q$ è la [[Cross-entropy]] e $H(P) = -\sum p \log p$ è l'entropia di $P$. Minimizzare la cross-entropy a $P$ fissa equivale a minimizzare la KL.

## Usi in ML

- **Loss in classificazione** (via [[Cross-entropy]]).
- **Variational inference**: si approssima una distribuzione complessa $P$ con una semplice $Q$ minimizzando $D_{KL}(Q \| P)$ (o $D_{KL}(P \| Q)$, scelte diverse).
- **VAE** (autoencoder variazionali): nel termine di regolarizzazione del prior.
- **[[t-SNE]]** e **[[Stochastic Neighbor Embedding|SNE]]**: come stress dell'embedding.

## Connessione con MLE (apprendimento non supervisionato)

Nel framework MatML, il rischio teorico in apprendimento non supervisionato con loss logaritmica è esattamente la KL:

$$
\ell(g) = \mathbb{E}_f\!\left[\log \frac{f(X)}{g(X|\theta)}\right] = D_{KL}(f \| g(\cdot|\theta)) + \mathrm{const}
$$

Minimizzare questo rischio rispetto a `θ` è equivalente a massimizzare `E[log g(X|θ)]`, che sull'osservato diventa la [[Stima di Massima Verosimiglianza|log-likelihood]]:

$$
\hat\theta_{ML} = \arg\max_\theta \sum_{i=1}^n \log g(x_i|\theta)
$$

Nel framework [[Apprendimento Bayesiano|Bayesiano]], il rischio della densità marginale è anch'esso una KL:

$$
\ell(g) = D_{KL}\!\left(f(\tau) \,\Big\|\, \int g(\tau|\theta) w(\theta)\,d\theta\right) + \mathrm{const}
$$

## Disuguaglianza di Gibbs

La non-negatività di $D_{KL}$ segue dalla [[Disuguaglianza di Jensen]] applicata a $-\log$ (funzione convessa):

$$
D_{KL}(P \| Q) = \mathbb{E}_P\!\left[-\log \frac{q(X)}{p(X)}\right] \geq -\log \mathbb{E}_P\!\left[\frac{q(X)}{p(X)}\right] = -\log 1 = 0
$$

## Collegamenti

- Cugina: [[Cross-entropy]]
- Persone: [[Kullback, Solomon]], [[Leibler, Richard A.]]
- Usato in: [[t-SNE]], [[Stochastic Neighbor Embedding]], [[Apprendimento Bayesiano]], [[Stima di Massima Verosimiglianza]]
- Non-negatività via: [[Disuguaglianza di Jensen]]
- Riapparirà in: [[Modelli Matematici per la Fisica II]] (principio di massima entropia).

## Fonti

- [[Dispense Machine Learning — Galletti]] (§7.3-7.4, pp. 24-25)
- [[Dispense MatML — Galletti]] (esempio 2.8, pp. 25-26)
