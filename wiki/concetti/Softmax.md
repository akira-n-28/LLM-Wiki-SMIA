---
tipo: concetto
titolo: Softmax
tag: [ml, reti-neurali, classificazione]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# Softmax

La **softmax** è la generalizzazione della [[Funzione sigmoide]] al caso multiclasse. Mappa un vettore $f \in \mathbb{R}^K$ (logits) in una distribuzione di probabilità su $K$ classi:

$$
\text{softmax}_k(f) = \frac{e^{f_k}}{\sum_{k'=1}^K e^{f_{k'}}}
$$

L'output è in $[0,1]$ e la somma delle $K$ componenti è 1.

## Derivazione probabilistica

Si sceglie la **distribuzione categorica** con $K$ parametri $\lambda_1, \ldots, \lambda_K$ (con $\sum \lambda_k = 1$). Una rete $f[x; \theta] \in \mathbb{R}^K$ produce logits non vincolati — la softmax li converte in probabilità rispettando i vincoli.

La NLL (Negative Log-Likelihood) sul dataset diventa la **cross-entropy multiclasse**:

$$
\mathcal{L}(\theta) = -\sum_{i=1}^N \left[ f_{y_i}[x_i; \theta] - \log \sum_{k=1}^K e^{f_k[x_i; \theta]} \right]
$$

In inferenza: $\hat{y} = \arg\max_k \text{softmax}_k(f[x; \hat\theta])$.

## Differenza con la sigmoide

- **Sigmoide**: classificazione binaria (output scalare in $(0,1)$).
- **Softmax**: classificazione multiclasse (output vettore in $\Delta^{K-1}$).

Per $K = 2$ la softmax si riduce alla sigmoide.

## Uso nel Transformer

Nella **scaled dot-product attention**:
$$
\text{Attention}(Q, K, V) = \text{softmax}\!\left(\frac{QK^\top}{\sqrt{d_k}}\right) V
$$
la softmax normalizza gli alignment scores in pesi di attenzione. Vedi [[Meccanismo di Attention]].

## Costo computazionale

Il termine $\sum_{k'} e^{f_{k'}}$ richiede scorrere tutto il vocabolario $V$ — costoso per $|V| \sim 10^5$. Soluzioni: **Negative Sampling** (Word2Vec) o gerarchie di softmax.

## Collegamenti

- Caso binario: [[Funzione sigmoide]]
- Usata per: classificazione multiclasse, [[Transformer]], [[Language Model]]
- Loss associata: [[Cross-entropy]]
- Discusso in: [[Informatica per il Machine Learning]] (§1, §6)

## Fonti

- [[Dispense InfML — Galletti]] (§1.1, pp. 6-7)
