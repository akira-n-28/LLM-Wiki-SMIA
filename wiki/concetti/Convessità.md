---
tipo: concetto
titolo: Convessità
tag: [ottimizzazione, matematica-applicata, analisi]
cluster: ottimizzazione
fonti: 1
ultima-modifica: 2026-05-04
---

# Convessità

La convessità è la proprietà chiave che garantisce la coincidenza tra minimi locali e globali — fondamento di gran parte dell'ottimizzazione in ML.

## Insiemi convessi

$S \subseteq \mathbb{R}^n$ è **convesso** se:
$$
\forall x, y \in S, \; \forall \lambda \in [0,1]: \quad (1-\lambda)x + \lambda y \in S
$$

Esempi convessi: $\emptyset$, $\mathbb{R}^n$, $\{x_0\}$ (singleton), sfere aperte $B(x^*,\rho)$, iperpiani $\{x: w^T x = c\}$, semispazi $\{x: w^T x \leq c\}$, poliedri $\{x: Ax \leq b\}$.

**Proposizione**: l'intersezione (finita o infinita) di insiemi convessi è convessa.

**Insieme generato da funzione convessa**: se $g: \mathbb{R}^n \to \mathbb{R}$ è convessa, allora $S = \{x: g(x) \leq 0\}$ è convesso.

## Funzioni convesse

$f: \mathbb{R}^n \to \mathbb{R}$ è **convessa** su $S$ convesso se:
$$
\forall x, y \in S: \quad f\bigl((1-\lambda)x + \lambda y\bigr) \leq (1-\lambda)f(x) + \lambda f(y), \quad \forall \lambda \in [0,1]
$$
(la funzione è sotto la secante tra due punti qualsiasi).

È **strettamente convessa** se la disuguaglianza è stretta per $x \neq y$, $\lambda \in (0,1)$.

### Caratterizzazioni equivalenti

**Per funzioni $C^1$** ($S$ convesso aperto):
$$
f \text{ convessa} \iff f(y) \geq f(x) + \nabla f(x)^T(y-x) \quad \forall x,y \in S
$$
(il grafico è sopra ogni piano tangente).

**Per funzioni $C^2$**:
$$
f \text{ convessa} \iff \nabla^2 f(x) \succeq 0 \; \forall x \in S \quad (\text{Hessiana semidefinita positiva})
$$
$$
f \text{ strettamente convessa} \Leftarrow \nabla^2 f(x) \succ 0 \; \forall x \in S \quad (\text{condizione sufficiente})
$$
Per funzioni quadratiche la condizione è necessaria e sufficiente.

### Esempi importanti

| Funzione | $\nabla f$ | $\nabla^2 f$ | Convessa? |
|---|---|---|---|
| $f(x) = c^T x$ | $c$ | $0$ | sì (e concava) |
| $f(x) = \frac12 x^T Q x + c^T x$, $Q \succ 0$ | $Qx + c$ | $Q \succ 0$ | strettamente convessa |
| $f(x) = \frac12 \|Ax - b\|^2$ | $A^T(Ax-b)$ | $A^T A \succeq 0$ | convessa |
| $\log(1 + e^{-t})$ | — | $e^{-t}/(1+e^{-t})^2 > 0$ | strettamente convessa |

**Regressione logistica**: la somma $\sum_p \log(1+e^{-y_p w^T x_p})$ è convessa in $w$ (ogni termine è composizione di funzione convessa con lineare).

## Proprietà chiave per l'ottimizzazione

**Proposizione (locale = globale)**: se $S$ è convesso e $f$ è convessa su $S$, ogni minimo locale è minimo globale. L'insieme dei minimi globali $X^*$ è convesso.

**Proposizione (unicità)**: se $f$ è strettamente convessa su $S$ convesso, il minimo globale è unico (se esiste).

**Condizioni necessarie e sufficienti**: se $f$ è convessa e $C^1$, allora $\bar{x} \in \mathbb{R}^n$ è minimo globale $\iff \nabla f(\bar{x}) = 0$.

**Caso vincolato** (S convesso): $\bar{x} \in S$ è minimo globale $\iff \nabla f(\bar{x})^T(x - \bar{x}) \geq 0 \;\forall x \in S$.

## Funzione concava

$f$ è **concava** su $S$ convesso se $-f$ è convessa. Una funzione lineare è sia convessa che concava ($H = 0$). Per $f$ concava (non costante): ogni minimo globale è sulla frontiera di $S$.

## Insiemi di livello

$L_\alpha^f = \{x \in \mathbb{R}^n: f(x) \leq \alpha\}$.

Se $f$ è convessa, $L_\alpha^f$ è un insieme convesso. Se $f$ è coerciva, $L_\alpha^f$ è compatto per ogni $\alpha$ (→ esistenza del minimo).

## Collegamento con i corsi

- [[Ottimizzazione]]: la convessità è il filo conduttore di tutto il corso.
- [[Funzione di perdita]] ([[Matematica per il Machine Learning]]): la convessità della loss garantisce l'ottimalità globale del minimo trovato da [[ERM]].
- [[Regressione logistica]]: la sua loss è convessa, quindi ottimizzabile globalmente con metodi di discesa.

## Fonti

- [[Dispense Ottimizzazione — Galletti]] (§1.2, §1.3, pp. 11-17)
