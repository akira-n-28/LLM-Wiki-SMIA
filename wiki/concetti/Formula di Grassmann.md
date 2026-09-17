---
tipo: concetto
titolo: Formula di Grassmann
tag: [algebra-lineare, matematica]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Formula di Grassmann

Dati $U, W \leq V$ sottospazi vettoriali di $V$ su $K$:

$$\dim_K(U + W) + \dim_K(U \cap W) = \dim_K U + \dim_K W$$

## Interpretazione

La somma delle dimensioni dei due sottospazi conta due volte la dimensione della loro intersezione. La formula corregge questo doppio conteggio.

**Caso $U \cap W = \{O_V\}$:** la somma è diretta, $U \oplus W$, e

$$\dim_K(U \oplus W) = \dim_K U + \dim_K W$$

## Esempi in $\mathbb{R}^3$

- $U$ = piano ($\dim 2$), $W$ = piano ($\dim 2$): se $U \cap W$ è una retta ($\dim 1$), allora $\dim(U+W) = 2+2-1 = 3 = \dim \mathbb{R}^3$, cioè $U + W = \mathbb{R}^3$.
- $U$ = retta ($\dim 1$), $W$ = retta ($\dim 1$): se $U \cap W = \{O\}$, $\dim(U \oplus W) = 2$ (un piano).

## Somma diretta

$U \oplus W$ è caratterizzata dalla condizione $U \cap W = \{O_V\}$: ogni vettore $v \in U \oplus W$ si scrive in modo **unico** come $v = u + w$ con $u \in U$, $w \in W$.

## Calcolo di $U + W$ e $U \cap W$

**$U + W$:** si affiancano le basi di $U$ e $W$ in una matrice e si applica [[Algoritmo di Gauss-Jordan]] per trovare il rango.

**$U \cap W$:** si scrive il sistema di equazioni cartesiane che definisce $U \cap W$ e si risolve.

## Connessioni

- Richiede: [[Sottospazio vettoriale]], [[Base di uno spazio vettoriale]]
- Strumento: [[Algoritmo di Gauss-Jordan]]
- Discusso in: [[Algebra Lineare]]

## Fonti

- [[Dispense AlgLin — Galletti]]
