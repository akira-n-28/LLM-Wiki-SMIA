---
tipo: concetto
titolo: Leggi di Keplero
tag: [mmf, meccanica, fisica]
cluster: fisica
fonti: 1
ultima-modifica: 2026-05-06
---

# Leggi di Keplero

Le tre leggi descrivono il moto dei pianeti. Si derivano dalla meccanica lagrangiana con potenziale gravitazionale $U(r) = -Gm_1m_2/|r|$.

## Setup: massa ridotta

Per un sistema di due corpi:

$$m_R = \frac{m_1 m_2}{m_1+m_2}, \qquad m_R\ddot{r} = -\nabla U(r)$$

Il problema a due corpi si riduce al moto di una particella di massa $m_R$ in un potenziale centrale $U(\rho) = -k/\rho$ (con $k = Gm_1m_2$).

## Lagrangiana in coordinate polari

$$L = \frac{1}{2}m(\dot{\rho}^2 + \rho^2\dot{\theta}^2) + \frac{k}{\rho}$$

La coordinata $\theta$ è ciclica $\Rightarrow$ **momento angolare conservato**:

$$J = m\rho^2\dot{\theta} = \text{costante}$$

**Potenziale efficace:**

$$U_\text{eff}(\rho) = -\frac{k}{\rho} + \frac{J^2}{2m\rho^2}$$

## Seconda legge di Keplero — velocità areolare

L'area spazzata dal raggio vettore per unità di tempo è costante:

$$\frac{dA}{dt} = \frac{1}{2}\rho^2\dot{\theta} = \frac{J}{2m} = \text{costante}$$

**Equivalente alla conservazione del momento angolare.**

## Prima legge di Keplero — orbita ellittica

Via la **formula di Binet** ($\ddot{\rho} = -\frac{J^2}{m^2}u^2 u''$ con $u = 1/\rho$), l'equazione dell'orbita diventa $u'' = -u + mk/J^2$, con soluzione:

$$\frac{1}{\rho} = \frac{1}{p} + \frac{e}{p}\cos\theta, \qquad \rho = \frac{p}{1+e\cos\theta}$$

dove $p = J^2/(mk)$ è il **semilato retto** ed $e$ è l'**eccentricità**.

| $e$ | Tipo di orbita |
|---|---|
| $0 \leq e < 1$ | Ellisse ($e=0$: cerchio) |
| $e = 1$ | Parabola |
| $e > 1$ | Iperbole |

Semiassi: $a = p/(1-e^2)$, $b = p/\sqrt{1-e^2}$.

L'energia è $E = mc^2(e^2-1)/(2p^2)$: orbita ellittica $\Leftrightarrow$ $E < 0$.

## Terza legge di Keplero — $T^2 \propto a^3$

$$T^2 = \frac{\text{Area ellisse}^2}{(J/2m)^2} = \frac{\pi^2 a^2 b^2}{(J/2m)^2} \qquad \Rightarrow \qquad \frac{T^2}{a^3} = \frac{4\pi^2}{GM}$$

Il rapporto $T^2/a^3$ è uguale per tutti i pianeti intorno alla stessa stella.

## Connessioni

- Strumento: [[Meccanica Lagrangiana]] (equazioni EL, coordinate cicliche)
- Forza centrale e potenziale: [[Equazione differenziale ordinaria]]
- Corsi: [[Modelli Matematici per la Fisica I]]

## Fonti

- [[Dispense MMFI — Galletti]] (§5, pp. 34-36)
