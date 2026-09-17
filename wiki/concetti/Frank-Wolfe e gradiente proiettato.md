---
tipo: concetto
titolo: Frank-Wolfe e gradiente proiettato
tag: [ottimizzazione, ottimizzazione-vincolata, algoritmi]
cluster: ottimizzazione
fonti: 1
ultima-modifica: 2026-05-04
---

# Frank-Wolfe e gradiente proiettato

Due metodi per l'ottimizzazione vincolata $\min_{x \in S} f(x)$ con $S$ chiuso convesso. Entrambi generano iterazioni che restano in $S$ e convergono globalmente.

## Premessa: direzioni ammissibili e di discesa

$d \in \mathbb{R}^n$ è **ammissibile** in $\bar{x} \in S$ (convesso) se $\bar{x} + d \in S$. Per $S$ convesso, $d = x - \bar{x}$ per qualsiasi $x \in S$ è ammissibile.

**Condizioni necessarie di ottimalità** (S convesso): $\bar{x}$ è minimo locale $\Rightarrow$ non esiste direzione ammissibile e di discesa simultaneamente, ovvero $\nabla f(\bar{x})^T(x-\bar{x}) \geq 0 \;\forall x \in S$.

Equivalentemente (tramite [[Proiezione su insiemi convessi]]): $\bar{x} = p(\bar{x} - s\nabla f(\bar{x})) \;\forall s > 0$.

## Metodo di Frank-Wolfe

**Idea**: linearizzare $f$ in $x_k$ e minimizzare l'approssimazione lineare su $S$.

**Passo**:
1. Risolvere il **sottoproblema lineare**: $\hat{x} = \arg\min_{x \in S} \nabla f(x_k)^T x$
2. Direzione: $d_k = \hat{x} - x_k$ (ammissibile in $x_k$ perché $S$ convesso, di discesa se $x_k$ non critico)
3. $x_{k+1} = x_k + \alpha_k d_k$ con $\alpha_k$ da [[Metodo di Armijo]] ($\Delta_k = 1$)

**Criterio d'arresto**: se $\nabla f(x_k)^T(\hat{x} - x_k) \geq 0$ allora $x_k$ è critico.

**Vantaggi**: il sottoproblema lineare su poliedri si risolve efficacemente (es. metodo del simplesso per $S = \{Ax \leq b\}$).

**Convergenza globale**: dimostrata sotto ipotesi standard ($f \in C^1$, $L_0$ compatto).

## Metodo del gradiente proiettato

**Idea**: spostarsi nella direzione dell'antigradiente e proiettare su $S$.

**Passo**:
1. Calcolare il **punto proiettato**: $\hat{x}_k = p(x_k - s \nabla f(x_k))$, con $s > 0$
2. Direzione: $d_k = \hat{x}_k - x_k$
   - Se $d_k = 0$: $x_k$ è critico ($x_k = p(x_k - s\nabla f(x_k))$, condizione di ottimalità)
   - Se $d_k \neq 0$: $\nabla f(x_k)^T d_k < 0$ (si dimostra)
3. $x_{k+1} = x_k + \alpha_k d_k$ con $\alpha_k$ da Armijo ($\Delta_k = 1$)

**Vantaggi**: su box constraints la proiezione è in forma chiusa (componente per componente), costo $O(n)$.

**Convergenza globale**: dimostrata.

## Confronto algoritmico

| Aspetto | Frank-Wolfe | Gradiente proiettato |
|---|---|---|
| Passo chiave | minimizzazione lineare su $S$ | proiezione su $S$ |
| Efficiente se | $S$ poliedro (simplesso) | $S$ box, sfera |
| Costo/iter | dipende da $S$ | $O(n)$ per box |
| Iterazioni | più lente (convergenza sublineare) | più veloci (convergenza lineare) |

## Caso $S$ vincolato generale (KKT)

Per $S = \{g_i(x) \leq 0, h_j(x) = 0\}$ con $f, g, h \in C^1$ non necessariamente lineari, né Frank-Wolfe né il gradiente proiettato si applicano direttamente. Si usano metodi basati sulle condizioni [[Condizioni KKT]] (penalizzazione, Lagrangiano aumentato, SQP).

## Collegamento con i corsi

- [[Ottimizzazione]]: §6.4-6.5, metodi principali per vincolato.
- [[Machine Learning]]: il gradiente proiettato compare nell'ottimizzazione con vincoli di norma (regularizzazione LASSO, SVM).
- [[Discesa del gradiente]]: il gradiente proiettato è la generalizzazione vincolata della discesa del gradiente.

## Fonti

- [[Dispense Ottimizzazione — Galletti]] (§6.4-6.5, pp. 53-54)
