---
tipo: concetto
titolo: GRU
tag: [reti-neurali, deep-learning, sequenze, nlp]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-05
---

# Gated Recurrent Unit (GRU)

Alternativa più semplice alla [[LSTM]]: elimina la **cell state** separata e usa solo due gate invece di tre, mantenendo prestazioni comparabili con meno parametri.

## Struttura

La GRU mantiene un unico **hidden state** $h^{(t)}$ per ogni passo temporale.

**Reset gate** — quanta parte dell'hidden state precedente usare per calcolare il candidato:
$$r^{(t)} = \sigma(W_r \cdot h^{(t-1)} + U_r \cdot x^{(t)} + b_r)$$

**Update gate** — quanto dell'hidden state aggiornare vs. mantenere:
$$u^{(t)} = \sigma(W_u \cdot h^{(t-1)} + U_u \cdot x^{(t)} + b_u)$$

**Candidato hidden state:**
$$\tilde{h}^{(t)} = \tanh\left(W_r \cdot (r^{(t)} \odot h^{(t-1)}) + U_h \cdot x^{(t)} + b_h\right)$$

**Hidden state finale** (l'update gate controlla simultaneamente cosa mantenere e cosa aggiornare):
$$h^{(t)} = (1 - u^{(t)}) \odot h^{(t-1)} + u^{(t)} \odot \tilde{h}^{(t)}$$

- $u^{(t)} \approx 0$: lo stato precedente viene preservato (dipendenze a lungo termine).
- $u^{(t)} \approx 1$: lo stato viene aggiornato con il candidato.

## GRU vs LSTM

| | GRU | LSTM |
|---|---|---|
| Gate | 2 (reset, update) | 3 (forget, input, output) |
| Stato | Solo hidden state | Cell state + hidden state |
| Parametri | Meno (~25% in meno) | Più |
| Velocità di training | Più veloce | Più lenta |
| Prestazioni | Comparabili | Spesso marginalmente migliore |

In pratica la scelta dipende dal task e dalle risorse computazionali disponibili. Le GRU sono preferite quando si vuole un modello più leggero senza perdita significativa di qualità.

## Connessione con l'update gate come interpolazione

L'aggiornamento dell'hidden state è un'**interpolazione lineare** tra lo stato precedente e il candidato, pesata dall'update gate. Questo è concettualmente simile alle skip connection di [[Residual Connection]], ma appreso dinamicamente a ogni step.

## Connessione con vanishing gradient

Come le [[LSTM]], le GRU mitigano il vanishing gradient tramite la struttura additiva: quando $u^{(t)} \approx 0$ il gradiente fluisce attraverso $(1 - u^{(t)}) \odot h^{(t-1)}$ quasi inalterato.

## Connessione con Seq2Seq

Sia le LSTM che le GRU vengono usate come encoder e decoder nei modelli [[Seq2Seq e Encoder-Decoder]].

## Collegamenti

- Prerequisito: [[Recurrent Neural Network]]
- Alternativa più espressiva: [[LSTM]]
- Applicazione: [[Seq2Seq e Encoder-Decoder]]
- Discusso in: [[Informatica per il Machine Learning]] (§12.5, pp. 46-48)

## Fonti

- [[Dispense InfML — Galletti]] (§12.5, pp. 46-48)
