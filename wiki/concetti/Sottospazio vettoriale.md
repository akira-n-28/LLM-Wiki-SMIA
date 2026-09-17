---
tipo: concetto
titolo: Sottospazio vettoriale
tag: [algebra-lineare, matematica]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Sottospazio vettoriale

Dato $V$ [[Spazio vettoriale]] su $K$, un sottoinsieme $W \subseteq V$ è un **sottospazio vettoriale** di $V$ (si scrive $W \leq V$) se $W$, con le stesse operazioni di $V$, è a sua volta uno spazio vettoriale.

## Criteri di verifica

**Criterio 1 (tre condizioni):** $W$ è sottospazio di $V$ se e solo se:
1. $W \neq \emptyset$
2. $\forall u, v \in W: u + v \in W$ (chiuso per la somma)
3. $\forall c \in K, u \in W: c \cdot u \in W$ (chiuso per il prodotto scalare)

La condizione 3 implica l'esistenza dell'elemento neutro ($c = 0_K \Rightarrow 0_K \cdot u = O_V \in W$) e dell'opposto ($c = -1_K$).

**Criterio 2 (combinazione lineare):** equivalente ma più compatto: $W$ è sottospazio se e solo se

$$\forall c, d \in K,\ u, v \in W:\quad c \cdot u + d \cdot v \in W$$

## Esempi

- $W = \{O_V\}$ (sottospazio banale, dimensione 0) e $V$ stesso (dimensione $n$) sono sempre sottospazi.
- In $\mathbb{R}^3$: il piano $T = \{(x,y,z) : 2x+y-z=0\}$ è un sottospazio (si verifica con il Criterio 1).
- In $\mathbb{R}^3$: $Z = \{(x,y,0) : x, y \in \mathbb{R}\}$ è un sottospazio (piano $xy$).
- In $M_2(\mathbb{R})$: le matrici a traccia nulla $\{A : \mathrm{Tr}(A) = 0\}$ formano un sottospazio di dimensione 3.
- **Controesempio:** $S = \{A \in M_2(\mathbb{R}) : a_{11} \cdot a_{21} = 0\}$ — non è sottospazio perché la somma di due elementi di $S$ può uscire da $S$.

## Operazioni sui sottospazi

Dati $U, W \leq V$:
- $U \cap W \leq V$ — l'intersezione di sottospazi è un sottospazio.
- $U + W = \{u + w : u \in U, w \in W\} = \mathrm{span}(U \cup W) \leq V$ — la somma è un sottospazio.
- Se $U \cap W = \{O_V\}$, la somma si chiama **somma diretta** $U \oplus W$: ogni vettore di $U \oplus W$ si scrive in modo unico come $u + w$.

Per la formula di Grassmann, vedi [[Formula di Grassmann]].

## Proprietà dimensionali

Se $\dim_K V = n$ e $W \leq V$:
- $\dim_K W \leq \dim_K V$
- $\dim_K W = \dim_K V \Leftrightarrow W = V$
- $W \neq \{O_V\} \Rightarrow \dim_K W \geq 1$

## Connessioni

- Definito in: [[Spazio vettoriale]]
- Genera: [[Sottospazio generato]], [[Base di uno spazio vettoriale]]
- Operazioni: [[Formula di Grassmann]]
- Esempi chiave: [[Applicazione lineare]] (ker $T$ e Im $T$ sono sottospazi)
- Discusso in: [[Algebra Lineare]]

## Fonti

- [[Dispense AlgLin — Galletti]]
