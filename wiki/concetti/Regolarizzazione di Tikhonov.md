---
tipo: concetto
titolo: Regolarizzazione di Tikhonov
tag: [ml, ottimizzazione, regressione]
cluster: ml
ultima-modifica: 2026-04-30
---

# Regolarizzazione di Tikhonov (ridge)

Si aggiunge un termine di **penalità $L^2$** alla loss per affrontare problemi sottodeterminati o mal condizionati:

$$
\min_x \|Ax - b\|_2^2 + \alpha \|x\|_2^2
$$

con $\alpha > 0$ iperparametro. La soluzione è ancora in **forma chiusa**:

$$
(A^\top A + \alpha I)\, x = A^\top b
$$

A differenza dell'equazione normale pura ([[Regressione lineare]]), $A^\top A + \alpha I$ è sempre **invertibile** per $\alpha > 0$ — un trick numerico oltre che statistico.

## Perché funziona

- Riduce i parametri liberi *effettivi*: shrinkage.
- Penalizza in particolare i $|x_i|$ grandi (la penalità $L^2$ cresce quadraticamente).
- Stabilizza la soluzione quando $A^\top A$ è singolare ($A$ "larga": più parametri che dati).

## Generalizzazioni

In forma generale: $\min_x \|Ax - b\|_p^p + \alpha \rho(x)$.

- **$\rho(x) = \|x\|_1$ (L1 / Lasso):** induce **sparsità** — molti coefficienti vanno esattamente a zero. Vedi [[Lasso e Elastic Net]].
- **Elastic Net:** combina L1 e L2. Vedi [[Lasso e Elastic Net]].
- **$\rho(x) = \|D x\|_2^2$:** smoothing, penalizza variazioni adiacenti tramite l'operatore di differenze $D$.
- **$\rho(x) = \|D x\|_1$:** total variation, preserva i salti.

## Contesto ML: Ridge regression

Nel contesto della regressione lineare, la Ridge (Tikhonov con $\rho = L_2$) viene usata con predittori **fortemente correlati** dove la pseudoinversa pura è instabile. La soluzione $(X^\top X + \lambda I)^{-1} X^\top y$ è sempre ben definita per $\lambda > 0$.

## Connessione con la stima MAP

La regolarizzazione Tikhonov equivale a una prior gaussiana sui pesi nella [[Stima MAP]]: $p(w) = \mathcal{N}(0, \sigma^2/\lambda)$.

## Collegamenti

- Strumento contro: [[Overfitting e underfitting]]
- Caso particolare di: [[Regressione lineare]] con penalità
- Estensioni L1 e miste: [[Lasso e Elastic Net]]
- Equivalente Bayesiano: [[Stima MAP]]
- Persone: [[Tikhonov]]
- Discusso in: [[Machine Learning]], [[Informatica per il Machine Learning]] (§3.2)

## Fonti

- [[Dispense Machine Learning — Galletti]] (§3.4, pp. 12-13)
