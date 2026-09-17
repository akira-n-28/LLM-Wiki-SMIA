---
tipo: concetto
titolo: Dropout
tag: [reti-neurali, deep-learning, regolarizzazione]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# Dropout

Tecnica di **regolarizzazione** per reti neurali che previene l'overfitting "spegnendo" casualmente alcune unità nascoste durante il training.

## Meccanismo

A ogni passo di training, ogni neurone viene impostato a 0 con probabilità $p$ (tipicamente $p = 0.5$ per layer nascosti, $p = 0.1$–$0.2$ per l'input). Il neurone sopravvissuto viene scalato di $\frac{1}{1-p}$ per mantenere il valore atteso invariato (**inverted dropout**).

## Effetto: prevenire il co-adattamento

Senza dropout, i neuroni possono diventare **co-dipendenti**: un neurone si fida troppo di un altro e smette di imparare rappresentazioni indipendenti. Il dropout forza ogni neurone a sviluppare feature utili *da solo*, migliorando la generalizzazione.

## Interpretazione ensemble

Ogni configurazione di neuroni sopravvissuti definisce una sotto-rete diversa. Il training con dropout equivale ad allenare un ensemble esponenzialmente grande di sotto-reti condividendo i pesi — a inferenza, l'intera rete (senza dropout) approssima la media dell'ensemble.

## Dropout vs Batch Normalization

Nelle architetture moderne (ResNet, Transformer) il dropout è spesso sostituito o affiancato dalla **Batch Normalization** (non trattata in dettaglio in queste dispense). Le due tecniche sono complementari: BN normalizza le attivazioni, dropout le azzera stocasticamente.

## Dove si usa

- **Layer fully-connected** (MLP): probabilità 0.5 (AlexNet, VGGNet)
- **Layer convoluzionali**: meno comune (le CNN hanno già meno parametri per unità)
- **Transformer**: usato tra i sub-layer (attention, FFN)

## Connessione con AlexNet

Il dropout è stato reso popolare da **AlexNet** (2012) come tecnica per addestrare reti molto profonde senza overfittare (vedi [[Convolutional Neural Network]]).

## Collegamenti

- Regolarizzazione parametrica: [[Regolarizzazione di Tikhonov]]
- Applicato in: [[Multi-Layer Perceptron]], [[Convolutional Neural Network]], [[Transformer]]
- Problema che risolve: [[Overfitting e underfitting]]
- Discusso in: [[Informatica per il Machine Learning]] (§9, p. 35)

## Fonti

- [[Dispense InfML — Galletti]] (§9, p. 35)
