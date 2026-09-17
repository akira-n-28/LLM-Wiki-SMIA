---
tipo: concetto
titolo: Metodo di Armijo
tag: [ottimizzazione, line-search, algoritmi]
cluster: ottimizzazione
fonti: 1
ultima-modifica: 2026-05-04
---

# Metodo di Armijo

Tecnica di **line search inesatta** per determinare lo step size $\alpha_k$ in metodi del tipo $x_{k+1} = x_k + \alpha_k d_k$. Garantisce un **sufficiente decremento** della funzione obiettivo — condizione necessaria per la convergenza globale.

## Il problema della line search

Dato $x_k$ e una direzione di discesa $d_k$ (con $\nabla f(x_k)^T d_k < 0$), si definisce la funzione:
$$
\Phi(\alpha) = f(x_k + \alpha d_k), \quad \Phi(0) = f(x_k), \quad \dot\Phi(0) = \nabla f(x_k)^T d_k < 0
$$

Il semplice decremento $f(x_{k+1}) < f(x_k)$ non garantisce convergenza (si può fare passi sempre più piccoli senza muoversi). Serve un **decremento sufficiente**.

## Condizione di Armijo

$$
f(x_k + \alpha_k d_k) \leq f(x_k) + \gamma \alpha_k \nabla f(x_k)^T d_k, \qquad \gamma \in (0,1)
$$

Geometricamente: $\Phi(\alpha_k)$ deve stare sotto la retta $Z(\alpha) = f(x_k) + \gamma \alpha \nabla f(x_k)^T d_k$ (pendenza negativa ridotta di un fattore $\gamma$).

## Algoritmo (backtracking)

Dati $\gamma \in (0,1)$, $\theta \in (0,1)$ (fattore di contrazione), $\Delta_k > 0$ (passo iniziale):

1. $\alpha \leftarrow \Delta_k$
2. **while** $f(x_k + \alpha d_k) > f(x_k) + \gamma \alpha \nabla f(x_k)^T d_k$ **do**
3. $\quad\alpha \leftarrow \theta \alpha$
4. **return** $\alpha_k = \alpha$

**Proposizione (terminazione finita)**: il ciclo termina in un numero finito di iterazioni.

*Dimostrazione*: se non terminasse, per $j \to \infty$ si avrebbe $\theta^j \Delta_k \to 0$ e passando al limite si ottiene $\nabla f(x_k)^T d_k \geq \gamma \nabla f(x_k)^T d_k$, cioè $(1-\gamma)\nabla f(x_k)^T d_k \geq 0$, assurdo perché $d_k$ è di discesa.

## Convergenza globale con Armijo

Con passo iniziale $\Delta_k = \frac{1}{\|d_k\|} \sigma\!\left(\frac{|\nabla f(x_k)^T d_k|}{\|d_k\|}\right)$ (sufficientemente grande), il metodo di Armijo garantisce:
1. $f(x_{k+1}) < f(x_k)$
2. Condizione d'angolo: $\frac{|\nabla f(x_k)^T d_k|}{\|d_k\|} \geq \sigma(\|\nabla f(x_k)\|)$
3. $\lim_{k\to\infty} \frac{\nabla f(x_k)^T d_k}{\|d_k\|} = 0$

Queste tre condizioni implicano che ogni punto limite di $\{x_k\}$ è un punto stazionario di $f$.

## Line search esatta vs inesatta

| | Esatta | Armijo (inesatta) |
|---|---|---|
| Formula | $\alpha_k = \arg\min_{\alpha \geq 0} f(x_k + \alpha d_k)$ | backtracking con $\gamma, \theta$ |
| Applicabilità | solo $f$ quadratica s.c. | qualsiasi $f \in C^1$ |
| Caso quadratico | $\alpha_k = -\nabla f(x_k)^T d_k / (d_k^T Q d_k)$ | — |
| Convergenza | ottimale per ogni passo | globale in generale |

## Condizioni di Wolfe (alternativa)

Estendono Armijo aggiungendo una **condizione di curvatura**: $\nabla f(x_k + \alpha_k d_k)^T d_k \geq c_2 \nabla f(x_k)^T d_k$ con $c_2 > \gamma$. Necessarie per garantire convergenza di metodi quasi-Newton (BFGS).

## Collegamento con i corsi

- [[Ottimizzazione]]: §3.4, usato in [[Discesa del gradiente]], [[Gradiente coniugato]], [[Metodo di Newton (ottimizzazione)]].
- Il parametro $\gamma$ tipicamente vale $10^{-4}$, $\theta = 0.5$.

## Fonti

- [[Dispense Ottimizzazione — Galletti]] (§3.4, §3.2, pp. 25-30)
