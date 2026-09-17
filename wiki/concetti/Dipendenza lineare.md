---
tipo: concetto
titolo: Dipendenza lineare
tag: [algebra-lineare, matematica]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Dipendenza lineare

## Combinazione lineare

Un vettore $v \in V$ è **combinazione lineare** di $v_1, v_2, \ldots, v_k \in V$ se esistono scalari $c_1, \ldots, c_k \in K$ tali che:

$$v = c_1 v_1 + c_2 v_2 + \cdots + c_k v_k$$

La combinazione è **banale** se $c_1 = c_2 = \cdots = c_k = 0$ (produce sempre $O_V$).

## Vettori linearmente indipendenti

Un insieme $\{v_1, v_2, \ldots, v_n\} \subseteq V$ è **linearmente indipendente** (o semplicemente *indipendente*) se l'unica combinazione lineare che dà $O_V$ è quella banale:

$$c_1 v_1 + c_2 v_2 + \cdots + c_n v_n = O_V \;\Rightarrow\; c_1 = c_2 = \cdots = c_n = 0$$

## Vettori linearmente dipendenti

L'insieme è **linearmente dipendente** se esistono scalari $c_1, \ldots, c_n$ **non tutti nulli** tali che:

$$c_1 v_1 + c_2 v_2 + \cdots + c_n v_n = O_V$$

In questo caso, ogni vettore con coefficiente non nullo si esprime come combinazione lineare degli altri.

## Esempi

**Indipendenti:** $v_1 = [2,0]$, $v_2 = [1,-1]$ in $\mathbb{R}^2$ — il sistema $c_1[2,0]+c_2[1,-1]=[0,0]$ impone $c_1 = c_2 = 0$.

**Dipendenti:** $v_1 = [3,-3]$, $v_2 = [1,-1]$ in $\mathbb{R}^2$ — $v_1 = 3v_2$, quindi $1\cdot v_1 - 3\cdot v_2 = O$: i due vettori puntano nella stessa direzione.

## Proprietà chiave

- $\{O_V\}$ è sempre dipendente (per $c = 1 \neq 0$: $1 \cdot O_V = O_V$).
- Se un sottoinsieme di vettori è dipendente, qualunque insieme più grande che lo contenga è anch'esso dipendente.
- Se $\dim_K V = n$ e ho più di $n$ vettori, sono necessariamente dipendenti.
- $v_1, \ldots, v_n$ sono indipendenti $\Leftrightarrow$ la matrice che li ha come colonne ha rango $n$.

## Legame con il rango

Dati $v_1, \ldots, v_k \in \mathbb{R}^n$, si forma la matrice $A = [v_1 | \cdots | v_k]$ e si applica Gauss-Jordan: le colonne in posizione pivot di $A$ sono linearmente indipendenti; le altre sono combinazioni lineari di queste. Cfr. [[Algoritmo di Gauss-Jordan]].

## Connessioni

- Prerequisito di: [[Base di uno spazio vettoriale]], [[Sottospazio generato]]
- Calcolo: [[Algoritmo di Gauss-Jordan]]
- Discusso in: [[Algebra Lineare]]

## Fonti

- [[Dispense AlgLin — Galletti]]
