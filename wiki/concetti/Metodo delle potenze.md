---
tipo: concetto
titolo: Metodo delle potenze
tag: [algebra-lineare, calcolo-numerico, metodi-numerici, autovalori]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Metodo delle Potenze

Il **metodo delle potenze** calcola l'autovalore di modulo massimo (autovalore dominante) e il corrispondente autovettore di $A \in \mathbb{R}^{n \times n}$.

## Ipotesi

Sia $|\lambda_1| > |\lambda_2| \geq \ldots \geq |\lambda_n|$ (autovalore dominante isolato). Scrivi $x_0 = \sum_i c_i v_i$ (decomposizione in autovettori), con $c_1 \neq 0$.

## Algoritmo

```
x₀ = vettore iniziale arbitrario (c₁ ≠ 0)
per k = 0, 1, 2, ...:
    y_{k+1} = A xₖ
    xₖ₊₁  = y_{k+1} / ‖y_{k+1}‖
    μₖ     = xₖᵀ A xₖ      ← quoziente di Rayleigh
```

**Convergenza:** $x_k \to v_1$ (autovettore dominante) e $\mu_k \to \lambda_1$.

Il tasso di convergenza è geometrico con fattore:

$$\rho = \left|\frac{\lambda_2}{\lambda_1}\right|^k$$

Se $|\lambda_2|$ è vicino a $|\lambda_1|$, la convergenza è lenta.

## Potenze Inverse

Per trovare l'**autovalore di modulo minimo** $\lambda_n$, si applica il metodo delle potenze a $A^{-1}$:

$$A x_{k+1} = x_k$$

(si risolve il sistema anziché moltiplicare per $A^{-1}$ esplicitamente). Converge a $1/\lambda_n$ come autovalore dominante di $A^{-1}$.

**Costo:** una fattorizzazione LU di $A$ + una sostituzione per iterazione.

## Potenze Inverse con Shift

Per trovare l'autovalore più vicino a un valore noto $\sigma$, si applica le potenze inverse a $(A - \sigma I)$:

$$(A - \sigma I)\, x_{k+1} = x_k$$

Converge all'autovalore $\lambda_j$ che minimizza $|\lambda_j - \sigma|$. Utile quando si ha una stima approssimata di un autovalore.

**Variante di Rayleigh:** aggiorna $\sigma_k = \mu_k$ (quoziente di Rayleigh corrente) a ogni passo → convergenza cubica vicino all'autovalore.

## Deflazione

Dopo aver trovato $(\lambda_1, v_1)$, si può deflazionare:

$$B = A - \lambda_1 v_1 v_1^T$$

$B$ ha gli stessi autovalori di $A$ tranne $\lambda_1 \to 0$. Si applica il metodo delle potenze a $B$ per trovare $\lambda_2$, ecc.

## Connessioni

- Prerequisito di: [[Algoritmo QR per autovalori]]
- Si collega a: [[Autovalori e autovettori]], [[Cerchi di Gershgorin]], [[Quoziente di Rayleigh]], [[Power iteration]]
- Discusso in: [[Metodi Numerici]], [[Machine Learning]] *(PCA usa il metodo delle potenze)*

## Fonti

- [[Dispense Metodi Numerici — Galletti]]
