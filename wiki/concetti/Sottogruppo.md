---
tipo: concetto
titolo: Sottogruppo
tag: [algebra, matematica, strutture-algebriche]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Sottogruppo

Dato $(G, \star)$ un [[Gruppo (struttura algebrica)|gruppo]], un **sottogruppo** è un sottoinsieme $S \subseteq G$ non vuoto tale che $(S, \star)$ sia a sua volta un gruppo (con la stessa operazione). Si scrive $S \leq G$.

## Criteri di verifica

**Criterio 1** — $S \leq G$ se e solo se:
1. $e_G \in S$
2. $\forall s \in S: s^{-1} \in S$
3. $\forall s, s' \in S: s \star s' \in S$

**Criterio 2** — $S \leq G$ se e solo se $S \neq \emptyset$ e:
$$\forall s_1, s_2 \in S: s_1 \star s_2^{-1} \in S$$

## Sottogruppo generato

Il **sottogruppo generato da $X \subseteq G$** è il più piccolo sottogruppo di $G$ contenente $X$:

$$\langle X \rangle = \bigcap_{\substack{H \leq G \\ X \subseteq H}} H$$

Per $X = \{g\}$: $\langle g \rangle = \{g^i \mid i \in \mathbb{Z}\}$ — l'insieme di tutte le potenze (positive e negative) di $g$.

## Sottogruppo normale

$H \leq G$ è **normale** ($H \unlhd G$) se le classi laterali destre e sinistre coincidono: $Hg = gH$ per ogni $g \in G$. Equivalentemente: $gHg^{-1} = H$ per ogni $g \in G$.

Il [[Omomorfismo di gruppi|nucleo]] di ogni omomorfismo è un sottogruppo normale.

## Esempi

- $n\mathbb{Z} = \{nk \mid k \in \mathbb{Z}\} \leq (\mathbb{Z}, +)$ per ogni $n$ (i sottogruppi di $\mathbb{Z}$ sono esattamente questi).
- $A_n = \{\sigma \in S_n \mid \sigma \text{ pari}\} \leq S_n$ (indice 2, quindi normale).
- $Z(G) \leq G$ (centro del gruppo).
- Intersezione di sottogruppi: $H, K \leq G \Rightarrow H \cap K \leq G$.

## Connessioni

- Gruppo base: [[Gruppo (struttura algebrica)]]
- Classi laterali: [[Teorema di Lagrange]]
- Normalità: [[Omomorfismo di gruppi]]
- In $\mathbb{Z}_n$: [[Aritmetica modulare]]
- Discusso in: [[Strutture Algebriche]]

## Fonti

- [[Dispense StrAlg — Galletti]] (§3.3, pp. 96-104)
