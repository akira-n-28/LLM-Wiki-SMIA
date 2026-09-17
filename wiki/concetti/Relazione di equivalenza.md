---
tipo: concetto
titolo: Relazione di equivalenza
tag: [algebra, matematica, teoria-degli-insiemi]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Relazione di equivalenza

Una relazione $\rho$ su un insieme $A$ è di **equivalenza** se soddisfa simultaneamente:

| Proprietà | Simbolo | Condizione |
|---|---|---|
| Riflessività | (R) | $\forall x \in A: x\rho x$ |
| Simmetria | (S) | $\forall x,y \in A: x\rho y \Rightarrow y\rho x$ |
| Transitività | (T) | $\forall x,y,z \in A: (x\rho y \land y\rho z) \Rightarrow x\rho z$ |

## Classi di equivalenza

Data $\sim$ relazione di equivalenza su $A$, la **classe di equivalenza** di $a \in A$ è:

$$[a] := \{b \in A \mid b \sim a\} \subseteq A$$

Proprietà fondamentali:
- $[a] \neq \emptyset$ (riflessività: $a \in [a]$)
- $[a] = [b] \Leftrightarrow a \sim b$
- $a \not\sim b \Rightarrow [a] \cap [b] = \emptyset$ (le classi distinte sono disgiunte)

## Insieme quoziente

L'**insieme quoziente** di $A$ modulo $\sim$ è la famiglia di tutte le classi distinte:

$$A/{\sim} := \{[a] \mid a \in A\}$$

Esempio: $\mathbb{Z}/{\equiv_n} = \{[0]_n, [1]_n, \ldots, [n-1]_n\}$ ha $n$ classi.

## Corrispondenza con le partizioni

**Teorema.** Le relazioni di equivalenza su $A$ sono in corrispondenza biunivoca con le partizioni insiemistiche di $A$:
- Ogni $\sim$ determina la partizione $A/{\sim}$ (le classi sono a due a due disgiunte e ricoprono $A$).
- Ogni partizione $\mathcal{F} = \{A_\alpha\}$ determina la relazione $x \sim_\mathcal{F} y \Leftrightarrow \exists \alpha: x,y \in A_\alpha$.

## Esempi

| Insieme $A$ | Relazione $\sim$ | Classi = |
|---|---|---|
| Rette del piano | parallelismo | fasci di rette parallele |
| $\mathbb{Z}$ | congruenza mod $n$ | $[0]_n, [1]_n, \ldots, [n-1]_n$ |
| $S_n$ | coniugio $\sigma' = \tau\sigma\tau^{-1}$ | permutazioni con stessa struttura ciclica |

## Connessioni

- Prerequisito: Prodotto cartesiano, sottoinsiemi
- Porta a: [[Relazione d'ordine]], [[Aritmetica modulare]], [[Classi di coniugio]]
- Usata in: [[Algoritmo di Gauss-Jordan]] (classi di riga-equivalenza), [[Sottogruppo]] (classi laterali)
- Discusso in: [[Strutture Algebriche]]

## Fonti

- [[Dispense StrAlg — Galletti]] (§1.2, pp. 9-19)
