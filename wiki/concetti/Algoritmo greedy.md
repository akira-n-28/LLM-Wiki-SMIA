---
tipo: concetto
titolo: Algoritmo greedy
tag: [algoritmi, ottimizzazione, matematica]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-05
---

# Algoritmo greedy

Un **algoritmo greedy** costruisce la soluzione passo dopo passo: ad ogni passo sceglie l'opzione localmente ottima (secondo una regola $M$) senza mai tornare indietro. È rapido ma non sempre corretto.

## Schema generale

```
S ← ∅
while (istanza non vuota):
    scegli un elemento secondo regola M
    aggiungi a S se compatibile
    rimuovi elementi incompatibili
return S
```

## Correttezza greedy: tecnica di scambio

Per dimostrare che una regola $M^*$ è ottima, si mostra che:

1. La soluzione greedy $S$ è **ammissibile** (soddisfa i vincoli).
2. Per ogni soluzione ottima $O$, si può "scambiare" progressivamente $O$ con $S$ senza perdere qualità — così $|S| \geq |O|$.

## Paradigma: Interval Scheduling

Regola $M^* =$ "scegli l'intervallo con **earliest finish time**". Ottima. (cfr. [[Interval Scheduling]])

## Paradigma: Interval Partitioning

Regola: ordina per start time, assegna la prima risorsa disponibile. Ottimo: usa esattamente $\mathrm{Depth}(I)$ risorse. Con heap binaria: $O(n \log n)$. (cfr. [[Interval Partitioning]])

## Paradigma: Algoritmo di Huffman

Greedy su alberi binari per prefix-code di minima ABL. (cfr. [[Algoritmo di Huffman]])

## Confronto con Programmazione Dinamica

| Aspetto | Greedy | DP |
|---|---|---|
| Scelta | Una sola opzione lokalmente ottima | Esplora più alternative |
| Reversibilità | Irreversibile | Sottoproblemi risolti una volta |
| Complessità | In genere $O(n \log n)$ | In genere $O(n^2)$ o $O(nW)$ |
| Correttezza | Non sempre; richiede dimostrazione | Sempre (se la ricorrenza è corretta) |

## Connessioni

- Esempi: [[Interval Scheduling]], [[Interval Partitioning]], [[Algoritmo di Huffman]]
- Alternativa: [[Programmazione dinamica]]
- Strutture dati: [[Heap Sort]] (priority queue)
- Discusso in: [[Algoritmi e Complessità]]

## Fonti

- [[Dispense Algoritmi — Galletti]] (§2, pp. 9-20)
