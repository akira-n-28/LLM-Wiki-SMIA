---
tipo: concetto
titolo: Meccanica Lagrangiana
tag: [mmf, meccanica, calcolo-variazionale]
cluster: fisica
fonti: 1
ultima-modifica: 2026-05-06
---

# Meccanica Lagrangiana

Reformulazione della meccanica newtoniana che lavora con **coordinate generalizzate** $q \in \Omega \subseteq \mathbb{R}^n$ invece di coordinate cartesiane.

## Lagrangiana

$$L(q, \dot{q}, t) = T - U$$

dove $T = \frac{1}{2}\langle\dot{q}, A\dot{q}\rangle$ è l'energia cinetica e $U = U(q)$ il potenziale.

**Equazioni di Eulero-Lagrange:**

$$\frac{d}{dt}\frac{\partial L}{\partial \dot{q}_k} = \frac{\partial L}{\partial q_k}, \quad k = 1,\ldots,n$$

**Teorema.** Se $L = T - U$, le equazioni di EL coincidono con le equazioni di Newton $m_k\ddot{x}_k = -\nabla_{x_k} U$.

## Funzionale d'azione e principio di Hamilton

Dato lo spazio funzionale $H^{t_1,t_2}_{q_1,q_2} = \{\phi \in C^2([t_1,t_2]\to\mathbb{R}^N): \phi(t_i)=q_i\}$, il **funzionale d'azione** è:

$$S[\phi] = \int_{t_1}^{t_2} L(\phi,\dot{\phi},t)\,dt$$

**Principio di Hamilton.** $\phi(t)$ è soluzione delle equazioni di EL $\Leftrightarrow$ $\phi$ è un punto stazionario di $S$:

$$\frac{d}{d\sigma}S[\omega_\sigma]\bigg|_{\sigma=0} = 0 \quad \forall \text{ variazione } \omega_\sigma \text{ di } \phi$$

**Lemma fondamentale del calcolo delle variazioni.** Se $\int_{t_1}^{t_2} \beta(t)h(t)\,dt = 0$ per ogni $h \in C^2$ con $h(t_1)=h(t_2)=0$, allora $\beta \equiv 0$.

## Invarianza in forma

Le equazioni di EL sono **invarianti per cambio di coordinate**: se $q = \psi(Q)$, la Lagrangiana trasformata $\tilde{L}(Q,V) = L(\psi(Q), D\psi(Q)\cdot V)$ soddisfa le stesse equazioni in $(Q,V)$.

**Esempio (coordinate polari):**

$$L = \frac{1}{2}m(\dot{x}^2+\dot{y}^2) - U(\sqrt{x^2+y^2}) \;\longrightarrow\; \tilde{L} = \frac{1}{2}m(\dot{\rho}^2 + \rho^2\dot{\theta}^2) - U(\rho)$$

## Energia generalizzata (Hamiltoniana)

$$H = \left\langle \frac{\partial L}{\partial \dot{q}}, \dot{q}\right\rangle - L = \sum_k \frac{\partial L}{\partial \dot{q}_k}\dot{q}_k - L$$

**Teorema.** Se $L = L(q,\dot{q})$ (non dipende esplicitamente da $t$), allora $H$ è costante del moto. Per $L = T - U$: $H = T + U$ (energia totale).

## Coordinate cicliche e leggi di conservazione

Se $L$ non dipende da $q_k$ (coordinata ciclica), allora $p_k = \frac{\partial L}{\partial \dot{q}_k}$ è costante.

**Esempio Keplero:** $L = \frac{1}{2}m(\dot{\rho}^2+\rho^2\dot{\theta}^2) + k/\rho$. La coordinata $\theta$ è ciclica $\Rightarrow$ $J = m\rho^2\dot{\theta}$ (momento angolare) si conserva.

## Sistemi vincolati e Brachistocrona

Per $N$ punti in $\mathbb{R}^d$ con $l$ vincoli, si usano $n = dN-l$ coordinate generalizzate. Le equazioni di EL si applicano alla Lagrangiana scritta in coordinate locali.

**Brachistocrona.** Il problema di trovare la curva di discesa più rapida si riduce a minimizzare il funzionale:

$$T = \int_0^l \frac{\sqrt{1+f'^2}}{\sqrt{2gf(x)}}\,dx$$

La soluzione soddisfa $f(1+f'^2) = c$ (costante), che parametricamente descrive una **cicloide**.

## Connessioni

- Fondamentale per: [[Leggi di Keplero]], [[Oscillatore armonico]]
- Teoria alla base: [[Equazione differenziale ordinaria]], [[Stabilità di un punto di equilibrio]]
- Versione hamiltoniana e ottimizzazione: [[Condizioni KKT]] (analogo per ottimizzazione vincolata)
- Corsi: [[Modelli Matematici per la Fisica I]]

## Fonti

- [[Dispense MMFI — Galletti]] (§4, §6, pp. 26-43)
