---
tipo: concetto
titolo: Sentiment Analysis
tag: [nlp, classificazione, ml]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-05
---

# Sentiment Analysis

Applicazione del natural language processing per analizzare, estrarre e quantificare l'opinione espressa in un testo. È un task di **classificazione multiclasse**.

## Task

Dato un testo (frase, recensione, post), assegnare una classe di sentimento:
- **Neutral** — 0
- **Positive** — 1
- **Negative** — 2

## Pipeline classica

1. **Rappresentazione testuale:** il testo viene trasformato in un vettore numerico tramite [[Bag of Words e TF-IDF]].
2. **Classificazione:** un modello (es. regressione logistica, SVM, MLP) predice la classe.
3. **Valutazione:** accuracy, precision, recall, F1-score, ROC-AUC (cfr. [[Metriche di classificazione]]).

## Con BERT

BERT (cfr. [[BERT]]) è il modo attuale per fare sentiment analysis ad alte prestazioni. Il task rientra nella categoria *Sequence Classification*: si usa l'embedding del token `[CLS]` come input a un layer fully-connected + softmax.

## Connessione con le RNN

Architetture many-to-one delle [[Recurrent Neural Network]] si prestano naturalmente al task: l'intera sequenza viene compressa in un singolo vettore di stato, usato poi per classificare.

## Metriche

Stesse metriche di classificazione multiclasse: accuracy, F1 macro/micro. Vedi [[Metriche di classificazione]].

## Collegamenti

- Rappresentazione: [[Bag of Words e TF-IDF]]
- Modello BERT: [[BERT]]
- Valutazione: [[Metriche di classificazione]]
- Architettura RNN: [[Recurrent Neural Network]]
- Discusso in: [[Informatica per il Machine Learning]] (§10, p. 35)

## Fonti

- [[Dispense InfML — Galletti]] (§10, p. 35)
