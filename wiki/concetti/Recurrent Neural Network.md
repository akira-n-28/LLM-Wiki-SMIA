---
tipo: concetto
titolo: Recurrent Neural Network
tag: [reti-neurali, deep-learning, sequenze, nlp]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-05
---

# Recurrent Neural Network (RNN)

Architettura neurale per **sequenze** $x_1, x_2, \ldots, x_T$. La caratteristica chiave è il **parameter sharing**: gli stessi pesi vengono usati a ogni passo temporale, consentendo di gestire sequenze di lunghezza variabile e di generalizzare pattern appresi in una posizione anche ad altre.

## Equazioni di una RNN Vanilla

Ad ogni passo $t$:

$$x_t = \Phi w_t \quad \text{(embedding lookup)}$$
$$h_t = \tanh(W_{hh} h_{t-1} + W_{xh} x_t) \quad \text{(aggiornamento stato)}$$
$$y_t = W_{hy} h_t \quad \text{(predizione/logits)}$$

dove $h_t \in \mathbb{R}^k$ è l'**hidden state** (memoria della rete), $\Phi \in \mathbb{R}^{d \times |V|}$ la matrice di embedding, e $W_{hh}, W_{xh}, W_{hy}$ pesi condivisi per tutti i time step.

### Formulazione dinamica

$$h^{\langle t \rangle} = f_W(h^{\langle t-1 \rangle}, x^{\langle t \rangle})$$

Per una sequenza di lunghezza $\tau$, questa ricorrenza viene "srotolata" (**unfolding**) $\tau-1$ volte, creando un grafo computazionale profondo.

## Efficienza dei parametri

Rispetto a un MLP su one-hot encoding ($\approx |V|^2$ parametri), una RNN richiede:
$$\text{Params} \approx d|V| + dk + k^2 + k|V|$$

Con valori realistici ($|V| = 10^5$, $d = k = 100$): da $\approx 10^{11}$ a $\approx 10^7$ parametri.

## Addestramento: BPTT

L'addestramento usa la **Backpropagation Through Time (BPTT)**: la rete è srotolata nel tempo e la backpropagation viene applicata sull'intera sequenza. Poiché i pesi sono condivisi, il gradiente è la somma dei contributi di ogni step:

$$\frac{\partial L}{\partial W_{hh}} = \sum_{t=1}^T \frac{\partial L^{\langle t \rangle}}{\partial W_{hh}}$$

**Truncated BPTT:** per sequenze molto lunghe, la retropropagazione viene limitata a $s$ step. Riduce il costo computazionale e mitiga l'instabilità dei gradienti.

## Vanishing e Exploding Gradient

Il gradiente di $L^{\langle i \rangle}$ rispetto a $h^{\langle j \rangle}$ (distanza $\ell = i - j$) contiene la potenza $W_{hh}^\ell$:

- **Vanishing** ($|\lambda| < 1$): il gradiente decade esponenzialmente → difficoltà ad apprendere dipendenze a lungo termine.
- **Exploding** ($|\lambda| > 1$): il gradiente cresce esponenzialmente → instabilità numerica.

Soluzione: architetture con gate ([[LSTM]], [[GRU]]).

## Tipologie di architettura

| Tipo | Descrizione | Esempio |
|---|---|---|
| Many-to-one | Sequenza → singolo output | Sentiment analysis |
| One-to-many | Singolo input → sequenza | Image captioning |
| Many-to-many (sync) | Sequenza → sequenza allineata | POS tagging |
| Many-to-many (async) | Sequenza → sequenza diversa | Traduzione (Seq2Seq) |

## Connessione con il Language Modeling

Le RNN sono la prima architettura neurale proposta per i [[Language Model]]: alla ogni passo $t$, $y_t = \text{softmax}(W_{hy} h_t)$ predice la probabilità delle parole nel vocabolario.

## Limitazione: information bottleneck

Nei modelli [[Seq2Seq e Encoder-Decoder]], l'encoder RNN comprime l'intera sequenza in un singolo vettore di dimensione fissa. Per sequenze lunghe, questo crea un collo di bottiglia. Soluzione: [[Meccanismo di Attention]].

## Collegamenti

- Versioni con gate: [[LSTM]], [[GRU]]
- Architettura seq2seq: [[Seq2Seq e Encoder-Decoder]]
- Attention: [[Meccanismo di Attention]]
- Embedding: [[Word Embedding]]
- Language modeling: [[Language Model]]
- Discusso in: [[Informatica per il Machine Learning]] (§12, pp. 43-49)

## Fonti

- [[Dispense InfML — Galletti]] (§12, pp. 43-49)
