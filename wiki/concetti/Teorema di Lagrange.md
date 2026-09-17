---
tipo: concetto
titolo: Teorema di Lagrange
tag: [algebra, matematica, strutture-algebriche]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Teorema di Lagrange

## Classi laterali

Dato $H \leq G$, le **classi laterali sinistre** di $H$ in $G$ sono i sottoinsiemi:

$$gH = \{gh \mid h \in H\}, \quad g \in G$$

Analogamente le **classi laterali destre** $Hg = \{hg \mid h \in H\}$. Le classi laterali sinistre formano una **partizione** di $G$: ogni elemento appartiene ad esattamente una classe, e $|gH| = |H|$ per ogni $g$.

## Teorema

**Teorema di Lagrange.** Se $G$ è un gruppo finito e $H \leq G$, allora $|H|$ divide $|G|$. Più precisamente:

$$|G| = |H| \cdot [G : H]$$

dove $[G : H]$ è il numero di classi laterali sinistre di $H$ in $G$, detto **indice** di $H$ in $G$.

**Dimostrazione (schema).** Le classi laterali $\{gH\}$ partono da $G$, sono a due a due disgiunte, e ciascuna ha cardinalità $|H|$. Contando gli elementi: $|G| = |H| \cdot |\{gH : g \in G\}|$.

## Corollari

**Corollario 1** (ordine elemento divide ordine gruppo). Se $G$ finito e $g \in G$, allora $O(g) \mid |G|$. In particolare $g^{|G|} = e_G$.

**Corollario 2** (Teorema di Eulero). Se $\gcd(a, n) = 1$, allora $a^{\varphi(n)} \equiv 1 \pmod{n}$.

*Prova:* applicare Corollario 1 a $g = [a]$ in $U(\mathbb{Z}_n)$, che ha ordine $\varphi(n)$.

**Corollario 3** (Piccolo Teorema di Fermat). Se $p$ primo e $p \nmid a$, allora $a^{p-1} \equiv 1 \pmod{p}$.

*Prova:* caso speciale con $n = p$, $\varphi(p) = p - 1$.

**Corollario 4**. Ogni gruppo di ordine primo è ciclico. Se $|G| = p$ primo, allora per qualsiasi $g \neq e$: $O(g) \mid p$ e $O(g) \neq 1$, quindi $O(g) = p$ e $G = \langle g \rangle$.

## Attenzione: il viceversa è falso

Il teorema di Lagrange non ha viceversa in generale: non è detto che per ogni divisore $d$ di $|G|$ esista un sottogruppo di ordine $d$. Esempio: $A_4$ ha ordine 12 ma non ha sottogruppi di ordine 6 (il gruppo di Klein $V_4 \leq A_4$ ha ordine 4, non 6).

Il viceversa vale però per i **gruppi ciclici** e per certi gruppi speciali (Sylow).

## Connessioni

- Prerequisito: [[Sottogruppo]], [[Gruppo (struttura algebrica)]]
- Applicazione: [[Aritmetica modulare]], [[Algoritmo di Euclide]]
- Coniugio e normalità: [[Classi di coniugio]], [[Sottogruppo]]
- In $S_n$: [[Gruppo simmetrico]]
- Discusso in: [[Strutture Algebriche]]

## Fonti

- [[Dispense StrAlg — Galletti]] (§3.3.1, pp. 104-107)
