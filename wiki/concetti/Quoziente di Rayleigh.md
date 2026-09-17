---
tipo: concetto
titolo: Quoziente di Rayleigh
tag: [algebra-lineare, ottimizzazione]
cluster: algebra
ultima-modifica: 2026-04-30
---

# Quoziente di Rayleigh

Per una matrice **simmetrica** $A \in \mathbb{R}^{n \times n}$ e un vettore $v \neq 0$, il quoziente di Rayleigh è:

$$
R(v) = \frac{v^\top A v}{v^\top v}
$$

## Teorema min-max

Se $\lambda_{\min}, \lambda_{\max}$ sono il minimo e il massimo autovalore di $A$:

$$
\lambda_{\min} \leq \frac{v^\top A v}{v^\top v} \leq \lambda_{\max}, \qquad \max_{\|v\| = 1} v^\top A v = \lambda_{\max}
$$

con il massimo raggiunto sull'autovettore associato a $\lambda_{\max}$. Più in generale (Courant-Fischer):

$$
\lambda_k = \min_{\dim(S) = n-k+1}\, \max_{v \in S, v \neq 0} R(v)
$$

## Perché serve in ML

- È la **chiave** della derivazione della [[Principal Component Analysis|PCA]]: massimizzare $w^\top C w$ con $\|w\| = 1$ equivale a trovare l'autovettore dominante di $C$.
- È il principio dietro [[Power iteration]] per stimare autovalori estremi.

## Collegamenti

- Strumento per: [[Principal Component Analysis]], [[Singular Value Decomposition]]
- Algoritmo correlato: [[Power iteration]]
- Discusso in: [[Machine Learning]]

## Fonti

- [[Dispense Machine Learning — Galletti]] (§6.2, p. 20)
