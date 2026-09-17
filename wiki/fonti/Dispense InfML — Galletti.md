---
tipo: fonte
titolo: Dispense InfML — Galletti
autori: [Marco Galletti]
corso: Informatica per il Machine Learning
docente: Fabrizio Silvestri
anno-accademico: 2025/2026
data-pubblicazione: 2025
data-ingest: 2026-05-04
file-raw: raw/appunti/inf_ml.pdf
pagine: 68
ultima-modifica: 2026-05-04
tag: [ml, nlp, reti-neurali, deep-learning, dispense, galletti]
---

# Dispense di Applicazioni Informatiche del Machine Learning — Galletti

Riassunto del corso di **Informatica per il Machine Learning** del prof. **Fabrizio Silvestri** (A.A. 2025/2026, SMIA Sapienza), redatto da **Marco Galletti** in 68 pagine. La dispensa più lunga e completa del corpus: copre tutto il ciclo supervised learning, ensemble, NLP, reti ricorrenti, Transformer e CNN.

**Riferimento file raw:** `raw/appunti/inf_ml.pdf`

## Riassunto in 5 punti

1. **Fondamenti probabilistici del supervised learning** (§1–4). Ogni loss è la NLL di una distribuzione scelta: Gaussiana → MSE, Bernoulli → BCE, Categorica → cross-entropy multiclasse. La regressione lineare viene estesa con Ridge (L2), Lasso (L1) e Elastic Net. La logistica introduce l'odds-ratio e la derivazione via regola della catena.

2. **Ensemble e valutazione** (§5–7). Metriche di classificazione (accuracy, precision, recall, F1, ROC-AUC) e di ranking (Precision@k, MRR, MAP, [[Metriche di ranking]]). Bagging, [[Random Forest]] con Extra-Trees, [[Gradient Boosting]] esteso al [[Learning to Rank]] (RankNet, LambdaRank). [[Sistemi di raccomandazione]] via matrix factorization.

3. **Reti neurali e training** (§8–9). Shallow vs deep NN con notazione matriciale, teorema di approssimazione universale (versione ReLU: rete con D unità produce funzione piecewise-lineare con D+1 regioni). Dropout come tecnica anti-overfitting. Backpropagation dettagliata layer-by-layer con forward/backward pass.

4. **NLP: dal bag-of-words ai word embedding** (§10–11). Sentiment analysis, TF-IDF, feature hashing. Language models statistici (N-gram, smoothing). Word2Vec (CBOW e Skip-Gram) come classificazione binaria via Negative Sampling. Embeddings semantici: analogie vettoriali (King − Man + Woman ≈ Queen).

5. **Architetture sequenziali e visione** (§12–14). RNN vanilla con BPTT e problema vanishing/exploding gradient. LSTM (3 gate: forget, input, output) e GRU (2 gate) come soluzioni. Seq2Seq encoder-decoder con attention (Bahdanau, self-attention), Transformer, BERT. CNN: convoluzione, AlexNet, VGG, ResNet (skip connections), semantic segmentation (Hourglass, U-Net).

## Citazioni notevoli

> "Minimizzare la cross-entropy equivale a massimizzare la verosimiglianza del modello." (p. 7)

> "Un ensemble di 5 classificatori con accuratezza 75% ciascuno ha probabilità ~89% di votare correttamente." (p. 19)

> "Backpropagation: efficiente perché riutilizza i valori del forward pass. Complessità O(K) dove K è il numero di layer." (p. 34)

> "Skip connections: se i layer aggiuntivi non sono utili, è più facile apprendere F(x) ≈ 0 che H(x) = x." (p. 64)

## Contraddizioni rilevate

- **Nessuna contraddizione** con le dispense di ML (Rodolà): i due corsi usano notazioni coerenti. InfML approfondisce dal lato applicativo/NLP/visione ciò che ML trattava dal lato matematico-strutturale.
- Piccola incoerenza di notazione: ML usa $\Theta$ per i parametri, InfML usa $\theta$ e $w$ in contesti diversi — non è una contraddizione concettuale.

## Ganci per ingest futuri

- **[[Modelli Matematici per la Fisica II]]** (Zamponi): toccherà energia/entropia di Hopfield, che si collega ai word embedding e alle reti recurrent.
- **[[Algebra Lineare]]** (Malvenuto): l'algebra del Transformer (proiezioni Q/K/V, multi-head) si approfondisce con la teoria degli spazi vettoriali.

## Pagine create da questa ingest

**Concetti nuovi (20):**
[[Softmax]], [[Metriche di classificazione]], [[Metriche di ranking]], [[Learning to Rank]], [[Sistemi di raccomandazione]], [[Dropout]], [[Bag of Words e TF-IDF]], [[Language Model]], [[Word Embedding]], [[Recurrent Neural Network]], [[LSTM]], [[GRU]], [[Seq2Seq e Encoder-Decoder]], [[Meccanismo di Attention]], [[Transformer]], [[BERT]], [[Convolutional Neural Network]], [[Residual Connection]], [[Lasso e Elastic Net]], [[Sentiment Analysis]]

**Aggiornati:**
[[Regressione lineare]] (Lasso/Elastic Net), [[Decision Tree]] (algoritmo LEARN, entropia/info gain), [[Gradient Boosting]] (Learning to Rank), [[Stima di Massima Verosimiglianza]] (derivazione NLL→cross-entropy), [[Regolarizzazione di Tikhonov]] (Ridge nel contesto L2 vs L1)

**Persone (1):** [[Silvestri, Fabrizio]]
