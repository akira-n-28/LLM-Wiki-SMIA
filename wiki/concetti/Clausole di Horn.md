---
tipo: concetto
titolo: Clausole di Horn
tag: [fond-ai, logica, clausole, programmazione-logica]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-04
---

# Clausole di Horn

Le **clausole di Horn** sono un sottoinsieme delle clausole CNF con struttura ristretta che consente algoritmi di inferenza lineari nel numero di clausole.

## Definizioni

**Letterale negativo**: letterale della forma $\lnot p$.
**Letterale positivo**: letterale della forma $p$.

**Clausola di Horn**: clausola con **al più un** letterale positivo.

**Clausola definita**: clausola con **esattamente un** letterale positivo:
- **Fatto**: clausola con un solo letterale positivo (nessuna premessa) — es. $\{p\}$
- **Regola**: clausola con un letterale positivo e uno o più negativi — es. $\{\lnot p, \lnot q, r\}$ che rappresenta $p \land q \to r$

**Clausola obiettivo** (goal): clausola **senza** letterali positivi:
- La clausola vuota $\bot$ è un caso particolare di goal
- In un programma logico, le clausole obiettivo rappresentano le query da dimostrare

## Interpretazione logica

Una clausola definita $\{\lnot p_1, \ldots, \lnot p_k, q\}$ si legge come:

$$p_1 \land \cdots \land p_k \to q$$

Le premesse sono i letterali negativi; la conclusione è il letterale positivo.

## Utilizzo nella deduzione automatica

Quando la KB è composta da **clausole definite**, si possono usare algoritmi specializzati — più efficienti della risoluzione generale:

- **Concatenazione in avanti**: guidata dai fatti, ragionamento bottom-up — cfr. [[Concatenazione in avanti e all'indietro]]
- **Concatenazione all'indietro**: guidata dalla query, ragionamento top-down — cfr. [[Concatenazione in avanti e all'indietro]]

Entrambi hanno complessità **lineare** nel numero di clausole.

## Dimostrazione con clausole obiettivo

Dato un goal $G$, un programma logico dimostra $G$ mostrando che $\text{KB} \cup \{\lnot G\}$ è insoddisfacibile (refutazione). La clausola obiettivo $\lnot G$ diventa il punto di partenza della catena di backward.

## Legame con Prolog

Le clausole di Horn sono il fondamento del linguaggio di programmazione logica **Prolog**: fatti e regole di Prolog sono clausole definite, e le query sono clausole obiettivo risolte tramite concatenazione all'indietro con unificazione.

## Relazione con la risoluzione

La risoluzione generale su clausole di Horn produce sempre clausole di Horn: il risolvente di due clausole con al più un letterale positivo ciascuna ha al più un letterale positivo.

## Esempio

KB composta da:
- Fatti: $\{p\}$, $\{q\}$
- Regole: $\{\lnot p, \lnot q, r\}$ (cioè $p \land q \to r$), $\{\lnot r, s\}$ (cioè $r \to s$)

Query: $s$?

Applicando concatenazione in avanti:
1. Fatti noti: $\{p, q\}$
2. Le premesse di $p \land q \to r$ sono soddisfatte → aggiungi $r$
3. Le premesse di $r \to s$ sono soddisfatte → aggiungi $s$ ✓

## Collegamenti

- Si fonda su: [[Risoluzione (RES)]], [[Logica proposizionale]]
- Usate in: [[Concatenazione in avanti e all'indietro]]
- Discusso in: [[Fondamenti di Intelligenza Artificiale]]

## Fonti

- [[Dispense FondAI — Galletti]] §6.5.1
