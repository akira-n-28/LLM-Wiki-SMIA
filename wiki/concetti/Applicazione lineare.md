---
tipo: concetto
titolo: Applicazione lineare
tag: [algebra-lineare, matematica]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Applicazione lineare (Trasformazione lineare)

Una **applicazione lineare** (o trasformazione lineare, omomorfismo) è una funzione $T: V \to W$ tra spazi vettoriali su $K$ tale che:

$$\forall c, d \in K,\ v_1, v_2 \in V:\quad T(c \cdot v_1 + d \cdot v_2) = c \cdot T(v_1) + d \cdot T(v_2)$$

Equivalentemente: $T(v_1 + v_2) = T(v_1) + T(v_2)$ e $T(c \cdot v) = c \cdot T(v)$.

## Sottospazi associati

Data $T: V \to W$:

- **Nucleo** (kernel): $\ker T = \{v \in V : T(v) = 0_W\} \leq V$
- **Immagine**: $\mathrm{Im}(T) = \{T(v) : v \in V\} \leq W$

$T$ è iniettiva $\Leftrightarrow \ker T = \{O_V\}$; $T$ è suriettiva $\Leftrightarrow \mathrm{Im}(T) = W$.

## Matrice associata

Fissate basi ordinate $\mathcal{B} = (v_1, \ldots, v_n)$ di $V$ e $\mathcal{C} = (w_1, \ldots, w_m)$ di $W$, esiste un'unica matrice $A \in M_{m,n}(K)$ tale che $L_A = F_\mathcal{C} \circ T \circ F_\mathcal{B}^{-1}$. Le **colonne** di $A$ sono le coordinate in base $\mathcal{C}$ dei trasformati $T(v_1), \ldots, T(v_n)$:

$$A^{(i)} = F_\mathcal{C}(T(v_i))$$

In particolare, $\mathrm{Im}(L_A) = \mathrm{span}(\text{colonne di } A)$.

## Teorema della dimensione (Rank-Nullity)

$$\dim_K V = \dim_K \ker T + \dim_K \mathrm{Im}(T)$$

ossia $n = n(T) + \mathrm{rg}(T)$, con $n(T) = \dim \ker T$ (nullità) e $\mathrm{rg}(T) = \dim \mathrm{Im}(T)$ (rango). Per $T = L_A$ con $A \in M_{m,n}$:

$$n = n(A) + \mathrm{rg}(A)$$

dove $n(A) = n - \mathrm{rg}(A)$ = numero di variabili libere nel sistema omogeneo $AX = 0$.

## Cambio di base

Se $A$ rappresenta $T$ nelle basi $\mathcal{B}$ (su $V$) e $\mathcal{C}$ (su $W$), e si cambiano le basi in $\mathcal{B}'$ e $\mathcal{C}'$ con matrici di cambiamento $B$ ($\mathcal{B}' = \mathcal{B} \cdot B$) e $C$ ($\mathcal{C}' = \mathcal{C} \cdot C$), allora la nuova matrice è:

$$A' = C^{-1} \cdot A \cdot B$$

## Endomorfismo e similitudine

Se $V = W$ (e si usa la stessa base), $T: V \to V$ è un **endomorfismo**. Cambiando base $\mathcal{B} \to \mathcal{B}'$ con matrice $B$:

$$A' = B^{-1} \cdot A \cdot B$$

$A$ e $A'$ sono **matrici simili**: rappresentano lo stesso endomorfismo in basi diverse (vedi [[Diagonalizzazione]]).

## Isomorfismo

Se $T$ è biettiva (iniettiva e suriettiva), è un **isomorfismo**. Tutti gli spazi di dimensione $n$ su $K$ sono isomorfi a $K^n$.

## Connessioni

- Generalizza: [[Mappe lineari]]
- Strumento di calcolo: [[Algoritmo di Gauss-Jordan]]
- Porta a: [[Diagonalizzazione]], [[Autovalori e autovettori]]
- Teorema chiave: [[Teorema della dimensione (algebra lineare)]]
- Discusso in: [[Algebra Lineare]]

## Fonti

- [[Dispense AlgLin — Galletti]]
