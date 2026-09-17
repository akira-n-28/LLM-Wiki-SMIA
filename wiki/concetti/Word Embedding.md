---
tipo: concetto
titolo: Word Embedding
tag: [nlp, rappresentazione, ml]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-05
---

# Word Embedding

Rappresentazione densa di parole in uno spazio vettoriale di dimensione ridotta $d$ (es. $d = 300$), tale che parole semanticamente simili abbiano vettori geometricamente vicini.

Superano i limiti del [[Bag of Words e TF-IDF|One-Hot Encoding]]: altissima dimensionalità ($|V|$) e mancanza di nozione di similarità (tutti i vettori sono ortogonali).

## Word2Vec

Famiglia di algoritmi efficienti per apprendere embedding. Il problema del calcolo della softmax sull'intero vocabolario ($O(|V|)$) viene aggirato con il **Negative Sampling** (o Noise Contrastive Estimation): il modello impara a distinguere coppie (parola, contesto) reali da coppie "rumore" generate casualmente.

### CBOW (Continuous Bag of Words)

Predice la **parola target** dalla media delle parole di contesto nella finestra temporale.

$$\max \frac{1}{T} \sum_{t=1}^T \log P(w_t | w_{t-m}, \ldots, w_{t-1}, w_{t+1}, \ldots, w_{t+m})$$

- L'ordine delle parole di contesto non conta (da cui "Bag of Words").
- Più veloce; funziona bene per parole frequenti.

### Skip-Gram

Fa l'opposto: data la **parola target centrale** $w_t$, predice le parole di contesto.

$$\max \frac{1}{T} \sum_{t=1}^T \sum_{\substack{-m \le j \le m \\ j \ne 0}} \log P(w_{t+j} | w_t)$$

La probabilità è modellata con softmax:
$$P(w_\text{out} | w_\text{in}) = \frac{\exp(u_\text{out}^\top v_\text{in})}{\sum_{w \in V} \exp(u_w^\top v_\text{in})}$$

- Funziona meglio con dataset piccoli e per parole rare.
- Più costoso computazionalmente.

## Proprietà degli Embedding

### Analogie vettoriali

Le relazioni semantiche corrispondono a direzioni costanti nello spazio:
$$v_\text{King} - v_\text{Man} + v_\text{Woman} \approx v_\text{Queen}$$
$$v_\text{Paris} - v_\text{France} + v_\text{Italy} \approx v_\text{Rome}$$

### Valutazione

- **Intrinsic:** task di analogie o similarità in isolamento. Veloce ma non garantisce prestazioni downstream.
- **Extrinsic:** valutazione su task reali (es. Machine Translation). Più affidabile ma costoso.

## Limiti di Word2Vec

Assegna un unico vettore per parola indipendentemente dal contesto. Parole polisemiche (es. "banco") ricevono la stessa rappresentazione in tutti i contesti.

Soluzione: **embedding contestuali** (ELMo, poi [[BERT]]) dove la rappresentazione dipende dalla frase completa.

## Connessione con i sistemi di raccomandazione

L'idea di imparare embedding latenti di parole dal contesto co-occorrente è la stessa usata nei [[Sistemi di raccomandazione]] per utenti e oggetti (matrix factorization). Vedi anche [[Singular Value Decomposition]].

## Connessione con le RNN

Le RNN (cfr. [[Recurrent Neural Network]]) usano una matrice di embedding $\Phi$ per trasformare one-hot token in vettori densi $x_t = \Phi w_t$ come primo passo del processing.

## Collegamenti

- Supera: [[Bag of Words e TF-IDF]]
- Usato da: [[Recurrent Neural Network]], [[Language Model]]
- Embedding contestuali: [[BERT]]
- Stessa idea: [[Sistemi di raccomandazione]]
- Discusso in: [[Informatica per il Machine Learning]] (§11.3, pp. 40-42)

## Fonti

- [[Dispense InfML — Galletti]] (§11.3, pp. 40-42)
