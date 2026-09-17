---
tipo: concetto
titolo: Sottospazio generato
tag: [algebra-lineare, matematica]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Sottospazio generato (Span)

Dato un insieme finito $S = \{v_1, v_2, \ldots, v_k\} \subseteq V$, il **sottospazio generato** (o **span**) di $S$ è il più piccolo sottospazio di $V$ che contiene $S$:

$$\mathrm{span}(v_1, \ldots, v_k) = \langle v_1, \ldots, v_k \rangle = \{c_1 v_1 + c_2 v_2 + \cdots + c_k v_k \mid c_i \in K\}$$

È l'insieme di tutte le combinazioni lineari dei vettori di $S$.

## Sistema di generatori

$\{v_1, \ldots, v_k\}$ è un **sistema di generatori** per $V$ se $V = \mathrm{span}(v_1, \ldots, v_k)$, cioè se ogni vettore di $V$ si scrive come combinazione lineare dei $v_i$.

## Proprietà

- Se $v \in \mathrm{span}(v_1, \ldots, v_k)$, allora $\mathrm{span}(v, v_1, \ldots, v_k) = \mathrm{span}(v_1, \ldots, v_k)$ — aggiungere una combinazione lineare non estende lo span.
- $\mathrm{span}(U \cup W) = U + W$ per $U, W \leq V$ (vedi [[Formula di Grassmann]]).

## Estrarre una base dallo span

Per trovare una base di $\mathrm{span}(v_1, \ldots, v_k)$ si forma la matrice $A = [v_1 | \cdots | v_k]$ e si applica [[Algoritmo di Gauss-Jordan]]: le colonne di $A$ in posizione pivot sono linearmente indipendenti e generano lo stesso span.

$$\dim \mathrm{span}(v_1, \ldots, v_k) = \mathrm{rg}(A)$$

## Connessioni

- Costruito da: [[Dipendenza lineare]]
- Porta a: [[Base di uno spazio vettoriale]]
- Strumento di calcolo: [[Algoritmo di Gauss-Jordan]]
- Discusso in: [[Algebra Lineare]]

## Fonti

- [[Dispense AlgLin — Galletti]]
