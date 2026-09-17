---
tipo: concetto
titolo: Relazione d'ordine
tag: [algebra, matematica, teoria-degli-insiemi]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Relazione d'ordine

Una relazione $\rho$ su $A$ è una **relazione d'ordine** (o **ordine parziale**) se è:

| Proprietà | Condizione |
|---|---|
| Riflessiva (R) | $\forall x: x\rho x$ |
| Antisimmetrica (As) | $x\rho y \land y\rho x \Rightarrow x = y$ |
| Transitiva (T) | $x\rho y \land y\rho z \Rightarrow x\rho z$ |

La coppia $(A, \rho)$ si dice **insieme parzialmente ordinato (POSET)**. Se $\rho$ è anche **totale** ($\forall x,y: x\rho y \lor y\rho x$) si parla di **ordine totale** (o lineare).

## Diagramma di Hasse

Rappresentazione grafica di un POSET finito: si disegna un segmento tra $x$ e $y$ (con $y$ sopra $x$) se $x < y$ e non esiste $z$ con $x < z < y$ (relazione di **copertura** $x \prec y$).

Esempio: $(D_{12}, |)$ con $D_{12} = \{1,2,3,4,6,12\}$:
```
      12
     /  \
    4    6
    |   / \
    2  2   3
     \ |  /
       1
```

## Massimo, minimo, massimale, minimale

Dato $(X, \leq)$:
- **Massimo** $M$: $\forall x \in X, x \leq M$ (unico se esiste; è anche massimale)
- **Minimo** $m$: $\forall x \in X, m \leq x$ (unico se esiste; è anche minimale)
- **Massimale** $M_0$: $\nexists x \in X, x \neq M_0$ con $M_0 \leq x$ (può non essere unico)
- **Minimale** $m_0$: $\nexists x \in X, x \neq m_0$ con $x \leq m_0$ (può non essere unico)

**NB:** In un ordine parziale un massimale non è necessariamente massimo.

## Divisibilità in $\mathbb{N}^*$

La relazione $a | b$ ($a$ divide $b$: $\exists q \in \mathbb{N}: b = aq$) su $\mathbb{N}^* = \mathbb{N} \setminus \{0\}$ è un ordine parziale (non totale). Ha minimo $m = 1$ ma in genere più massimali.

## Principio del buon ordinamento

Ogni sottoinsieme non vuoto di $\mathbb{N}$ ha un elemento minimo. Equivalente al [[Principio di induzione]].

## Connessioni

- Confronta con: [[Relazione di equivalenza]]
- Applicazione: [[Massimo comun divisore]] (divisibilità come ordine), [[Sottogruppo]] (reticolo dei sottogruppi)
- Discusso in: [[Strutture Algebriche]]

## Fonti

- [[Dispense StrAlg — Galletti]] (§1.2.2, pp. 19-23)
