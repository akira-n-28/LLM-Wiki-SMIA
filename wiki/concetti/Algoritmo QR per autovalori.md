---
tipo: concetto
titolo: Algoritmo QR per autovalori
tag: [algebra-lineare, calcolo-numerico, metodi-numerici, autovalori]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Algoritmo QR per autovalori

L'**algoritmo QR** calcola tutti gli autovalori di $A$ iterando fattorizzazioni QR. È il metodo standard per il calcolo numerico degli autovalori in software come LAPACK.

## Iterazione base

Poni $A_0 = A$. A ogni passo:

1. Fattorizza $A_k = Q_k R_k$ (QR)
2. Aggiorna $A_{k+1} = R_k Q_k$ (prodotto invertito)

Le matrici $A_k$ sono tutte **simili** ad $A$ (stesso spettro) poiché $A_{k+1} = Q_k^T A_k Q_k$.

**Convergenza (matrici simmetriche):** $A_k \to \Lambda = \mathrm{diag}(\lambda_1, \ldots, \lambda_n)$; gli autovalori compaiono sulla diagonale in ordine decrescente di modulo.

**Convergenza (matrici generali):** $A_k$ tende alla **forma di Schur quasi-triangolare** (a blocchi $1\times 1$ o $2\times 2$ per coppie complesse coniugate).

## Fattorizzazione di Schur

Ogni matrice $A \in \mathbb{R}^{n\times n}$ ammette la decomposizione:

$$A = Q T Q^T$$

dove $Q$ ortogonale e $T$ è **quasi-triangolare superiore** (blocchi $1\times1$ e $2\times 2$). Gli autovalori sono i valori propri dei blocchi diagonali di $T$.

Per $A$ simmetrica: $T = \Lambda$ (diagonale reale).

## Pre-processing: forma di Hessenberg

Costo grezzo dell'algoritmo QR: $O(n^3)$ per iterazione × molte iterazioni = costoso.

**Soluzione:** si riduce prima $A$ alla forma di **Hessenberg superiore** ($H_{ij}=0$ per $i > j+1$) con $O(n^3)$ moltiplicazioni tramite trasformazioni di Householder simili. Poi ogni passo QR sulla forma di Hessenberg costa $O(n^2)$.

Per matrici simmetriche: la forma di Hessenberg è tridiagonale → ogni passo QR costa $O(n)$.

## Shift di Wilkinson

Per accelerare la convergenza, si sostituisce:

$$A_k - \sigma_k I = Q_k R_k, \qquad A_{k+1} = R_k Q_k + \sigma_k I$$

con $\sigma_k$ scelto come un autovalore della sottomatrice $2\times 2$ in basso a destra di $A_k$. Lo **shift di Wilkinson** garantisce convergenza cubica per matrici simmetriche.

## Convergenza e complessità

- Convergenza garantita per qualsiasi $A$ reale (con deflazione).
- Costo totale (Hessenberg + iterazione con shift): $O(n^3)$ — lineare nel numero di passi una volta in forma di Hessenberg.
- Implementazione pratica: algoritmo DGEHRD (Hessenberg) + DHSEQR (QR) in LAPACK.

## Relazione con il metodo delle potenze

L'iterazione QR può essere vista come l'applicazione simultanea del [[Metodo delle potenze]] a tutti gli autovettori contemporaneamente (metodo delle potenze simultanee / ortogonalizzato).

## Connessioni

- Richiede: [[Fattorizzazione QR]], [[Autovalori e autovettori]]
- Si collega a: [[Metodo delle potenze]], [[Singular Value Decomposition]], [[Cerchi di Gershgorin]]
- Discusso in: [[Metodi Numerici]]

## Fonti

- [[Dispense Metodi Numerici — Galletti]]
