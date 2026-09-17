---
tipo: concetto
titolo: Seq2Seq e Encoder-Decoder
tag: [reti-neurali, deep-learning, sequenze, nlp]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-05
---

# Seq2Seq e Architettura Encoder-Decoder

Paradigma per task di trasformazione sequenza → sequenza con lunghezze diverse tra input e output (es. traduzione automatica, riassunto).

## Tipologie di RNN per sequenze

| Tipo | Input | Output | Esempio |
|---|---|---|---|
| Many-to-one | Sequenza | Singolo | Sentiment analysis |
| One-to-many | Singolo | Sequenza | Image captioning |
| Many-to-many (sync) | Sequenza | Sequenza allineata | POS tagging |
| Many-to-many (async) | Sequenza | Sequenza diversa | Traduzione |

## Architettura Encoder-Decoder

Per il many-to-many asincrono si separa il modello in due componenti:

**Encoder:** processa la sequenza di input $(x_0, x_1, \ldots, x_n)$ tramite una [[Recurrent Neural Network]] (o [[LSTM]], [[GRU]]) e la comprime in un **context vector** (feature vector) di dimensione fissa.

**Decoder:** a partire dal context vector, genera la sequenza di output $(y_0, y_1, \ldots, y_m)$ in modo **autoregressivo** — un elemento alla volta, condizionando ogni predizione sugli elementi già generati.

Sia encoder che decoder possono essere composti da più layer impilati (stacked), aumentando la capacità rappresentativa.

## Modello autoregressivo

La probabilità della sequenza di output viene fattorizzata come:

$$P(x_1, \ldots, x_T) = \prod_{t=1}^T P(x_t | x_1, \ldots, x_{t-1})$$

### Teacher Forcing

Durante il **training**: l'input per lo step successivo del decoder è il **ground truth** (token corretto), non l'output generato. Accelera la convergenza e stabilizza l'addestramento.

Durante l'**inferenza**: il decoder usa i propri output precedenti (autoregressivo puro). Questo crea **exposure bias**: errori nei primi step si propagano amplificandosi.

Compromesso: durante il training, usare il ground truth con probabilità $p$ e l'output del modello con probabilità $1-p$.

## Information Bottleneck

Comprimere un'intera sequenza in un singolo vettore di dimensione fissa è un **collo di bottiglia**: per sequenze lunghe, il context vector non riesce a catturare tutti i dettagli rilevanti dell'input. Questo ha motivato il [[Meccanismo di Attention]].

## Connessione con il Transformer

Il [[Transformer]] adotta la stessa struttura encoder-decoder ma elimina la ricorrenza, usando solo self-attention. Questo risolve il bottleneck in modo più scalabile.

## Connessione con U-Net e CNN per segmentazione

L'architettura encoder-decoder viene usata anche nelle CNN per la **semantic segmentation** (cfr. [[Convolutional Neural Network]]): l'encoder comprime la rappresentazione spaziale, il decoder la espande — ma con skip connections tra livelli corrispondenti (U-Net).

## Applicazioni principali

- Traduzione automatica (Neural Machine Translation)
- Riassunto automatico
- Speech-to-text
- Image captioning

## Limitazioni delle RNN Seq2Seq

- Information bottleneck nel context vector.
- Training sequenziale (non parallelizzabile).
- Difficoltà con dipendenze a lungo termine (anche con LSTM/GRU).

→ Superate dal [[Transformer]] (2017).

## Collegamenti

- Componenti: [[Recurrent Neural Network]], [[LSTM]], [[GRU]]
- Soluzione al bottleneck: [[Meccanismo di Attention]]
- Architettura senza ricorrenza: [[Transformer]]
- Discusso in: [[Informatica per il Machine Learning]] (§12.6-12.7, pp. 48-49)

## Fonti

- [[Dispense InfML — Galletti]] (§12.6-12.7, pp. 48-49)
