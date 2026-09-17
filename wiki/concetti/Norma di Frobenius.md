---
tipo: concetto
titolo: Norma di Frobenius
tag: [algebra-lineare, ml]
cluster: algebra
ultima-modifica: 2026-04-30
---

# Norma di Frobenius

La norma di **Frobenius** di una matrice $X \in \mathbb{R}^{m \times n}$ è:

$$
\|X\|_F^2 = \mathrm{Tr}(X^\top X) = \mathrm{Tr}(X X^\top) = \sum_{i,j} X_{ij}^2
$$

È l'estensione naturale della norma euclidea ai tensori bidimensionali: misura la "lunghezza" di una matrice come se fosse un vettore in $\mathbb{R}^{mn}$.

## Proprietà utili

- **Invarianza ciclica della traccia:** $\mathrm{Tr}(ABC) = \mathrm{Tr}(BCA)$ — permette di riscrivere prodotti complessi.
- **Caso vettoriale:** se $X$ è un vettore colonna, $\|X\|_F^2 = X^\top X$ (norma 2 al quadrato).
- **Differenza:** $\|A - B\|_F^2 = \mathrm{Tr}(A^\top A) + \mathrm{Tr}(B^\top B) - 2\,\mathrm{Tr}(A^\top B)$.

## Perché conta in ML

- È la metrica con cui [[Singular Value Decomposition|SVD]] fornisce la **migliore approssimazione di rango basso** ([[Singular Value Decomposition|teorema di Eckart-Young]]).
- Compare nella formulazione matriciale della [[Regressione lineare]] (errore quadratico totale).
- Definisce la "energia" complessiva di un dataset $X$ — la somma delle varianze lungo tutte le direzioni.

## Collegamenti

- Vedi anche: [[Singular Value Decomposition]], [[Principal Component Analysis]], [[Regressione lineare]]
- Persona: [[Frobenius]]

## Fonti

- [[Dispense Machine Learning — Galletti]] (def. 2.7, pp. 4-5)
