---
tipo: concetto
titolo: Stable Matching
tag: [algoritmi, combinatoria, matematica]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-05
---

# Stable Matching

## Problema

Dati due insiemi $A$ e $B$ con $|A| = |B| = n$ e $A \cap B = \emptyset$, dove ogni elemento di $A$ ha una lista di preferenze totale su $B$ e viceversa: trovare un **matching stabile**.

**Matching perfetto:** biiezione $M \subseteq A \times B$ tale che ogni elemento è accoppiato esattamente una volta.

**Instabilità:** una coppia $\{a,b\}, \{a',b'\} \in M$ è instabile se $a$ preferisce $b'$ a $b$ **e** $b'$ preferisce $a$ ad $a'$ (entrambi vorrebbero "scappare" con l'altro).

**Matching stabile:** matching perfetto senza instabilità.

## Algoritmo di Gale-Shapley

Gli elementi di $A$ fanno proposte; $B$ accetta o rifiuta:

1. Ogni $a$ libero propone al miglior $b$ non ancora proposto.
2. $b$ accetta sempre se è libero; se già accoppiato con $a'$, accetta $a$ iff $a \succ_{b} a'$ (altrimenti rifiuta).
3. Si continua finché tutti sono accoppiati.

**Lemmi chiave:**
- (L1) Ogni $b$ rimane accoppiato dalla prima proposta in poi; i suoi partner non peggiorano.
- (L2) Le proposte di $a$ seguono ordine decrescente di preferenza (non migliorano).
- (L3) Se $a$ è libero, esiste ancora un $b$ cui non ha proposto.
- (L4) L'algoritmo termina con un matching perfetto.

**Teorema (stabilità).** Gale-Shapley termina con un matching stabile.

## Ottimalità

Definite $\mathrm{best}(a)$ = il miglior partner valido per $a$ tra tutti i matching stabili, e $\mathrm{worst}(b)$ = il peggiore:

- L'algoritmo restituisce $M^* = \{\{a, \mathrm{best}(a)\}\}$: ottimo per $A$, pessimo per $B$.

## Complessità

Con strutture dati opportune (array `apref`, `next`, `current`, `ranking`, lista concatenata per gli $a$ liberi), ogni iterazione del while costa $O(1)$:

$$T_{\text{GS}} = O(n^2)$$

## Connessioni

- Strutture dati: [[Algoritmo di Gauss-Jordan]] (analogia: pivot), [[Grafo]]
- Paradigma greedy: [[Algoritmo greedy]]
- Discusso in: [[Algoritmi e Complessità]]

## Fonti

- [[Dispense Algoritmi — Galletti]] (§1.1, pp. 3-8)
