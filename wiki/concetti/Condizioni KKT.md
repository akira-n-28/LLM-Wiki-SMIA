---
tipo: concetto
titolo: Condizioni KKT
tag: [ottimizzazione, ottimizzazione-vincolata, matematica-applicata]
cluster: ottimizzazione
fonti: 1
ultima-modifica: 2026-05-04
---

# Condizioni KKT (Karush-Kuhn-Tucker)

Condizioni necessarie di ottimalità per il problema vincolato generale:
$$
\min_{x \in S} f(x), \qquad S = \{x \in \mathbb{R}^n : g_i(x) \leq 0 \; (i=1,\ldots,m),\; h_j(x) = 0 \; (j=1,\ldots,p)\}
$$

Generalizzazione delle condizioni $\nabla f = 0$ al caso con vincoli.

## Funzione Lagrangiana

$$
L(x, \lambda_0, \lambda, \mu) = \lambda_0 f(x) + \sum_{i=1}^m \lambda_i g_i(x) + \sum_{j=1}^p \mu_j h_j(x)
$$

dove $\lambda_i \geq 0$ sono i **moltiplicatori di Lagrange** per i vincoli di disuguaglianza e $\mu_j$ per quelli di uguaglianza.

## Condizioni di Fritz-John

**Teorema**: se $x^*$ è un punto di minimo locale ammissibile, allora $\exists \lambda_0^*, \lambda_1^*, \ldots, \lambda_m^*, \mu_1^*, \ldots, \mu_p^*$ tali che:

1. **Stazionarietà**: $\lambda_0^* \nabla f(x^*) + \sum_i \lambda_i^* \nabla g_i(x^*) + \sum_j \mu_j^* \nabla h_j(x^*) = 0$
2. **Ammissibilità**: $g(x^*) \leq 0$, $h(x^*) = 0$
3. **Complementarità**: $\lambda_i^* g_i(x^*) = 0 \;\forall i \quad$ (equivalente a $\langle \lambda^*, g(x^*) \rangle = 0$)
4. **Non negatività**: $(\lambda_0^*, \lambda^*) \geq 0$
5. **Non trivialità**: $(\lambda_0^*, \lambda^*, \mu^*) \neq (0,0,0)$

Se $\lambda_0^* = 0$ le condizioni sono equivalenti all'ammissibilità e **non sono significative**. Le condizioni di regolarità garantiscono $\lambda_0^* > 0$.

## Condizioni KKT (forma standard, $\lambda_0 = 1$)

Sotto **condizioni di regolarità dei vincoli** (soddisfatte se: vincoli lineari, oppure gradienti dei vincoli attivi linearmente indipendenti), se $x^*$ è un punto di minimo locale ammissibile, $\exists \lambda^* \geq 0$, $\mu^*$ tali che:

$$
\boxed{\nabla f(x^*) + \nabla g(x^*)^T \lambda^* + \nabla h(x^*)^T \mu^* = 0}
$$
$$
\lambda^* \geq 0, \quad g(x^*) \leq 0, \quad h(x^*) = 0, \quad (\lambda^*)^T g(x^*) = 0
$$

**Condizione di complementarità**: $\lambda_i^* g_i(x^*) = 0$ — o il moltiplicatore è zero (vincolo non attivo) o il vincolo è attivo ($g_i(x^*) = 0$).

**Vincoli attivi**: $I(x^*) = \{i: g_i(x^*) = 0\}$.

## Condizioni di regolarità

Garantiscono $\lambda_0^* > 0$ (da Fritz-John → KKT):
- **Vincoli lineari**: sempre soddisfatte.
- **LICQ** (Linear Independence Constraint Qualification): i gradienti $\{\nabla g_i(x^*)\}_{i \in I(x^*)} \cup \{\nabla h_j(x^*)\}_{j=1}^p$ sono linearmente indipendenti.

## Caso convesso (condizioni necessarie e sufficienti)

Se $f$ e $g_i$ sono convesse, $h_j$ affini, le condizioni KKT sono **necessarie e sufficienti** per il minimo globale.

## Interpretazione geometrica

Il gradiente $\nabla f(x^*)$ è combinazione conica dei gradienti dei vincoli attivi: non può esistere una direzione ammissibile e di discesa contemporaneamente.

## Esempio sintetico

Per $\min f(x)$ con $g_1(x) \leq 0$ e $h_1(x) = 0$:
$$
\nabla f(x^*) + \lambda_1^* \nabla g_1(x^*) + \mu_1^* \nabla h_1(x^*) = 0
$$
$$
\lambda_1^* \geq 0, \quad \lambda_1^* g_1(x^*) = 0
$$

Se $g_1(x^*) < 0$ (vincolo non attivo) $\Rightarrow \lambda_1^* = 0$ (il vincolo non conta all'ottimo). Se $g_1(x^*) = 0$ (vincolo attivo) $\Rightarrow \lambda_1^*$ può essere $>0$.

## Collegamento con i corsi

- [[Ottimizzazione]]: §6 (Fritz-John) e §6 (KKT), fondamento dell'ottimizzazione vincolata.
- [[Machine Learning]]: le SVM (Support Vector Machine) si formulano tramite condizioni KKT.
- [[Matematica per il Machine Learning]]: [[Stima MAP]] è un problema vincolato (prior come regularizer).

## Fonti

- [[Dispense Ottimizzazione — Galletti]] (§6, pp. 53-56)
