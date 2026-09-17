---
tipo: concetto
titolo: Power iteration
tag: [algebra-lineare, calcolo-numerico]
cluster: algebra
ultima-modifica: 2026-04-30
---

# Power iteration

Algoritmo iterativo per calcolare l'**autovalore di modulo massimo** (e il corrispondente autovettore) di una matrice $A$.

## Algoritmo

Si parte da un vettore iniziale $v_0 \neq 0$ (tipicamente casuale) e si itera:

$$
v_{t+1} = \frac{A v_t}{\|A v_t\|}
$$

Sotto ipotesi blande (autovalore dominante semplice e $v_0$ con componente non nulla lungo l'autovettore associato), $v_t$ converge all'autovettore dominante. L'autovalore corrispondente si stima poi via [[Quoziente di Rayleigh]]: $\lambda \approx v_t^\top A v_t / v_t^\top v_t$.

## Esempio

$A = \begin{pmatrix} 2 & 1 \\ 1 & 2 \end{pmatrix}$, $v_0 = (1, 0)^\top$. Dopo pochi passi $v_t \to \frac{1}{\sqrt 2}(1, 1)^\top$, autovettore associato a $\lambda = 3$.

## Varianti

- **Inverse iteration**: applicata ad $A^{-1}$ — converge al **minore** autovalore (utile fattorizzando LU una volta sola).
- **Shift**: applicata a $(A - \sigma I)^{-1}$ — converge all'autovalore più vicino a $\sigma$. Strategia chiave per isolare autovalori interni.

## A cosa serve

- Calcolo veloce della prima componente in [[Principal Component Analysis|PCA]]/[[Singular Value Decomposition|SVD]] quando solo i top-$k$ servono.
- PageRank di Google (è essenzialmente power iteration sulla matrice di transizione).
- [[Metodi Numerici]] — argomento centrale del calcolo di autovalori.

## Collegamenti

- Stima dell'autovalore: [[Quoziente di Rayleigh]]
- Usato per: [[Singular Value Decomposition]], [[Principal Component Analysis]]
- Discusso in: [[Machine Learning]], [[Metodi Numerici]] (verrà collegato)

## Fonti

- [[Dispense Machine Learning — Galletti]] (§6.2, p. 20)
