---
tipo: concetto
titolo: Condizioni di ottimalità
tag: [ottimizzazione, matematica-applicata, analisi]
cluster: ottimizzazione
fonti: 1
ultima-modifica: 2026-05-04
---

# Condizioni di ottimalità

Condizioni che caratterizzano i punti candidati a essere minimi. Si dividono in: necessarie (candidati), sufficienti (certifica l'ottimalità), necessarie-e-sufficienti (equivalenza con la definizione). Gli algoritmi sono figli delle condizioni di ottimalità.

## Caso non vincolato

### Direzione di discesa

$d \in \mathbb{R}^n$, $d \neq 0$ è una **direzione di discesa** per $f$ in $x$ se $\exists \bar{t} > 0$:
$$
f(x + td) < f(x) \quad \forall t \in (0, \bar{t})
$$

**Derivata direzionale**: $Df(x, d) = \lim_{t \to 0^+} \frac{f(x+td)-f(x)}{t} = \nabla f(x)^T d$ (per $f$ differenziabile).

**Condizione sufficiente di discesa del primo ordine**: se $\nabla f(x)^T d < 0$ allora $d$ è di discesa. L'**antigradiente** $-\nabla f(x)$ è sempre una direzione di discesa (quando $\nabla f(x) \neq 0$).

**Condizione sufficiente di discesa del secondo ordine**: se $\nabla f(x)^T d = 0$ e $d^T \nabla^2 f(x) d < 0$ allora $d$ è di discesa (direzione a curvatura negativa).

### Condizione necessaria: nessuna direzione di discesa

Se $\bar{x}$ è un minimo locale non può esistere una direzione di discesa in $\bar{x}$.

**Condizione necessaria del 1° ordine** ($f \in C^1$): se $\bar{x}$ è minimo locale $\Rightarrow \nabla f(\bar{x}) = 0$.

L'insieme $\Omega = \{x: \nabla f(x) = 0\}$ si dice insieme dei **punti stazionari** (o critici).

**Condizione necessaria del 2° ordine** ($f \in C^2$): se $\bar{x}$ è minimo locale $\Rightarrow$
$$
(a)\; \nabla f(\bar{x}) = 0 \qquad (b)\; \nabla^2 f(\bar{x}) \succeq 0
$$

**Condizione sufficiente del 2° ordine** ($f \in C^2$): se $\nabla f(\bar{x}) = 0$ e $\nabla^2 f(\bar{x}) \succ 0$ allora $\bar{x}$ è minimo locale stretto.

### Caso convesso

Se $f \in C^1$ è convessa: $\bar{x}$ è **minimo globale** $\iff \nabla f(\bar{x}) = 0$.

Se $f \in C^1$ è strettamente convessa: il minimo globale è unico.

### Caso quadratico

$f(x) = \frac12 x^T Q x + c^T x$, $Q$ simmetrica:

| Proprietà di $Q$ | Conseguenza |
|---|---|
| $Q$ indefinita | no minimo globale |
| $Q \succeq 0$ + sistema $Qx+c=0$ ammette soluzione | esiste minimo globale |
| $Q \succ 0$ | minimo globale unico: $x^* = -Q^{-1}c$ |
| $Q \succeq 0$ singolare | infiniti minimi globali |

## Caso vincolato (S convesso)

**Condizione necessaria**: se $\bar{x} \in S$ è minimo locale:
$$
\nabla f(\bar{x})^T(x - \bar{x}) \geq 0 \quad \forall x \in S
$$

**Condizione necessaria e sufficiente** (se $f$ convessa): $\bar{x} \in S$ è minimo globale $\iff$ la condizione sopra vale.

**Caso con box constraints** ($l \leq x \leq u$): le condizioni si scrivono componente per componente:
$$
\frac{\partial f(\bar{x})}{\partial x_i} \begin{cases} \geq 0 & \text{se } \bar{x}_i = l_i \\ = 0 & \text{se } l_i < \bar{x}_i < u_i \\ \leq 0 & \text{se } \bar{x}_i = u_i \end{cases}
$$

## Condizioni KKT (caso vincolato generale)

Per $S = \{x: g_i(x) \leq 0, h_j(x) = 0\}$, vedi [[Condizioni KKT]].

## Collegamento con i corsi

- [[Ottimizzazione]]: §1.5 e §6, nucleo teorico del corso.
- [[Matematica per il Machine Learning]]: le condizioni $\nabla E = 0$ per [[ERM]] sono esattamente le condizioni del 1° ordine.
- [[Metodi Numerici]]: radici di $\nabla f = 0$ tramite [[Metodo di Newton (ottimizzazione)]].

## Fonti

- [[Dispense Ottimizzazione — Galletti]] (§1.5, pp. 18-23)
