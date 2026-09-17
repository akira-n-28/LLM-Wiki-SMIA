---
tipo: concetto
titolo: Curse of dimensionality
tag: [ml, statistica, geometria]
cluster: ml
ultima-modifica: 2026-04-30
---

# Curse of dimensionality

Difficoltà nell'analisi dei dati che emerge quando il numero di variabili (dimensione $d$ dello spazio delle feature) cresce. Il volume cresce **esponenzialmente** in $d$, quindi i campioni diventano *sparsi* anche se il loro numero è grande, e le **metriche di distanza euclidee** perdono potere discriminativo (le distanze tendono a concentrarsi).

Conseguenze pratiche:
- I modelli che fanno affidamento su distanze (kNN, kernel) degradano.
- Il numero di campioni necessari per riempire lo spazio cresce in modo proibitivo.
- L'overfitting diventa più probabile perché si possono sempre trovare separatori "casuali".

**Mitigazioni:**
- **Riduzione di dimensionalità** lineare (vedi [[Principal Component Analysis]], [[Singular Value Decomposition]]) o non lineare ([[Multidimensional Scaling]], [[t-SNE]]).
- **Regolarizzazione** ([[Regolarizzazione di Tikhonov]]) per ridurre i gradi di libertà effettivi.
- **Sparsità indotta** (norma $L^1$) per costringere il modello a usare poche feature.

## Collegamenti

- Discusso in: [[Machine Learning]]
- Si lega a tutti i metodi di [[Embedding isometrico|embedding]] e proiezione lineare.

## Fonti

- [[Dispense Machine Learning — Galletti]] (def. 1.2, p. 2)
