---
tipo: concetto
titolo: Classi di coniugio
tag: [algebra, matematica, strutture-algebriche]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Classi di coniugio

Dato un [[Gruppo (struttura algebrica)|gruppo]] $(G, \cdot)$, la relazione di **coniugio** su $G$ è:

$$g \sim g' \;\Leftrightarrow\; \exists x \in G: g' = x g x^{-1}$$

Questa è una [[Relazione di equivalenza]] su $G$ (R: $g = e\,g\,e^{-1}$; S: se $g' = xgx^{-1}$ allora $g = x^{-1}g'x$; T: composizione di coniugi). La classe di equivalenza di $g$ si chiama **classe di coniugio**:

$$[g]_\sim = \{g' \in G \mid g' \sim g\} = \{xgx^{-1} \mid x \in G\}$$

## In $S_n$: struttura ciclica

**Proposizione.** Due permutazioni $\sigma, \sigma' \in S_n$ sono coniugate $\Leftrightarrow$ hanno la stessa struttura ciclica (stesse lunghezze dei cicli disgiunti).

- Se $\sigma = (a_1 \cdots a_r)(b_1 \cdots b_s)\cdots$ e $\tau \in S_n$, allora $\tau\sigma\tau^{-1} = (\tau(a_1) \cdots \tau(a_r))(\tau(b_1)\cdots\tau(b_s))\cdots$.
- Dato $\sigma'$ con la stessa struttura di $\sigma$, si costruisce esplicitamente $\tau$ con $\sigma' = \tau\sigma\tau^{-1}$.

**Corollario.** Le classi di coniugio in $S_n$ sono in biezione con le **partizioni di $n$**.

## Gruppi abeliani

Se $G$ è abeliano: $xgx^{-1} = g$ per ogni $x$, quindi ogni classe di coniugio è un singleton $\{g\}$.

## Centro del gruppo

Il **centro** di $G$ è:
$$Z(G) = \{g \in G \mid gx = xg \;\forall x \in G\} = \{g \in G \mid [g]_\sim = \{g\}\}$$

$Z(G) \leq G$ (è un [[Sottogruppo]]). Se $G$ abeliano, $Z(G) = G$.

## Connessioni

- Relazione sottostante: [[Relazione di equivalenza]]
- Gruppo simmetrico: [[Gruppo simmetrico]], [[Permutazione]]
- Struttura: [[Gruppo (struttura algebrica)]], [[Sottogruppo]]
- Discusso in: [[Strutture Algebriche]]

## Fonti

- [[Dispense StrAlg — Galletti]] (§3.3.2, pp. 107-109)
