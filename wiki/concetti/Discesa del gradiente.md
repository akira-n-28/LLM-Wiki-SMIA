---
tipo: concetto
titolo: Discesa del gradiente
tag: [ottimizzazione, ml]
cluster: ottimizzazione
fonti: 2
ultima-modifica: 2026-05-04
---

# Discesa del gradiente (gradient descent)

Metodo iterativo per minimizzare una funzione differenziabile $f : \mathbb{R}^n \to \mathbb{R}$. Si parte da $x^{(0)}$ e si itera:

$$
x^{(t+1)} = x^{(t)} - \alpha \nabla f(x^{(t)})
$$

Il **gradiente** è ortogonale alle curve di livello e indica la direzione di massima crescita di $f$; ci muoviamo nel verso opposto. Il parametro $\alpha > 0$ è il **learning rate**.

## Punti di attenzione

- Si ferma in un **punto stazionario** $\nabla f(x^*) = 0$. Se $f$ è convessa è il minimo globale; in generale può essere un minimo locale o sella.
- **Sensibilità a $\alpha$**:
  - troppo piccolo → convergenza lenta;
  - troppo grande → oscillazioni o divergenza.
- Il passo effettivo è $\alpha \|\nabla f\|$. Strategie: line search euristica, learning rate scheduling.

## Metodo della discesa più ripida (steepest descent)

La direzione ottimale minimizza il prodotto scalare $\nabla f(x_k)^T d$ sotto vincolo $\|d\|=1$. Per Cauchy-Schwarz:
$$
\min_{\|d\|=1} \nabla f(x_k)^T d \quad \Rightarrow \quad d_k = -\frac{\nabla f(x_k)}{\|\nabla f(x_k)\|}
$$
La direzione dell'antigradiente normalizzata è la direzione di discesa massima.

## Convergenza con passo costante (gradient Lipschitz)

Se $f \in C^1(\mathbb{R}^n)$ con gradiente **Lipschitz-continuo** di costante $L > 0$ ($\|\nabla f(x) - \nabla f(y)\| \leq L\|x-y\|$):

**Lemma di discesa**: $f(x + \alpha d) \leq f(x) + \alpha \nabla f(x)^T d + \frac12 \alpha^2 L \|d\|^2$.

**Proposizione (convergenza)**: $x_{k+1} = x_k - \mu \nabla f(x_k)$ con $\mu < 2/L$ garantisce $f(x_{k+1}) < f(x_k)$ e ogni punto limite è stazionario. Se $\mu \leq (2-\varepsilon)/L$ la successione ammette punti limite.

**Step ottimale teorico**: $\mu = 1/L$. Praticamente $L$ non è nota → si usa [[Metodo di Armijo]].

## Line search

- **Esatta** (solo caso quadratico $f = \frac12 x^T Qx + c^T x$): $\alpha_k = -\nabla f(x_k)^T d_k / (d_k^T Q d_k)$.
- **Inesatta** ([[Metodo di Armijo]]): garantisce decremento sufficiente per qualsiasi $f \in C^1$.

## Momentum

Si introduce una velocità $v$ che accumula i gradienti passati con decadimento $\lambda$:

$$
v^{(t+1)} = \lambda v^{(t)} - \alpha \nabla f(x^{(t)}), \qquad x^{(t+1)} = x^{(t)} + v^{(t+1)}
$$

Equivalentemente in forma chiusa: $x^{(t+1)} = x^{(0)} - \alpha \sum_{i=0}^{t} \frac{1 - \lambda^{t+1-i}}{1 - \lambda} \nabla f(x^{(i)})$. Il momentum aiuta a smussare oscillazioni e accelerare nelle valli strette.

## Versioni

- **GD batch**: usa tutti i dati a ogni passo. Costoso ma stabile.
- **[[Stochastic Gradient Descent|SGD]]**: usa un solo campione (o mini-batch) — molto più veloce, gradiente rumoroso.

## Collegamenti

- Variante stocastica: [[Stochastic Gradient Descent]]
- Necessario quando manca forma chiusa: [[Regressione logistica]], [[Multi-Layer Perceptron]]
- Calcolo efficiente del gradiente per le reti: [[Backpropagation]]
- Discusso in: [[Machine Learning]], [[Ottimizzazione]] (da collegare con ingest)

## Fonti

- [[Dispense Machine Learning — Galletti]] (§4, pp. 13-15)
- [[Dispense Ottimizzazione — Galletti]] (§3.2-3.5, §4.1, pp. 25-31)
