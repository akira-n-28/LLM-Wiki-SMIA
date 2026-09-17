---
tipo: concetto
titolo: Proiezione su insiemi convessi
tag: [ottimizzazione, ottimizzazione-vincolata, geometria]
cluster: ottimizzazione
fonti: 1
ultima-modifica: 2026-05-04
---

# Proiezione su insiemi convessi

Operazione fondamentale nell'ottimizzazione vincolata: trovare il punto di $S$ più vicino a $x$.

## Definizione

$S \subseteq \mathbb{R}^n$ non vuoto, chiuso, convesso. La **proiezione** di $x \in \mathbb{R}^n$ su $S$ è:
$$
y^* = p(x) = \arg\min_{y \in S} \|x - y\|
$$

**Esistenza e unicità**: $F_x(y) = \frac12 \|x - y\|^2$ è strettamente convessa e coerciva su $S$ chiuso convesso $\neq \emptyset$ $\Rightarrow$ esiste unico $y^*$.

- Se $S$ non è chiuso: la proiezione non esiste (il minimo cade sul bordo ma non appartiene a $S$).
- Se $S$ non è convesso: l'unicità fallisce per almeno un $x$.

## Caratterizzazione dell'ottimalità

$$
y^* = p(x) \iff (x - y^*)^T (y - y^*) \leq 0 \quad \forall y \in S
$$

Geometricamente: l'angolo tra $(x - y^*)$ e qualsiasi vettore $(y - y^*)$ è ottuso ($\geq \pi/2$).

**Dimostrazione**: $y^*$ è il minimo locale (e globale, per convessità stretta) di $F_x(y) = \frac12\|x-y\|^2$ $\Rightarrow \nabla F_x(y^*)^T(y - y^*) \geq 0$ $\Rightarrow (y^* - x)^T(y - y^*) \geq 0$ $\Rightarrow (x - y^*)^T(y - y^*) \leq 0$.

**Proprietà di non espansività**: $\|p(x) - p(z)\| \leq \|x - z\| \quad \forall x, z \in \mathbb{R}^n$ (la proiezione è una contrazione).

## Esempi in forma chiusa

**Vincoli di non negatività** ($S = \{y \geq 0\}$):
$$
p(x)_i = \max(x_i, 0)
$$

**Vincoli di box** ($S = \{l \leq y \leq u\}$):
$$
p(x)_i = \min\bigl(\max(x_i, l_i),\, u_i\bigr)
$$

**Sfera** ($S = \{y: \|y\| \leq R\}$):
$$
p(x) = \begin{cases} x & \text{se } \|x\| \leq R \\ R \cdot x/\|x\| & \text{se } \|x\| > R \end{cases}
$$

**Poliedro generico** ($S = \{Ax \leq b\}$): no forma chiusa, si risolve con un QP.

## Connessione con le condizioni di ottimalità vincolata

Per $f \in C^1$, $S$ convesso, $\bar{x} \in S$:
$$
\nabla f(\bar{x})^T(x - \bar{x}) \geq 0 \;\forall x \in S \iff \bar{x} = p\bigl(\bar{x} - s\nabla f(\bar{x})\bigr) \quad \forall s > 0
$$

Questa equivalenza è alla base degli algoritmi [[Frank-Wolfe e gradiente proiettato]].

## Algoritmi che usano la proiezione

- **[[Frank-Wolfe e gradiente proiettato|Gradiente proiettato]]**: $x_{k+1} = x_k + \alpha_k (p(x_k - \nabla f(x_k)) - x_k)$
- **Projected gradient descent**: variante senza line search, $x_{k+1} = p(x_k - \mu \nabla f(x_k))$
- **ADMM, ProxGrad**: metodi moderni per $l_1$-regularizzazione (LASSO, sparse ML)

## Collegamento con i corsi

- [[Ottimizzazione]]: §6.3, building block per [[Frank-Wolfe e gradiente proiettato]].
- [[Machine Learning]]: la proiezione su norma-$l_1$ ball è legata alla regolarizzazione LASSO.
- [[Metodi Numerici]]: la proiezione su poliedri è un QP risolto con metodi specifici.

## Fonti

- [[Dispense Ottimizzazione — Galletti]] (§6.3, pp. 49-53)
