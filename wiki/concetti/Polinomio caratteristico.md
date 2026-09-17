---
tipo: concetto
titolo: Polinomio caratteristico
tag: [algebra-lineare, matematica]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Polinomio caratteristico

Dato un endomorfismo $T: V \to V$ e $A$ una matrice che lo rappresenta in una base, il **polinomio caratteristico** di $T$ è:

$$p_T(\lambda) = \det(A - \lambda I_n)$$

Il polinomio $p_T$ non dipende dalla scelta della base (matrici simili hanno lo stesso polinomio caratteristico).

## Struttura

$p_T(\lambda)$ è un polinomio di grado $n$ in $\lambda$:
- Coefficiente di $\lambda^n$: $(-1)^n$.
- Coefficiente di $\lambda^{n-1}$: $(-1)^{n-1} \cdot \mathrm{Tr}(A)$.
- Termine noto ($\lambda^0$): $\det A$.

## Autovalori come radici

$$\lambda_0 \in \mathrm{Spec}(T) \;\Longleftrightarrow\; p_T(\lambda_0) = 0$$

**Dimostrazione:** $\lambda_0$ è autovalore $\Leftrightarrow$ esiste $v \neq 0$ con $T(v) = \lambda_0 v \Leftrightarrow (T - \lambda_0 \mathrm{Id})$ è singolare $\Leftrightarrow \det(A - \lambda_0 I) = 0$.

Gli autovalori di $A$ sono le soluzioni in $K$ di $p_T(\lambda) = 0$.

## Molteplicità algebrica e geometrica

Data una radice $\lambda_0$ di $p_T$:

- **Molteplicità algebrica** $m_a(\lambda_0)$: molteplicità di $\lambda_0$ come radice di $p_T$.
- **Molteplicità geometrica** $m_g(\lambda_0) = \dim V_{\lambda_0}$: dimensione dell'autospazio $V_{\lambda_0} = \ker(A - \lambda_0 I)$.

Vale sempre: $1 \leq m_g(\lambda_0) \leq m_a(\lambda_0)$.

## Calcolo

Per $A = \begin{pmatrix} 0&2\\-3&4 \end{pmatrix}$:

$$\det(A - \lambda I) = \det\begin{pmatrix} -\lambda & 2 \\ -3 & 4-\lambda \end{pmatrix} = \lambda^2 - 4\lambda + 6$$

Le radici reali (se esistono) sono gli autovalori. Se $p_T$ ha radici complesse, $T$ non è diagonalizzabile su $\mathbb{R}$.

## Connessioni

- Richiede: [[Autovalori e autovettori]]
- Porta a: [[Diagonalizzazione]]
- Discusso in: [[Algebra Lineare]]

## Fonti

- [[Dispense AlgLin — Galletti]]
