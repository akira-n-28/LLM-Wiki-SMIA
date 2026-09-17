---
tipo: concetto
titolo: BERT
tag: [reti-neurali, deep-learning, nlp, transformer, pre-training]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-05
---

# BERT

**Bidirectional Encoder Representations from Transformers.** Modello basato sull'encoder del [[Transformer]], pre-addestrato su enormi corpus non etichettati con obiettivi self-supervised. Rappresenta il passaggio al paradigma **pre-train → fine-tune** in NLP.

## Bidirectionalità

A differenza di GPT (unidirezionale, left-to-right) ed ELMo (bidirezionale ma concatenando due LM indipendenti), BERT è **profondamente bidirezionale**: ogni token vede contemporaneamente il contesto a sinistra e a destra in ogni layer.

## Pre-training

### Masked Language Model (MLM)

Il problema delle predizioni bidirezionali naïve: i layer superiori potrebbero "vedere" la parola target stessa. BERT risolve con il **masking**:

- Il **15%** dei token viene scelto casualmente.
- Di questi: sostituiti con `[MASK]` (80%), con un token casuale (10%), lasciati invariati (10%).
- L'obiettivo: predire i token originali basandosi sul contesto.

La variazione al 10% evita che il modello impari a ignorare completamente i token non-MASK durante il fine-tuning.

### Next Sentence Prediction (NSP)

Addestramento a capire relazioni tra frasi:

- Input: coppia di frasi $(A, B)$.
- 50%: $B$ è la frase che segue effettivamente $A$.
- 50%: $B$ è una frase casuale.
- Obiettivo: predire se $B$ segue $A$.

Utile per task come Question Answering e Natural Language Inference.

## Fine-tuning

Il modello pre-addestrato viene adattato a task supervisionati aggiungendo un layer di output minimale e aggiornando tutti i parametri. Token speciali:
- `[CLS]`: inserito all'inizio; il suo embedding rappresenta l'intera sequenza.
- `[SEP]`: separa frasi diverse.
- Segment embeddings: distinguono la frase A dalla frase B.

### Applicazioni principali

**Sequence Classification** (es. [[Sentiment Analysis]]): embedding di `[CLS]` → layer FC + softmax.

**Named Entity Recognition (NER)**: embedding di ogni token → classificatore condiviso.

**Natural Language Inference (NLI)**: due frasi separate da `[SEP]` → embedding di `[CLS]` → predizione della relazione logica (implicazione, contraddizione, neutro).

**Grounded Common Sense Inference**: 4 sequenze (frase + ciascuna continuazione) → score tramite `[CLS]` → softmax per scegliere la continuazione migliore.

## Perché funziona

Il pre-training su corpora massicci permette a BERT di apprendere:
- Feature sintattiche (layer bassi).
- Feature semantiche e contestuali (layer alti).
- Relazioni tra frasi (NSP).

Il fine-tuning adatta queste rappresentazioni generali a task specifici con pochissimi dati etichettati.

## Confronto con Word2Vec/ELMo

| Modello | Bidirezionale | Contestuale | Pre-training |
|---|---|---|---|
| [[Word Embedding|Word2Vec]] | No | No | Sì (task-specifico) |
| ELMo | Sì (concatenato) | Sì | Sì (biLSTM) |
| BERT | Sì (profondo) | Sì | Sì (Transformer) |

## Connessioni

BERT usa le connessioni residue e la Layer Normalization del [[Transformer]]. L'idea di embedding contestuali viene da ELMo (cfr. [[Language Model]]).

## Varianti

- **BERT-Base:** 12 layer, 768 hidden, 12 head, 110M parametri.
- **BERT-Large:** 24 layer, 1024 hidden, 16 head, 340M parametri.
- Successori: RoBERTa (più dati, no NSP), DistilBERT (distillato), ALBERT, DeBERTa.

## Connessione con il Transformer Decoder

BERT usa solo l'**encoder** del Transformer. I modelli generativi come GPT usano solo il **decoder** (con masked attention). I modelli encoder-decoder completi (T5, BART) combinano entrambi.

## Collegamenti

- Architettura: [[Transformer]]
- Meccanismo centrale: [[Meccanismo di Attention]]
- Embedding contestuali: [[Language Model]] (ELMo)
- Fine-tuning applicato: [[Sentiment Analysis]]
- Discusso in: [[Informatica per il Machine Learning]] (§13.9, pp. 54-55)

## Fonti

- [[Dispense InfML — Galletti]] (§13.9, pp. 54-55)
