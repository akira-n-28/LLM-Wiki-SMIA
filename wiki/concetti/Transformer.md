---
tipo: concetto
titolo: Transformer
tag: [reti-neurali, deep-learning, nlp, attention]
cluster: ml
fonti: 2
ultima-modifica: 2026-05-05
---

# Transformer

Architettura seq2seq (Vaswani et al., 2017) che elimina completamente le [[Recurrent Neural Network]], basandosi esclusivamente su meccanismi di [[Meccanismo di Attention|attention]]. Ha ridefinito lo stato dell'arte in NLP e successivamente in computer vision.

## Caratteristiche principali

- **Self-attention:** cattura dipendenze a qualsiasi distanza in tempo costante (vs. lineare per RNN).
- **Multi-Head Attention:** più "teste" in parallelo, ognuna che cattura relazioni diverse.
- **Positional Encoding:** l'ordine viene aggiunto esplicitamente agli embedding (nessuna ricorrenza).
- **Parallelizzazione completa:** il training può essere parallelizzato sull'intera sequenza.

## Multi-Head Attention

Esegue la scaled dot-product attention $h$ volte in parallelo su sottospazi diversi:

$$\text{MultiHead}(Q, K, V) = \text{Concat}(\text{head}_1, \ldots, \text{head}_h) W^O$$

$$\text{head}_i = \text{Attention}(QW^Q_i, KW^K_i, VW^V_i)$$

Ogni testa si specializza su tipi diversi di relazioni (sintassi, semantica a lungo raggio, ecc.). Con una singola testa la media pesata potrebbe "appiattire" informazioni diverse.

## Architettura Encoder-Decoder

### Encoder

Stack di $N = 6$ layer identici. Ogni layer ha due sotto-strati:
1. **Multi-Head Self-Attention:** ogni posizione può attendere a tutte le altre.
2. **Position-wise Feed-Forward Network:** rete fully-connected applicata indipendentemente a ogni posizione.

Ogni sotto-strato usa una **connessione residua** seguita da **Layer Normalization**:
$$\text{LayerNorm}(x + \text{Sublayer}(x))$$

Dimensione output di ogni sotto-strato: $d_\text{model} = 512$.

### Decoder

Stack di $N = 6$ layer con tre sotto-strati:
1. **Masked Multi-Head Self-Attention:** impedisce di attendere a posizioni future (causalità).
2. **Multi-Head Cross-Attention:** Query dal decoder, Key e Value dall'encoder.
3. **Position-wise Feed-Forward Network.**

### Positional Encoding

Poiché non c'è ricorrenza, l'informazione posizionale viene sommata agli embedding di input. La codifica posizionale usa funzioni sinusoidali a diverse frequenze, permettendo al modello di generalizzare a sequenze più lunghe di quelle viste in training.

### Output

L'output finale passa per un layer lineare e una [[Softmax]] per generare le probabilità dei token successivi.

## Connessioni residue e Layer Norm

Le connessioni residue (identiche alle [[Residual Connection]] di ResNet) permettono al gradiente di fluire direttamente attraverso i layer, facilitando il training di reti profonde. La Layer Normalization normalizza le attivazioni all'interno di ogni esempio (diversa dalla Batch Normalization).

## Complessità computazionale

| Modello | Complessità per layer | Dipendenze sequenziali |
|---|---|---|
| RNN | $O(n \cdot d^2)$ | $O(n)$ |
| Transformer | $O(n^2 \cdot d)$ | $O(1)$ |

Il Transformer è quadratico nella lunghezza della sequenza $n$ ma parallelo. Per $n$ piccoli è molto più veloce del training sequenziale delle RNN.

## Applicazioni

Il Transformer è la base di tutti i modelli NLP moderni: [[BERT]] (encoder-only), GPT (decoder-only), T5 (encoder-decoder). Ha anche trovato applicazione in computer vision (Vision Transformer, ViT).

## Connessione con la CNN

Sia il Transformer che le [[Convolutional Neural Network]] usano **parameter sharing** e **connessioni locali** (le CNN nello spazio, il Transformer tramite la finestra di attenzione). Le connessioni residue sono condivise da entrambe le architetture (cfr. [[Residual Connection]]).

## Importanza storica

"Attention Is All You Need" (Vaswani et al., 2017) ha dimostrato che si possono raggiungere risultati migliori delle LSTM su Machine Translation eliminando completamente la ricorrenza. Da allora il Transformer è diventato l'architettura dominante in NLP.

## Collegamenti

- Meccanismo centrale: [[Meccanismo di Attention]]
- Prerequisito: [[Seq2Seq e Encoder-Decoder]]
- Modello pre-addestrato: [[BERT]]
- Connessioni residue: [[Residual Connection]]
- Discusso in: [[Informatica per il Machine Learning]] (§13.6-13.8, pp. 52-54)

## Fonti

- [[Dispense InfML — Galletti]] (§13.6-13.8, pp. 52-54)
