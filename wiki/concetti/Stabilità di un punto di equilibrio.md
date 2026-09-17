---
tipo: concetto
titolo: Stabilità di un punto di equilibrio
tag: [mmf, meccanica, equazioni-differenziali, stabilità]
cluster: fisica
fonti: 1
ultima-modifica: 2026-05-06
---

# Stabilità di un punto di equilibrio

Dato $\dot{x} = f(x)$ con $f(\bar{x}) = 0$, si classifica il punto di equilibrio $\bar{x}$:

| Tipo | Definizione |
|---|---|
| **Stabile** | $\forall\varepsilon>0\ \exists\delta>0: \|x(0)-\bar{x}\|<\delta \Rightarrow \|x(t)-\bar{x}\|<\varepsilon\ \forall t>0$ |
| **Asint. stabile** | Stabile + $x(t) \to \bar{x}$ per $t\to+\infty$ |
| **Instabile** | Non stabile |

Il **flusso** $\Phi_t(x)$ è la soluzione con $\Phi_0(x) = x$. La stabilità si esprime come: $x \in B_\delta(\bar{x}) \Rightarrow \Phi_t(x) \in B_\varepsilon(\bar{x})\ \forall t\geq 0$.

## Teorema di Lyapunov

**Teorema.** Sia $\bar{x}$ punto di equilibrio. Se esiste $W \in C^1$ su un aperto $\lambda \ni \bar{x}$ tale che:

1. $W(\bar{x}) = 0$
2. $W(x) > 0$ per $x \in \lambda\setminus\{\bar{x}\}$
3. $\frac{d}{dt}W(\Phi_t(x))\big|_{t=0} = \nabla W(\bar{x}) \cdot f(\bar{x}) \leq 0$

allora $\bar{x}$ è **stabile** (asintoticamente stabile se la condizione 3 è $< 0$).

**Corollario (Dirichlet-Lagrange).** Per $\dot{x}=v$, $m\dot{v}=-U'(x)$: se $U$ ha un minimo locale stretto in $\bar{x}$, allora $(\bar{x}, 0)$ è stabile. (La funzione di Lyapunov è $H = \frac{1}{2}mv^2 + U(x)$.)

## Teorema del linearizzato

Per $\dot{x} = f(x)$ con $f(\bar{x}) = 0$ e $f \in C^2$: si calcola la jacobiana

$$A = Df(\bar{x}), \quad A_{ij} = \frac{\partial f_i}{\partial x_j}\bigg|_{\bar{x}}$$

- Se tutti gli autovalori di $A$ hanno parte reale **negativa** $\Rightarrow \bar{x}$ è asintoticamente stabile.
- Se almeno un autovalore ha parte reale **positiva** $\Rightarrow \bar{x}$ è instabile.

## Insiemi di livello e moti periodici

**Insieme di livello:** $I_E = \{(x,v): H(x,v)=E\}$. È **critico** se contiene un punto di equilibrio.

Per sistemi 1D conservativi: i moti si svolgono sulle curve di livello di $H$. La formula del periodo è:

$$T = 2\int_{x_-(E)}^{x_+(E)} \frac{dx}{\sqrt{\frac{2}{m}(E-U(x))}}$$

## Poincaré-Bendixson (sistemi 2D)

**$\omega$-limite:** $\omega_l(x) = \{y \mid \exists t_k \nearrow +\infty: \Phi_{t_k}(x) \to y\}$.

**Teorema (Poincaré-Bendixson).** Se $D \subset \mathbb{R}^2$ è un insieme positivamente invariante e compatto senza punti di equilibrio, allora $\forall x \in D$, $\omega_l(x)$ è un'orbita periodica.

Applicazione: l'oscillatore di Van der Pol ha un ciclo limite stabile (vedi [[Oscillatore armonico]]).

## Connessioni

- Teoria ODE: [[Equazione differenziale ordinaria]]
- Applicazione meccanica: [[Oscillatore armonico]], [[Meccanica Lagrangiana]]
- Corsi: [[Modelli Matematici per la Fisica I]]

## Fonti

- [[Dispense MMFI — Galletti]] (§2.2-2.4, §3, pp. 9-25)
