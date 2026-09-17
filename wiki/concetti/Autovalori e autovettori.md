---
tipo: concetto
titolo: Autovalori e autovettori
tag: [algebra-lineare, matematica, ml, metodi-numerici]
cluster: algebra
fonti: 3
ultima-modifica: 2026-05-05
---

# Autovalori e autovettori

Un vettore non nullo $x \in \mathbb{C}^d$ è **autovettore** di una matrice quadrata $A \in \mathbb{C}^{d \times d}$ se esiste $\lambda \in \mathbb{C}$ tale che:

$$
Ax = \lambda x
$$

Il numero $\lambda$ è il corrispondente **autovalore**.

## Proprietà di base

- La norma dell'autovettore è irrilevante: se $x$ è soluzione, lo è $cx$ per qualunque $c \neq 0$.
- Stessa norma: $x$ e $-x$ condividono lo stesso autovalore.
- **Esempio funzionale**: $\frac{d}{dx} e^{ax} = a e^{ax}$ — l'esponenziale è autovettore dell'operatore derivata con autovalore $a$.

## Trasformazioni di similarità

Per qualunque matrice invertibile $T$:

$$
B = T^{-1} A T \;\Longrightarrow\; A \text{ e } B \text{ condividono gli autovalori}
$$

## Casi notevoli

- **Matrici ortogonali** ($Q^\top Q = I$): autovalori di modulo 1, quindi $\lambda = \pm 1$.
- **Matrici diagonali/triangolari**: autovalori = elementi sulla diagonale.
- **Matrici commutanti** ($AB = BA$): $A$ e $B$ ammettono la stessa base di autovettori.

## Autospazio e molteplicità

L'**autospazio** relativo a $\lambda_0$ è:

$$V_{\lambda_0} = \ker(A - \lambda_0 I) = \{x \in K^n : Ax = \lambda_0 x\}$$

Si calcola risolvendo $(A - \lambda_0 I)X = 0$ con [[Algoritmo di Gauss-Jordan]].

Gli autovalori sono le radici del **[[Polinomio caratteristico]]** $p_A(\lambda) = \det(A - \lambda I)$, polinomio di grado $n$.

Due molteplicità per ogni autovalore $\lambda_0$:
- **Algebrica** $m_a(\lambda_0)$: molteplicità come radice di $p_A$.
- **Geometrica** $m_g(\lambda_0) = \dim V_{\lambda_0}$: dimensione dell'autospazio.

Vale sempre $1 \leq m_g(\lambda_0) \leq m_a(\lambda_0)$.

$A$ è **[[Diagonalizzazione|diagonalizzabile]]** su $K$ $\Leftrightarrow$ $p_A$ ha tutte le radici in $K$ e $m_g(\lambda_0) = m_a(\lambda_0)$ per ogni autovalore.

## Matrici simmetriche

Se $A = A^\top$:
1. Tutti gli autovalori sono **reali**.
2. Autovettori associati ad autovalori distinti sono **ortogonali**.
3. **Decomposizione spettrale**: $A = X \Lambda X^\top$, con $X$ ortogonale e $\Lambda$ diagonale.

## Quoziente di Rayleigh e teorema min-max

Per una matrice simmetrica:

$$
\lambda_{\min} \leq \frac{v^\top A v}{v^\top v} \leq \lambda_{\max}, \qquad \max_{\|v\|=1} v^\top A v = \lambda_{\max}
$$

Vedi [[Quoziente di Rayleigh]].

## Localizzazione: Cerchi di Gershgorin

I [[Cerchi di Gershgorin]] localizzano lo spettro senza calcolare gli autovalori: $\mathrm{spec}(A) \subseteq \bigcup_i C_i$, con $C_i = \{|z - a_{ii}| \leq R_i\}$ e $R_i = \sum_{j\neq i}|a_{ij}|$. Se un sottoinsieme di $k$ cerchi è separato dagli altri $n-k$, contiene esattamente $k$ autovalori.

## Calcolo numerico

- **[[Metodo delle potenze]]**: moltiplica iterativamente $x_{k+1} = Ax_k / \|Ax_k\|$ → converge all'autovalore dominante $\lambda_1$. Il quoziente di Rayleigh $\mu_k = x_k^T A x_k$ approssima $\lambda_1$. Tasso: $|\lambda_2/\lambda_1|^k$.
- **Potenza inversa**: applica le potenze a $A^{-1}$ (risolve $Ax_{k+1}=x_k$) → converge a $\lambda_{\min}$.
- **Potenza inversa con shift**: applica le potenze a $(A-\sigma I)^{-1}$ → autovalore più vicino a $\sigma$.
- **[[Algoritmo QR per autovalori]]**: itera $A_k=Q_kR_k$, $A_{k+1}=R_kQ_k$ → converge alla **fattorizzazione di Schur** $A = QTQ^T$ con $T$ triangolare (autovalori sulla diagonale). Pre-processing: riduzione alla forma di Hessenberg in $O(n^3)$, poi ogni passo QR costa $O(n^2)$.
- **[[Singular Value Decomposition]]**: $\sigma_i(A) = \sqrt{\lambda_i(A^T A)}$ — i valori singolari sono radici degli autovalori di $A^TA$.

## Rilevanza per il ML

- **PCA**: le componenti principali sono gli autovettori della matrice di covarianza (vedi [[Principal Component Analysis]]).
- **SVD**: i valori singolari sono radici degli autovalori di $A^\top A$ (vedi [[Singular Value Decomposition]]).
- **Quoziente di Rayleigh**: formulazione varianza-massima della PCA.

## Perché sono utili

Se gli autovettori formano una base, qualunque vettore $y = \sum_i \alpha_i x_i$; moltiplicare per $A$ scala ogni direzione: $Ay = \sum_i \alpha_i \lambda_i x_i$. Questo fornisce una rappresentazione "diagonale" di operatori lineari complessi.

## Connessioni

- Struttura sottostante: [[Mappe lineari]], [[Spazio vettoriale]]
- Polinomio: [[Polinomio caratteristico]]
- Forma canonica: [[Diagonalizzazione]]
- Applicazione principale: [[Principal Component Analysis]], [[Singular Value Decomposition]]
- Calcolo: [[Quoziente di Rayleigh]], [[Metodo delle potenze]], [[Algoritmo QR per autovalori]]
- Localizzazione: [[Cerchi di Gershgorin]]
- Discusso in: [[Algebra Lineare]], [[Machine Learning]] (§6.2), [[Metodi Numerici]] (cap. 7)

## Fonti

- [[Dispense Machine Learning — Galletti]] (§6.2, p. 20)
- [[Dispense Metodi Numerici — Galletti]] (cap. 7 — algoritmi numerici, Gershgorin, Schur)
- [[Dispense AlgLin — Galletti]] (autospazi, molteplicità, diagonalizzabilità)
