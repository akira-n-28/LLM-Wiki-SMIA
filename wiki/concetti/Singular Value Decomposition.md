---
tipo: concetto
titolo: Singular Value Decomposition
tag: [algebra-lineare, ml, calcolo-numerico]
cluster: algebra
fonti: 2
ultima-modifica: 2026-05-05
---

# Singular Value Decomposition (SVD)

Per ogni matrice $A \in \mathbb{R}^{m \times n}$ esiste una fattorizzazione

$$
A = U \Sigma V^\top
$$

con:
- $U \in \mathbb{R}^{m \times m}$ ortogonale ($U^\top U = I_m$) — colonne = **vettori singolari sinistri**.
- $V \in \mathbb{R}^{n \times n}$ ortogonale — colonne = **vettori singolari destri**.
- $\Sigma \in \mathbb{R}^{m \times n}$ diagonale con $\sigma_1 \geq \sigma_2 \geq \cdots \geq \sigma_\ell \geq 0$, $\ell = \min\{m, n\}$ — **valori singolari**.

## Proprietà chiave

- $\sigma_i^2$ sono autovalori di $A^\top A$ (e di $A A^\top$).
- $V$ contiene gli autovettori di $A^\top A$; $U$ quelli di $A A^\top$.
- Espansione in prodotti esterni: $A = \sum_{i=1}^\ell \sigma_i u_i v_i^\top$.

## Rango e norme

- $\mathrm{rank}(A) = \#\{\sigma_i > 0\}$ — il numero di valori singolari non nulli.
- $\|A\|_2 = \sigma_1$ — il valore singolare massimo è la norma spettrale.
- Per $A$ quadrata invertibile: $\|A^{-1}\|_2 = 1/\sigma_n$, quindi $K_2(A) = \sigma_1/\sigma_n$ (cfr. [[Numero di condizionamento]]).
- $\|A\|_F = \sqrt{\sigma_1^2 + \ldots + \sigma_\ell^2}$ — [[Norma di Frobenius]] come somma dei quadrati dei valori singolari.

## SVD ridotta (economica)

Per $m \geq n$ (più righe che colonne), la SVD piena ha $U \in \mathbb{R}^{m \times m}$ con $m-n$ colonne inutilizzate. La **SVD ridotta** è:

$$A = \tilde{U}\tilde{\Sigma}\tilde{V}^T$$

con $\tilde{U} \in \mathbb{R}^{m \times n}$, $\tilde{\Sigma} \in \mathbb{R}^{n \times n}$ diagonale, $\tilde{V} \in \mathbb{R}^{n \times n}$ ortogonale. Risparmia memoria e calcolo.

## Calcolo numerico

**Via $A^T A$:** calcola gli autovalori e autovettori di $A^T A$ (SPD). Svantaggi: $K_2(A^TA) = K_2(A)^2$ — raddoppia la perdita di cifre significative.

**Algoritmo di Golub-Reinsch (standard):**
1. Bidiagonalizzazione: $U_1^T A V_1 = B$ con $B$ bidiagonale superiore (Householder), $O(mn^2)$.
2. Iterazione QR su $B^T B$ per trovare $\sigma_i$ senza formare $A^TA$.
Numericamente stabile: $K_2(B^TB) = K_2(A)^2$ ma si lavora con $B$, non $B^TB$.

## Interpretazione geometrica

L'azione di $A$ si decompone in:

$$
x \xrightarrow{V^\top} \text{rotazione} \xrightarrow{\Sigma} \text{scaling anisotropo} \xrightarrow{U} \text{rotazione}
$$

La sfera unitaria viene mappata in un **ellissoide** con semiassi $\sigma_i$.

## Approssimazione a basso rango (Eckart-Young)

Troncando dopo $k < \ell$ termini:

$$
A^{(k)} = \sum_{i=1}^k \sigma_i u_i v_i^\top
$$

è la **migliore** approssimazione di $A$ di rango $\leq k$ in [[Norma di Frobenius]] (e anche in norma spettrale). Da qui derivano: compressione di immagini/segnali, denoising (i $\sigma_i$ piccoli sono spesso rumore), risoluzione di sistemi mal condizionati.

## Pseudoinversa di Moore-Penrose

$$
A^\dagger = V \Sigma^\dagger U^\top, \qquad \Sigma^\dagger = \mathrm{diag}(\sigma_1^{-1}, \ldots, \sigma_r^{-1}, 0, \ldots, 0)
$$

dove $r$ è il rango. Risolve $\min \|Ax - b\|_2$ tramite $x^* = A^\dagger b$ — generalizza la formula chiusa di [[Regressione lineare]] anche a casi sotto/sovradeterminati.

## Connessione con la PCA

Se $X$ è la matrice dei dati centrata: $X = U \Sigma V^\top$ implica che la matrice di covarianza $S = \frac{1}{n} X^\top X = V (\Sigma^2 / n) V^\top$. Quindi $V$ contiene le componenti principali e $\sigma_i^2 / n$ sono le varianze. Vedi [[Principal Component Analysis]].

## Collegamenti

- Calcolo: [[Power iteration]], [[Quoziente di Rayleigh]], [[Fattorizzazione QR]], [[Algoritmo QR per autovalori]]
- Applicazione: [[Principal Component Analysis]]
- Norma: [[Norma di Frobenius]]
- Condizionamento: [[Numero di condizionamento]] — $K_2(A) = \sigma_1/\sigma_n$
- Discusso in: [[Machine Learning]] (§6.3), [[Metodi Numerici]] (cap. 7)

## Fonti

- [[Dispense Machine Learning — Galletti]] (§6.3, pp. 21-22)
- [[Dispense Metodi Numerici — Galletti]] (cap. 7.4-7.5 — norme, rango, calcolo numerico)
