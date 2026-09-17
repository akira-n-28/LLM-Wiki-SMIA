---
tipo: concetto
titolo: LSTM
tag: [reti-neurali, deep-learning, sequenze, nlp]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-05
---

# Long Short-Term Memory (LSTM)

Variante della [[Recurrent Neural Network]] che risolve il problema del **vanishing gradient** introducendo una **cell state** $c^{(t)}$ come memoria a lungo termine, controllata da tre gate.

## Motivazione

Nelle RNN vanilla, il gradiente decade esponenzialmente con la distanza temporale: le dipendenze a lungo termine non vengono apprese. L'LSTM separa la memoria in:
- **Hidden state** $h^{(t)}$: memoria a breve termine (output al passo $t$).
- **Cell state** $c^{(t)}$: memoria a lungo termine che scorre con operazioni di somma (non prodotto), mantenendo il gradiente.

## I tre gate

I gate sono funzioni sigmoide ($\in (0,1)$) che modulano il flusso di informazioni: 0 = chiuso, 1 = aperto.

**Forget gate** — cosa dimenticare dalla cell state precedente:
$$f^{(t)} = \sigma(W_f \cdot h^{(t-1)} + U_f \cdot x^{(t)} + b_f)$$

**Input gate** — quanta parte dell'input corrente aggiungere:
$$i^{(t)} = \sigma(W_i \cdot h^{(t-1)} + U_i \cdot x^{(t)} + b_i)$$

**Output gate** — quanta parte della cell state esporre come output:
$$o^{(t)} = \sigma(W_o \cdot h^{(t-1)} + U_o \cdot x^{(t)} + b_o)$$

## Aggiornamento cell state e hidden state

**Candidato cell state:**
$$\tilde{c}^{(t)} = \tanh(W_c \cdot h^{(t-1)} + U_c \cdot x^{(t)} + b_c)$$

**Aggiornamento cell state** (combinazione forget + input):
$$c^{(t)} = f^{(t)} \odot c^{(t-1)} + i^{(t)} \odot \tilde{c}^{(t)}$$

**Hidden state:**
$$h^{(t)} = o^{(t)} \odot \tanh(c^{(t)})$$

## Perché le LSTM mitigano il vanishing gradient

Il cell state si aggiorna via **somma** (non prodotto): se $f^{(t)} \approx 1$, il gradiente fluisce quasi inalterato lungo la "highway" del cell state senza decadimento esponenziale. Questo è fondamentalmente diverso dalle RNN vanilla dove il gradiente passa sempre attraverso $W_{hh}^\ell$.

## Confronto con GRU

| | LSTM | GRU |
|---|---|---|
| Gate | 3 (forget, input, output) | 2 (reset, update) |
| Memoria | Cell state + hidden state | Solo hidden state |
| Parametri | Più | Meno |
| Prestazioni | Spesso migliore su task complessi | Comparabili, più leggera |

## Connessione con i Transformer

Le LSTM sono state la backbone dei modelli NLP prima dei Transformer. BERT e GPT le hanno superate in quasi tutti i benchmark, ma rimangono rilevanti per task su sequenze con risorse limitate.

## Uso pratico

ELMo usa una **biLSTM** (bidirezionale): forward LSTM (sinistra → destra) + backward LSTM (destra → sinistra) per creare embedding contestuali. Precede [[BERT]].

## Collegamenti

- Prerequisito: [[Recurrent Neural Network]]
- Alternativa più leggera: [[GRU]]
- Superate da: [[Transformer]], [[BERT]]
- Applicazione: [[Seq2Seq e Encoder-Decoder]], [[Language Model]]
- Discusso in: [[Informatica per il Machine Learning]] (§12.4, pp. 44-46)

## Fonti

- [[Dispense InfML — Galletti]] (§12.4, pp. 44-46)
