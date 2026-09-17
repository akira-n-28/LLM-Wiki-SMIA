---
tipo: concetto
titolo: Locality Sensitive Hashing
tag: [algoritmi, machine-learning, hashing, similarità]
cluster: algoritmi
fonti: 1
ultima-modifica: 2026-05-05
---

# Locality Sensitive Hashing

## Similarità e distanza di Jaccard

Dati due insiemi $A, B$:

$$J(A,B) = \frac{|A \cap B|}{|A \cup B|} \qquad d(A,B) = 1 - J(A,B)$$

La distanza di Jaccard è una metrica su insiemi finiti.

## Locality Sensitive Hashing (LSH)

Un **LSH** per una funzione di similarità $S: U \times U \to [0,1]$ è una distribuzione di probabilità su un insieme di funzioni hash $\mathcal{H}$ tale che:

$$\Pr_{h \sim \mathcal{H}}[h(A) = h(B)] = S(A,B) \quad \forall A, B$$

Elementi simili hanno alta probabilità di cadere nello stesso bucket; elementi dissimili bassa.

**Utilizzo pratico:** dato un grande dataset, anziché calcolare tutte le $\binom{n}{2}$ similarità, si raggruppano gli elementi con lo stesso hash e si confrontano solo quelli — riduzione drastica del numero di confronti.

## Single Linkage Clustering

Algoritmo gerarchico che parte con ogni punto come cluster separato e fonde iterativamente i due cluster con distanza minima. Restituisce un **dendrogramma** (albero di clustering).

**Terminazione:** il risultato dipende dalla condizione di stop:
- Tutte le distanze $> r$ fissato → Ricchezza + Consistenza
- Tutte le distanze $> x \cdot d_{\max}$ ($x \in (0,1)$) → Invarianza di scala + Ricchezza
- Si vuole $k$ cluster fissi → Invarianza di scala + Consistenza

**Impossibilità:** non esiste un algoritmo che soddisfi simultaneamente Invarianza di scala, Consistenza e Ricchezza (teorema di Kleinberg).

## Connessioni

- Paradigma: [[Problema degli esperti]] (contesto §4 AlgComp)
- Similarità: [[Metriche di classificazione]], [[Metriche di ranking]]
- Struttura dati: [[Tabella hash]]
- Applicazione ML: [[Sistemi di raccomandazione]], [[Word Embedding]]
- Discusso in: [[Algoritmi e Complessità]]

## Fonti

- [[Dispense Algoritmi — Galletti]] (§4.2, pp. 28)
