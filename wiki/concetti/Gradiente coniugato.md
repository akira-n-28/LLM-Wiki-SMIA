---
tipo: concetto
titolo: Gradiente coniugato
tag: [ottimizzazione, algoritmi, algebra-lineare]
cluster: ottimizzazione
fonti: 2
ultima-modifica: 2026-05-05
---

# Gradiente coniugato

Metodo iterativo per minimizzare $f(x) = \frac12 x^T Q x - c^T x$ (caso quadratico, $Q \succ 0$) che converge in al più $n$ iterazioni. Estendibile al caso non quadratico (gradiente coniugato non lineare).

## Direzioni mutuamente coniugate

$d_i, d_j \in \mathbb{R}^n$ sono **mutuamente coniugate rispetto a $Q$** se:
$$
d_i^T Q d_j = 0, \quad d_i, d_j \neq 0
$$

**Proposizione**: $n$ direzioni mutuamente coniugate sono linearmente indipendenti (la dimostrazione usa $d_k^T Q (\sum \alpha_i d_i) = \alpha_k d_k^T Q d_k = 0 \Rightarrow \alpha_k = 0$ perché $Q \succ 0$).

## Metodo delle direzioni coniugate

Dato $x^* = \arg\min f$, esistono $\alpha_i$ tali che $x^* = \sum_{i=0}^{n-1} \alpha_i d_i$. Moltiplicando per $d_k^T Q$:
$$
\alpha_k = \frac{d_k^T c}{d_k^T Q d_k} = -\frac{\nabla f(x_k)^T d_k}{d_k^T Q d_k} = \arg\min_\alpha f(x_k + \alpha d_k)
$$

L'algoritmo: $x_{k+1} = x_k + \alpha_k d_k$, con $\alpha_k$ come sopra. Converge in esattamente $n$ passi.

## Metodo del gradiente coniugato (caso quadratico)

Genera le direzioni coniugate iterativamente senza precalcolarle:

$$
d_{k+1} = -\nabla f(x_{k+1}) + \beta_{k+1} d_k
$$

Scelta di $\beta_{k+1}$ per garantire $d_{k+1}^T Q d_k = 0$:
$$
\beta_{k+1} = \frac{\nabla f(x_{k+1})^T Q d_k}{d_k^T Q d_k} = \frac{\|\nabla f(x_{k+1})\|^2}{\|\nabla f(x_k)\|^2}
$$

L'ultima forma (formula **Fletcher-Reeves**) si ricava usando $\nabla f(x_{k+1})^T \nabla f(x_k) = 0$ e $Q d_k = [\nabla f(x_{k+1}) - \nabla f(x_k)]/\alpha_k$.

### Algoritmo completo

```
d₀ = -∇f(x₀)
for k = 0, 1, ..., n-1:
    αk = ‖∇f(xk)‖² / (dk^T Q dk)
    xk+1 = xk + αk dk
    ∇f(xk+1) = ∇f(xk) + αk Q dk       # aggiornamento efficiente
    βk+1 = ‖∇f(xk+1)‖² / ‖∇f(xk)‖²
    dk+1 = -∇f(xk+1) + βk+1 dk
```

**Proprietà chiave** (si dimostrano):
- $\nabla f(x_{k+1})^T d_k = 0$
- $\nabla f(x_{k+1})^T \nabla f(x_k) = 0$ (residui ortogonali)
- Converge in $\leq n$ iterazioni; se $Q$ ha $p \leq n$ autovalori distinti, converge in $\leq p$ iterazioni

## Convergenza nel caso non quadratico

Per $f$ non quadratica: stessa struttura iterativa ma $\beta_{k+1}$ calcolato senza $Q$.

**Fletcher-Reeves** (FR): $\beta_{k+1} = \|\nabla f(x_{k+1})\|^2 / \|\nabla f(x_k)\|^2$

**Polak-Ribière** (PR): $\beta_{k+1} = \nabla f(x_{k+1})^T [\nabla f(x_{k+1}) - \nabla f(x_k)] / \|\nabla f(x_k)\|^2$

Direzione: $d_{k+1} = -\nabla f(x_{k+1}) + \beta_{k+1} d_k$. Step size con ricerca di linea inesatta (Armijo o Wolfe). Convergenza globale dimostrata con opportune condizioni.

## Applicazione all'addestramento di reti neurali

Il gradiente coniugato si applica a $E(w) = \sum_p E_p(w)$ non quadratico con ricerca di linea inesatta. Per la variante lineare (ELM con $w$ fissi), $E(v) = \frac12 \|Av - b\|^2 = \frac12 v^T (A^T A) v - b^T A v$: problema quadratico con $Q = A^T A$ semidefinita positiva, risolvibile con CG.

## GC per sistemi lineari SPD

Risolvere $Ax = b$ con $A$ SPD equivale a minimizzare $f(x) = \frac{1}{2}x^TAx - b^Tx$, il cui gradiente è $\nabla f(x) = Ax - b = -r$ (residuo cambiato di segno).

**Algoritmo (formulazione residui):**

```
r₀ = b - Ax₀,  d₀ = r₀
for k = 0, 1, ...:
    αk = rₖᵀrₖ / (dₖᵀAdₖ)       ← passo ottimale lungo dₖ
    xₖ₊₁ = xₖ + αₖdₖ
    rₖ₊₁ = rₖ - αₖAdₖ            ← aggiornamento residuo
    βₖ₊₁ = rₖ₊₁ᵀrₖ₊₁ / rₖᵀrₖ   ← (Fletcher-Reeves)
    dₖ₊₁ = rₖ₊₁ + βₖ₊₁dₖ
    if ‖rₖ₊₁‖ < tol: break
```

**Convergenza in $\leq n+1$ iterazioni** in aritmetica esatta. In pratica, se $A$ ha $p \leq n$ autovalori distinti, converge in $\leq p$ iterazioni.

### Tasso di convergenza

$$\|e_k\|_A \leq 2\left(\frac{\sqrt{K}-1}{\sqrt{K}+1}\right)^k \|e_0\|_A, \qquad K = K_2(A) = \frac{\lambda_{\max}}{\lambda_{\min}}$$

Confronto con Richardson ottimale ($\rho_R = (K-1)/(K+1)$):

| Metodo | $\rho$ | Per $K=100$ |
|---|---|---|
| Richardson | $(K-1)/(K+1)$ | $\approx 0.980$ |
| GC | $(\sqrt{K}-1)/(\sqrt{K}+1)$ | $\approx 0.818$ |

Per $K \gg 1$: $\rho_R \approx 1-2/K$, $\rho_{GC} \approx 1-2/\sqrt{K}$ — GC riduce l'errore molto più rapidamente. Richiede $O(\sqrt{K})$ iterazioni contro $O(K)$ di Richardson.

### GC precondizionato (PCG)

Si sostituisce $A \to M^{-1}A$ con $M \approx A$ e $K(M^{-1}A) \ll K(A)$. Scelte comuni di $M$: diagonale (Jacobi), ILU, SSOR. Il PCG converge in $O(\sqrt{K(M^{-1}A)})$ iterazioni.

## Confronto con altri metodi

| Metodo | Info usate | Complessità/iter | Convergenza |
|---|---|---|---|
| Steepest descent | $f, \nabla f$ | $O(n)$ | lenta (lineare) |
| Gradiente coniugato | $f, \nabla f$ | $O(n)$ | $\leq n$ iter (quadratico) |
| Newton | $f, \nabla f, \nabla^2 f$ | $O(n^3)$ | locale, quadratica |
| L-BFGS | $f, \nabla f$ | $O(nm)$ | superlineare |
| Richardson (lin.) | $r_k$ | $O(n^2)$ | $O(K)$ iter |
| GC (lin., SPD) | $r_k, d_k$ | $O(n^2)$ | $O(\sqrt{K})$ iter |

## Collegamento con i corsi

- [[Ottimizzazione]]: §4.2, metodo principale per addestramento reti neurali.
- [[Metodi Numerici]]: GC per sistemi lineari sparsi SPD, confronto con [[Metodi iterativi per sistemi lineari]].
- [[Algebra Lineare]]: sistema $Ax = b$ risolto senza invertire $A$.

## Fonti

- [[Dispense Ottimizzazione — Galletti]] (§4.2, pp. 31-36)
- [[Dispense Metodi Numerici — Galletti]] (cap. 4 — GC lineare, tasso √K, PCG)
