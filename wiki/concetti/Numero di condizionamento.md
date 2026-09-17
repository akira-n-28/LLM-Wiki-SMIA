---
tipo: concetto
titolo: Numero di condizionamento
tag: [calcolo-numerico, algebra-lineare, metodi-numerici]
cluster: numerico
fonti: 1
ultima-modifica: 2026-05-05
---

# Numero di condizionamento

Il **numero di condizionamento** di una matrice $A$ invertibile rispetto alla norma $p$ è:

$$K_p(A) = \|A\|_p \cdot \|A^{-1}\|_p \geq 1$$

Misura quanto il problema $Ax = b$ è sensibile a perturbazioni dei dati: se $K(A)$ è grande, piccoli errori in $b$ (o in $A$) producono grandi errori in $x$.

## Bound sull'errore relativo

Se $\tilde{b} = b + \delta b$ è un rhs perturbato e $\tilde{x}$ risolve $A\tilde{x} = \tilde{b}$, allora:

$$\frac{\|\tilde{x} - x\|}{\|x\|} \leq K(A) \cdot \frac{\|\delta b\|}{\|b\|}$$

Analogamente, se $A$ è perturbata in $\tilde{A} = A + \delta A$:

$$\frac{\|\tilde{x} - x\|}{\|x\|} \leq \frac{K(A)}{1 - K(A)\|\delta A\|/\|A\|} \cdot \frac{\|\delta A\|}{\|A\|}$$

In entrambi i casi, $K(A)$ è il fattore di amplificazione degli errori relativi.

## Proprietà chiave

**Per matrici simmetriche definite positive:**

$$K_2(A) = \frac{\lambda_{\max}}{\lambda_{\min}}$$

cioè il rapporto tra il massimo e il minimo autovalore (tutti positivi per SPD).

**Per matrici ortogonali:** $K_2(Q) = 1$ — le trasformazioni ortogonali non amplificano gli errori. Questo motiva l'uso della fattorizzazione QR per i minimi quadrati.

**Invarianza:** $K_p(A) = K_p(A^{-1})$.

**Moltiplicatività:** $K(AB) \leq K(A) \cdot K(B)$.

## Classificazione

| $K(A)$         | Sistema        |
|----------------|----------------|
| $\approx 1$    | ben condizionato |
| $10^6$–$10^8$  | moderatamente mal condizionato |
| $\gg 1/\varepsilon_M$ | effettivamente singolare per la macchina |

**Regola pratica:** si perdono $\approx \log_{10} K(A)$ cifre significative nella soluzione rispetto ai dati.

## Esempio: matrice di Hilbert

$$H_{ij} = \frac{1}{i+j-1}$$

$K_2(H_n)$ cresce esponenzialmente con $n$: per $n=10$, $K_2 \approx 10^{13}$. La matrice di Hilbert è l'esempio canonico di sistema mal condizionato.

## Legame con SVD

Se $A = U\Sigma V^T$ è la SVD, allora $\|A\|_2 = \sigma_1$ e $\|A^{-1}\|_2 = 1/\sigma_n$, quindi:

$$K_2(A) = \frac{\sigma_1}{\sigma_n}$$

il rapporto tra il valore singolare massimo e minimo.

## Connessioni

- Prerequisito di: [[Metodi iterativi per sistemi lineari]], [[Gradiente coniugato]]
- Si collega a: [[Sistemi lineari — metodi diretti]], [[Autovalori e autovettori]], [[Singular Value Decomposition]]
- Discusso in: [[Metodi Numerici]]

## Fonti

- [[Dispense Metodi Numerici — Galletti]]
