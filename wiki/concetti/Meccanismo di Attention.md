---
tipo: concetto
titolo: Meccanismo di Attention
tag: [reti-neurali, deep-learning, nlp, transformer]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-05
---

# Meccanismo di Attention

Estensione dell'architettura [[Seq2Seq e Encoder-Decoder]] che risolve l'**information bottleneck**: invece di un unico context vector fisso, il decoder può "guardare" direttamente tutti gli hidden state dell'encoder, pesandoli dinamicamente a ogni step di decodifica.

## Problema

I modelli Seq2Seq classici comprimono l'intera sequenza di input in un singolo context vector di dimensione fissa. Per sequenze lunghe il modello tende a dimenticare le prime parti dell'input.

## Encoder Bidirezionale

L'encoder usa una [[Recurrent Neural Network]] bidirezionale che produce per ogni posizione $i$:
- $\overrightarrow{h}_i$: forward (sinistra → destra)
- $\overleftarrow{h}_i$: backward (destra → sinistra)

Rappresentazione finale: $h_i = [\overrightarrow{h}_i^\top; \overleftarrow{h}_i^\top]^\top$ — cattura il contesto sia precedente che successivo.

## Context Vector Dinamico

Invece di un unico context vector, l'attention calcola un context vector diverso $c_t$ per ogni output $y_t$:

$$c_t = \sum_{i=1}^n \alpha_{t,i} h_i$$

dove $\alpha_{t,i}$ sono i **pesi di attenzione** (alignment weights).

## Calcolo dei Pesi di Attenzione

I pesi $\alpha_{t,i}$ sono calcolati tramite softmax su uno **alignment score**:

$$\alpha_{t,i} = \frac{\exp(\text{score}(s_{t-1}, h_i))}{\sum_{i'=1}^n \exp(\text{score}(s_{t-1}, h_{i'}))}$$

dove $s_{t-1}$ è lo stato del decoder al passo precedente.

### Additive Attention (Bahdanau, 2015)

$$\text{score}(s_{t-1}, h_i) = v^\top \tanh(W_s s_{t-1} + W_h h_i)$$

dove $v, W_s, W_h$ sono parametri appresi. Misura la compatibilità additiva tra decoder e encoder.

## Decoder con Attention

Lo stato del decoder dipende ora dal context vector dinamico:
$$s_t = f(s_{t-1}, y_{t-1}, c_t)$$

I pesi $\alpha_{t,i}$ possono essere visualizzati come una "mappa di attenzione" che mostra quali parole dell'input influenzano ogni parola dell'output.

## Self-Attention (Intra-Attention)

Nella **self-attention** query, key e value provengono dalla **stessa sequenza**. Per ogni posizione si calcola la similarità con tutte le altre posizioni e si usa il risultato per pesare le informazioni.

### Scaled Dot-Product Attention

Formulazione usata nei [[Transformer]]:

$$\text{Attention}(Q, K, V) = \text{softmax}\left(\frac{QK^\top}{\sqrt{d_k}}\right) V$$

- **Query (Q):** "cosa sto cercando?"
- **Key (K):** "cosa contiene ogni posizione?"
- **Value (V):** "quale informazione restituire?"

La divisione per $\sqrt{d_k}$ previene che i dot-product diventino troppo grandi, causando gradienti piccoli dopo la softmax.

## Differenza tra Attention e Self-Attention

| | Attention (Bahdanau) | Self-Attention |
|---|---|---|
| Query | Stato del decoder | Ogni posizione della sequenza |
| Key/Value | Hidden state encoder | Stessa sequenza |
| Uso | Encoder-Decoder | Transformer, BERT |

## Connessione con il Transformer

Il [[Transformer]] estende la self-attention in tre modi:
1. **Multi-Head Attention**: più teste parallele, ognuna che cattura relazioni diverse.
2. **Positional Encoding**: poiché non c'è ricorrenza, l'ordine viene aggiunto esplicitamente.
3. **Parallelizzazione completa**: a differenza delle RNN, il calcolo può essere parallelizzato.

## Importanza storica

L'attention (Bahdanau et al., 2015) è stata la svolta che ha dimostrato che l'allineamento dinamico tra sorgente e target poteva migliorare drasticamente la traduzione automatica. Ha direttamente portato al design del Transformer (2017).

## Connessione con i Sistemi di Raccomandazione

I pesi di attenzione $\alpha_{t,i}$ sono concettualmente simili ai pesi di similarità nei [[Sistemi di raccomandazione]]: entrambi misurano quanto una query sia "compatibile" con un insieme di elementi.

## Collegamenti

- Prerequisito: [[Seq2Seq e Encoder-Decoder]], [[Recurrent Neural Network]]
- Basato su: [[Softmax]]
- Esteso in: [[Transformer]], [[BERT]]
- Discusso in: [[Informatica per il Machine Learning]] (§13, pp. 50-55)

## Fonti

- [[Dispense InfML — Galletti]] (§13, pp. 50-55)
