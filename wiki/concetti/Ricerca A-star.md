---
tipo: concetto
titolo: Ricerca A*
aliases: ["Ricerca A*"]
tag: [fond-ai, ricerca, euristica, agenti]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-05
---

# Ricerca A*

A* è un algoritmo di ricerca informata che seleziona il nodo da espandere minimizzando la funzione:

$$f(n) = g(n) + h(n)$$

dove:
- $g(n)$: costo del cammino dallo stato iniziale al nodo $n$
- $h(n)$: **euristica ammissibile** — stima del costo per raggiungere lo stato obiettivo da $n$

con $h(n) \geq 0$ e $h(\text{obiettivo}) = 0$.

## Ricerca best-first greedy

Caso degenere: $f(n) = h(n)$. Espande per primo il nodo con $h$ più basso. Non garantisce ottimalità; complessità $O(|V|)$ temporale e spaziale in spazi finiti.

## Euristica ammissibile

**Definizione.** Un'euristica $h(n)$ è **ammissibile** se per ogni nodo $n$ non obiettivo:

$$h(n) \leq h^*(n)$$

dove $h^*(n)$ è il costo effettivo del cammino minimo da $n$ all'obiettivo. Un'euristica ammissibile non sovrastima mai.

## Ottimalità di A*

**Teorema.** La ricerca A* con euristica ammissibile è ottima rispetto al costo.

**Dimostrazione** (per assurdo). Sia $C$ il costo del cammino restituito. Supponiamo $\exists C^* < C$. Allora esiste un nodo $n$ sul cammino ottimo non ancora espanso. Ma:

$$f(n) = g^*(n) + h(n) \leq g^*(n) + h^*(n) = C^*$$

Quindi $f(n) \leq C^*$, ma allora $n$ sarebbe stato espanso prima del nodo obiettivo subottimo — contraddizione. $\square$

**Corollario**: una euristica che sovrastima può tagliare rami utili e restituire soluzioni non ottime.

## Consistenza

Un'euristica $h$ è **consistente** (o monotona) se per ogni nodo $n$ e successore $n'$ tramite azione $a$:

$$h(n) \leq c(n, a, n') + h(n')$$

Ricorda la disuguaglianza triangolare.

**Teorema.** Una euristica consistente è ammissibile.

**Corollario.** A* con euristica consistente è ottima.

## Proprietà fondamentali di A*

| Proprietà | Condizione |
|---|---|
| Completezza | Se l'euristica è ammissibile (spazio finito) |
| Ottimalità | Se l'euristica è consistente |
| Efficienza ottimale | Espande tutti e soli i nodi che qualsiasi altro algoritmo con la stessa euristica espanderebbe |

## Struttura dati

Per ogni nodo $n$ dell'albero di ricerca:
- $n.\text{stato}$: stato associato
- $n.\text{padre}$: nodo padre
- $n.\text{azione}$: azione che ha portato al nodo
- $n.\text{costo\_cammino}$: $g(n)$

La **frontiera** è implementata come coda con priorità su $f(n)$.

## Limiti

- Il numero di nodi espansi può crescere esponenzialmente con la lunghezza della soluzione
- Varianti: A* pesata (meno nodi, non ottimale), IDA* (memoria limitata), beam search

## Collegamenti

- Prerequisito di: [[Logica proposizionale]] (agenti KB come alternativa)
- Si collega a: [[Agente intelligente]] (agenti PS)
- Discusso in: [[Fondamenti di Intelligenza Artificiale]]

## Fonti

- [[Dispense FondAI — Galletti]] §2
