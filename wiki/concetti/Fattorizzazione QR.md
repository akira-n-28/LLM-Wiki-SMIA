---
tipo: concetto
titolo: Fattorizzazione QR
tag: [algebra-lineare, calcolo-numerico, metodi-numerici]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Fattorizzazione QR

Ogni matrice $A \in \mathbb{R}^{m \times n}$ con $m \geq n$ ammette la decomposizione:

$$A = QR$$

dove $Q \in \mathbb{R}^{m \times m}$ è **ortogonale** ($Q^TQ = I$) e $R \in \mathbb{R}^{m \times n}$ è **triangolare superiore**.

## Costruzione via Householder

Le **riflessioni di Householder** azzerano sistematicamente le entrate sotto la diagonale di $A$ colonna per colonna.

La matrice di Householder associata al vettore $v$ è:

$$H = I - \frac{2\,vv^T}{\|v\|^2}$$

$H$ è ortogonale ($H^T = H^{-1} = H$) e simmetrica. Scegliendo $v = x - \|x\|e_1$, la trasformazione $Hx = \|x\|e_1$ azzera tutte le componenti di $x$ tranne la prima.

**Costo:** $O(n^2(m-n/3))$ moltiplicazioni — simile alla LU ma con migliori proprietà di stabilità.

## Fattorizzazione QR ridotta (economica)

Per $m > n$, la fattorizzazione piena è ridondante. La **QR ridotta** è:

$$A = \tilde{Q}\tilde{R}$$

con $\tilde{Q} \in \mathbb{R}^{m \times n}$ (colonne ortonormali, $\tilde{Q}^T\tilde{Q}=I_n$) e $\tilde{R} \in \mathbb{R}^{n \times n}$ triangolare superiore.

## Applicazione: minimi quadrati sovradeterminati

Dato $A \in \mathbb{R}^{m \times n}$ con $m > n$ (più equazioni che incognite), si cerca:

$$x^* = \arg\min_x \|Ax - b\|_2$$

**Via QR ridotta:** $\tilde{Q}^TAx = \tilde{Q}^Tb$ si riduce a $\tilde{R}x = \tilde{Q}^Tb$, sistema triangolare — backward substitution in $O(n^2)$.

**Confronto con equazione normale** $A^TAx = A^Tb$:
- L'equazione normale ha condizionamento $K(A^TA) = K(A)^2$ — raddoppia la perdita di cifre significative.
- La QR mantiene $K(\tilde{R}) = K(A)$ — numericamente molto più stabile.

## Algoritmo di Gram-Schmidt (classico e modificato)

Alternativa a Householder, costruisce $Q$ colonna per colonna ortogonalizzando le colonne di $A$. Il Gram-Schmidt modificato (MGS) è numericamente più stabile del classico (CGS).

**Costo:** $O(mn^2)$ — stesso ordine di Householder ma meno stabile per matrici mal condizionate.

## Legame con autovalori

La fattorizzazione QR è la base dell'[[Algoritmo QR per autovalori]]: iterando $A_{k+1} = R_kQ_k$ (dopo aver fattorizzato $A_k = Q_kR_k$), la matrice converge alla forma di Schur triangolare.

## Connessioni

- Si collega a: [[Sistemi lineari — metodi diretti]], [[Algoritmo QR per autovalori]], [[Numero di condizionamento]]
- Applicazione a: [[Singular Value Decomposition]] (via Golub-Reinsch)
- Discusso in: [[Metodi Numerici]]

## Fonti

- [[Dispense Metodi Numerici — Galletti]]
