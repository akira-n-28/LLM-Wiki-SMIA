---
tipo: concetto
titolo: Gruppo (struttura algebrica)
tag: [algebra, matematica, strutture-algebriche]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Gruppo (struttura algebrica)

Un **gruppo** è una coppia $(G, \star)$ dove $G$ è un insieme non vuoto e $\star: G \times G \to G$ è un'operazione che soddisfa:

| Assioma | Condizione |
|---|---|
| Associatività | $\forall g, g', g'' \in G: (g \star g') \star g'' = g \star (g' \star g'')$ |
| Elemento neutro | $\exists e \in G: e \star g = g \star e = g \;\forall g$ |
| Inverso | $\forall g \in G \;\exists g^{-1} \in G: g \star g^{-1} = g^{-1} \star g = e$ |

Se $\star$ è anche commutativa $(g \star g' = g' \star g)$, il gruppo si dice **abeliano**.

## Gerarchia di strutture

$$\text{semigruppo} \subset \text{monoide} \subset \text{gruppo}$$

- **Semigruppo** $(S, \star)$: chiusura + associatività.
- **Monoide** $(M, \star)$: semigruppo + elemento neutro.
- **Gruppo** $(G, \star)$: monoide + inverso per ogni elemento.

## Esempi fondamentali

| Gruppo | Operazione | Abeliano? | Ordine |
|---|---|---|---|
| $(\mathbb{Z}, +)$ | somma | sì | $\infty$ |
| $(\mathbb{Q}\setminus\{0\}, \cdot)$ | prodotto | sì | $\infty$ |
| $(\mathbb{Z}_n, +)$ | somma mod $n$ | sì | $n$ |
| $(U(\mathbb{Z}_n), \cdot)$ | prodotto mod $n$ | sì | $\varphi(n)$ |
| $(S_n, \circ)$ | composizione | no ($n\geq3$) | $n!$ |

## Proprietà di base

- L'elemento neutro è unico.
- L'inverso di ogni elemento è unico.
- **Legge di cancellazione:** $ax = bx \Leftrightarrow a = b$.
- $(a \star b)^{-1} = b^{-1} \star a^{-1}$, $(a^{-1})^{-1} = a$.

## Ordine di un elemento

L'**ordine** (o periodo) di $g \in G$ è il più piccolo $r > 0$ tale che $g^r = e_G$. Se non esiste, $g$ è **aperiodico**.

- $g$ aperiodico $\Rightarrow$ $\langle g \rangle \cong (\mathbb{Z}, +)$ (infinito).
- $O(g) = n$ $\Rightarrow$ $\langle g \rangle = \{e, g, g^2, \ldots, g^{n-1}\}$ ($n$ elementi distinti).
- In un gruppo finito: $g^{|G|} = e_G$ (corollario del [[Teorema di Lagrange]]).

## Connessioni

- Sottostruttura: [[Sottogruppo]]
- Esempio principale: [[Gruppo simmetrico]]
- Omomorfismi: [[Omomorfismo di gruppi]]
- Classi laterali: [[Teorema di Lagrange]]
- Aritmetica: [[Aritmetica modulare]]
- Discusso in: [[Strutture Algebriche]], [[Algebra Lineare]] (spazi vettoriali come gruppi abeliani)

## Fonti

- [[Dispense StrAlg — Galletti]] (§3.1-3.2, pp. 80-95)
