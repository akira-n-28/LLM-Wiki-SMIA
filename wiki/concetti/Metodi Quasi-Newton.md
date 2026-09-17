---
tipo: concetto
titolo: Metodi Quasi-Newton
tag: [ottimizzazione, algoritmi, larga-scala]
cluster: ottimizzazione
fonti: 1
ultima-modifica: 2026-05-04
---

# Metodi Quasi-Newton

Metodi che approssimano la Hessiana $\nabla^2 f(x_k)$ con una matrice $B_k$ aggiornata iterativamente, evitando il costo $O(n^3)$ del [[Metodo di Newton (ottimizzazione)|Metodo di Newton]].

## Idea

Il metodo di Newton usa $x_{k+1} = x_k - [\nabla^2 f(x_k)]^{-1} \nabla f(x_k)$. Nei metodi quasi-Newton si sostituisce la Hessiana con un'approssimazione $B_k$:
$$
x_{k+1} = x_k - \alpha_k B_k^{-1} \nabla f(x_k)
$$

## Equazione secante (condizione quasi-Newton)

Nel caso quadratico: $\nabla f(y) - \nabla f(x) = Q(y-x) = \nabla^2 f(x)(y-x)$.

Nel caso generale si chiede che $B_{k+1}$ soddisfi:
$$
B_{k+1}(x_{k+1} - x_k) = \nabla f(x_{k+1}) - \nabla f(x_k)
$$

Definendo $s_k = x_{k+1} - x_k$ e $y_k = \nabla f(x_{k+1}) - \nabla f(x_k)$: $B_{k+1} s_k = y_k$.

L'aggiornamento è della forma $B_{k+1} = B_k + \Delta B_k$.

## Formule di aggiornamento

**Formule dirette** (aggiornano $B_k \approx \nabla^2 f$).

**Formule inverse** (aggiornano $H_k = B_k^{-1} \approx [\nabla^2 f]^{-1}$): $H_{k+1} s_k = y_k$ no, $H_{k+1} y_k = s_k$.

**BFGS** (Broyden-Fletcher-Goldfarb-Shanno): formula di aggiornamento con le migliori proprietà di convergenza. Richiede di memorizzare una matrice $n \times n$ → **inapplicabile a larga scala**.

## L-BFGS (Limited-memory BFGS)

Metodo per problemi a **larga scala** ($n \geq 10^4$): invece di memorizzare $H_k$ ($n \times n$), si memorizzano solo gli ultimi $m$ aggiornamenti $(s_{k-1}, y_{k-1}), \ldots, (s_{k-m}, y_{k-m})$.

$$
H_k \nabla f(x_k) = F\bigl(H_{n-m},\; (s_{k-1}, y_{k-1}), \ldots, (s_{k-m}, y_{k-m}),\; \nabla f(x_k)\bigr)
$$

dove $H_{n-m}$ è inizializzata con una matrice sparsa (tipicamente l'identità scalata). La procedura $F$ è un algoritmo ricorsivo a due loop — costo $O(nm)$ per iterazione.

**Caratteristiche L-BFGS**:
- Non memorizza matrici $n \times n$: memoria $O(nm)$ con $m \ll n$ (tipicamente $m = 5\text{--}20$)
- Convergenza superlineare in pratica
- **Miglior metodo quasi-Newton per larga scala**
- Usato di default in molti framework ML (PyTorch optim, scipy)

## Confronto con altri metodi

| Metodo | Memoria | Costo/iter | Convergenza |
|---|---|---|---|
| Gradiente ($\nabla f$) | $O(n)$ | $O(n)$ | lineare |
| CG non lineare | $O(n)$ | $O(n)$ | superlineare |
| BFGS | $O(n^2)$ | $O(n^2)$ | superlineare |
| L-BFGS | $O(nm)$ | $O(nm)$ | superlineare pratica |
| Newton | $O(n^2)$ | $O(n^3)$ | quadratica locale |
| Newton troncato | $O(n)$ | $O(n \cdot \text{iter CG})$ | quadratica locale |

## Collegamento con i corsi

- [[Ottimizzazione]]: §6.1.
- [[Machine Learning]]: L-BFGS è un'alternativa a [[Stochastic Gradient Descent]] per training su dataset piccoli/medi (batch completo).
- [[Fondamenti di Intelligenza Artificiale]]: ottimizzazione dei parametri di modelli non lineari.

## Fonti

- [[Dispense Ottimizzazione — Galletti]] (§6.1, pp. 43-44)
