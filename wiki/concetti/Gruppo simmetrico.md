---
tipo: concetto
titolo: Gruppo simmetrico
tag: [algebra, matematica, strutture-algebriche]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Gruppo simmetrico

Il **gruppo simmetrico** $S_n$ è il [[Gruppo (struttura algebrica)|gruppo]] di tutte le biiezioni $\sigma: [n] \to [n]$ con la composizione funzionale:

$$S_n = \{\sigma: [n] \to [n] \mid \sigma \text{ biunivoca}\}, \quad |S_n| = n!$$

$(S_n, \circ)$ è un gruppo finito **non abeliano** per $n \geq 3$.

## Struttura tramite cicli

Ogni $\sigma \in S_n$ si scrive univocamente come prodotto di **cicli disgiunti**. Un ciclo $(a_1\, a_2 \cdots a_r)$ muove gli elementi $a_1 \to a_2 \to \cdots \to a_r \to a_1$ e lascia fissi gli altri. I cicli disgiunti commutano.

**Esempio** ($n=6$):
$$\sigma = \begin{pmatrix}1&2&3&4&5&6\\2&3&4&6&5&1\end{pmatrix} = (1\;2\;3\;4\;6)(5)$$

**Ordine** di $\sigma = C_1 \cdots C_k$: $O(\sigma) = \text{mcm}(|C_1|, \ldots, |C_k|)$.

## Orbite

L'**orbita** di $x \in [n]$ tramite $\sigma$ è la classe di equivalenza della relazione $x \equiv_\sigma y \Leftrightarrow \exists i \in \mathbb{Z}: y = \sigma^i(x)$:

$$\mathcal{O}_\sigma(x) = \{\sigma^i(x) : i \in \mathbb{Z}\}$$

Le orbite formano una partizione di $[n]$ e corrispondono ai cicli di $\sigma$.

## Sottogruppi notevoli

- $A_n \leq S_n$: **gruppo alterno**, permutazioni pari, $|A_n| = n!/2$ per $n \geq 2$.
- $\langle \sigma \rangle = \{e, \sigma, \sigma^2, \ldots, \sigma^{O(\sigma)-1}\}$: sottogruppo ciclico generato da $\sigma$.

## Struttura ciclica e coniugio

Due permutazioni sono **coniugate** in $S_n$ $\Leftrightarrow$ hanno la stessa struttura ciclica (stesse lunghezze dei cicli) $\Leftrightarrow$ corrispondono alla stessa partizione di $n$. Le [[Classi di coniugio]] in $S_n$ sono in biezione con le partizioni di $n$.

## Gruppi ciclici come sottogruppi

$G$ è **ciclico** se $\exists g \in G: G = \langle g \rangle$. Ogni gruppo ciclico finito di ordine $n$ è isomorfo a $\mathbb{Z}_n$: $C_n \cong (\mathbb{Z}_n, +)$.

Tutti i sottogruppi di $(\mathbb{Z}, +)$ hanno la forma $m\mathbb{Z} = \{mh \mid h \in \mathbb{Z}\}$.

## Connessioni

- Struttura di base: [[Gruppo (struttura algebrica)]]
- Permutazioni: [[Permutazione]]
- Coniugio: [[Classi di coniugio]]
- Sottogruppi: [[Sottogruppo]], [[Teorema di Lagrange]]
- Discusso in: [[Strutture Algebriche]]

## Fonti

- [[Dispense StrAlg — Galletti]] (§3.2-3.3, pp. 84-106)
