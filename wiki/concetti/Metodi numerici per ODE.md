---
tipo: concetto
titolo: Metodi numerici per ODE
tag: [calcolo-numerico, equazioni-differenziali, metodi-numerici]
cluster: numerico
fonti: 1
ultima-modifica: 2026-05-05
---

# Metodi numerici per ODE

Si considera il **problema di Cauchy** (IVP — Initial Value Problem):

$$y' = f(t, y), \quad y(t_0) = y_0, \quad t \in [t_0, T]$$

I metodi numerici approssimano la soluzione $y(t)$ su una griglia $t_0 < t_1 < \ldots < t_N = T$ con passo $h = (T-t_0)/N$.

## Eulero Esplicito (Forward Euler)

$$y_{k+1} = y_k + h\,f(t_k, y_k)$$

**Derivazione:** approssimazione a differenze finite in avanti di $y'$.

**Errore locale di troncamento:** $\tau_k = O(h^2)$ → **ordine globale 1** ($\|y_N - y(T)\| = O(h)$).

**Stabilità assoluta:** per l'equazione test $y'=\lambda y$ (con $\text{Re}(\lambda)<0$), il metodo è stabile se $h\lambda$ cade nella **regione di stabilità**:

$$|1 + h\lambda| < 1$$

che per $\lambda$ reale negativo richiede $h < 2/|\lambda|$. Sistemi stiff con $|\lambda| \gg 1$ richiedono passi $h$ molto piccoli → Eulero esplicito è inadatto per sistemi stiff.

## Eulero Implicito (Backward Euler)

$$y_{k+1} = y_k + h\,f(t_{k+1}, y_{k+1})$$

A ogni passo si risolve un'equazione non lineare in $y_{k+1}$ (con Newton o iterazioni di punto fisso).

**Ordine globale 1** (come esplicito).

**Stabilità assoluta:** la regione di stabilità è $\mathbb{C} \setminus \{|1-h\lambda|<1\}$, che contiene tutto il semipiano sinistro $\text{Re}(h\lambda)<0$. Il metodo è **A-stabile**: qualsiasi $h>0$ garantisce stabilità per $\lambda$ con parte reale negativa → adatto a sistemi stiff.

**Svantaggio:** ogni passo richiede la risoluzione di un sistema non lineare.

## Ordine di convergenza

| Metodo             | Ordine locale | Ordine globale |
|--------------------|---------------|----------------|
| Eulero esplicito   | 2 ($O(h^2)$)  | 1              |
| Eulero implicito   | 2             | 1              |
| Runge-Kutta 4      | 5 ($O(h^5)$)  | 4              |

L'errore **locale** (troncamento in un passo) ha un ordine più alto dell'errore **globale** (cumulato su tutti i passi).

## Runge-Kutta di ordine 4 (RK4)

$$k_1 = f(t_k,\, y_k)$$
$$k_2 = f\!\left(t_k+\tfrac{h}{2},\, y_k+\tfrac{h}{2}k_1\right)$$
$$k_3 = f\!\left(t_k+\tfrac{h}{2},\, y_k+\tfrac{h}{2}k_2\right)$$
$$k_4 = f(t_k+h,\, y_k+hk_3)$$
$$y_{k+1} = y_k + \frac{h}{6}(k_1 + 2k_2 + 2k_3 + k_4)$$

**Errore locale:** $O(h^5)$ → **ordine globale 4**. Usa 4 valutazioni di $f$ per passo.

La struttura è descritta da un **tableau di Butcher** $(A, b, c)$ che generalizza tutti i metodi Runge-Kutta.

## Stabilità assoluta e sistemi stiff

Un sistema è **stiff** se ha autovalori con $|\text{Re}(\lambda_{\max})| \gg |\text{Re}(\lambda_{\min})|$: la soluzione "lenta" è fisicamente interessante, ma i termini veloci impongono $h$ molto piccolo per i metodi espliciti.

**Regione di stabilità assoluta:** il metodo è stabile per $y'=\lambda y$ se $y_{k+1}/y_k = R(h\lambda)$ con $|R(h\lambda)| \leq 1$.

- Eulero esplicito: disco di centro $-1$ e raggio $1$.
- Eulero implicito: complemento di disco di centro $+1$ e raggio $1$ — include il semipiano sinistro.
- RK4: regione più ampia di Eulero esplicito, ma non A-stabile.

**Per sistemi stiff:** Eulero implicito, Crank-Nicolson (ordine 2, A-stabile), BDF (Backward Differentiation Formulas, ordine fino a 6).

## Connessioni

- Richiede: [[Metodi per equazioni non lineari]] (Eulero implicito), [[Teorema delle Contrazioni]] (convergenza punto fisso)
- Analogia con: [[Integrazione numerica]] (quadratura = passo ODE su griglia)
- Discusso in: [[Metodi Numerici]]

## Fonti

- [[Dispense Metodi Numerici — Galletti]]
