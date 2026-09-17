---
tipo: moc
titolo: MOC — Machine Learning
cluster: ml
ultima-modifica: 2026-05-06
---

# MOC — Machine Learning

**Map of Content** del cluster `ml` (59 concetti). Pagina di **navigazione tematica** per studio: i concetti sono raggruppati per percorso pedagogico, non in ordine alfabetico. Per la versione live e le metriche vai su [[dashboard]].

> **Corsi coinvolti:** [[Machine Learning]] (Rodolà, A.A. 24/25), [[Informatica per il Machine Learning]] (Silvestri, A.A. 25/26), [[Matematica per il Machine Learning]] (Agliari, A.A. 25/26).

---

## 🎯 Da dove iniziare

Se è la prima volta che vedi ML, segui quest'ordine:

1. [[Apprendimento statistico]] — il framework
2. [[Funzione di perdita]] — cosa minimizziamo
3. [[Rischio teorico]] e [[Rischio empirico]] — la quantità di interesse
4. [[ERM]] — Empirical Risk Minimization
5. [[Bias-Variance trade-off]] — il dilemma centrale
6. [[Overfitting e underfitting]] — cosa va storto
7. [[Cross-validation]] — come scegliere

## 📐 Modelli lineari

**Regressioni:**
- [[Regressione lineare]] → [[Regressione polinomiale]] → [[Regressione logistica]]
- Strumenti: [[Minimi quadrati]], [[Funzione sigmoide]]

**Probabilistico:**
- [[Modello lineare normale]]
- [[Stima di Massima Verosimiglianza|MLE]] → [[Stima MAP]]
- [[Distribuzioni coniugate]]

**Loss:**
- [[Cross-entropy]] (classificazione) — [[Softmax]]
- MSE / Minimi quadrati (regressione)

## 🧠 Reti neurali profonde

**Teoria base:**
- [[Multi-Layer Perceptron]] — l'architettura
- [[Teorema di approssimazione universale]] — espressività
- [[Backpropagation]] + [[Grafo computazionale]] — addestramento

**Architetture per dati strutturati:**
- *Sequenze:* [[Recurrent Neural Network]] → [[LSTM]] → [[GRU]] → [[Transformer]]
- *Immagini:* [[Convolutional Neural Network]] → [[Residual Connection]] (ResNet)
- *Linguaggio:* [[Word Embedding]] → [[BERT]]
- *Encoder-decoder:* [[Seq2Seq e Encoder-Decoder]] → [[Meccanismo di Attention]] → [[Transformer]]

**Pre-elaborazione testo:**
- [[Bag of Words e TF-IDF]] — baseline classico
- [[Sentiment Analysis]], [[Language Model]]
- [[Learning to Rank]], [[Sistemi di raccomandazione]]

## 📊 Spettrale & riduzione di dimensionalità

**Lineare:**
- [[Singular Value Decomposition]] → [[Principal Component Analysis]]
- Strumenti: [[Power iteration]], [[Quoziente di Rayleigh]]

**Non lineare:**
- [[Multidimensional Scaling]] → [[Stochastic Neighbor Embedding]] → [[t-SNE]]

**Maledizione:**
- [[Curse of dimensionality]]

## ⚖️ Regolarizzazione & generalizzazione

- [[Regolarizzazione di Tikhonov]] (Ridge, L²)
- [[Lasso e Elastic Net]] (L¹, sparsità)
- [[Dropout]] (per reti profonde)
- [[Errore di approssimazione e di stima]] — decomposizione del rischio

## 🌳 Ensemble methods

- Base: [[Decision Tree]]
- Bagging: [[Random Forest]]
- Boosting: [[AdaBoost]] → [[Gradient Boosting]]

## 📈 Valutazione & selezione modello

- [[Metriche di classificazione]] — confusion matrix, F1, ROC-AUC
- [[Metriche di ranking]] — MAP, NDCG, MRR
- [[Cross-validation]] — k-fold, stratificata
- [[Ottimismo]], [[Rischio in-sample]] — gap teoria/pratica
- [[BIC]] — selezione asintotica
- [[Bootstrap]] — stima non parametrica

## 🎲 Framework Bayesiano (in ML)

- [[Apprendimento Bayesiano]] — paradigma
- [[Stima MAP]] — punto vs distribuzione
- [[Distribuzioni coniugate]] — chiusura analitica
- [[Metodi Monte Carlo]] — approssimazione

## 🔗 Argomenti trasversali rilevanti

Quando ti serve il quadro più ampio:

- [[Reti neurali]] — vedute incrociate ML/InfML/Ottimizzazione/MMFII
- [[SVD e decomposizione spettrale]] — visione unificata di PCA/SVD
- [[Regolarizzazione]] — collegamento ridge/MAP/dropout/early-stopping
- [[Ottimizzazione iterativa]] — GD/SGD/Newton da 5 corsi
- [[Probabilità bayesiana e inferenza]] — base inferenziale
- [[Entropia e information theory]] — cross-entropy, KL, t-SNE

## 📚 Per esame

**ML (Rodolà, 24/25):** focus su §1-§7 della pagina corso → [[Machine Learning]]
**InfML (Silvestri, 25/26):** focus su NLP/RNN/Transformer → [[Informatica per il Machine Learning]]
**MatML (Agliari, 25/26):** focus su statistica + Bayes + Monte Carlo → [[Matematica per il Machine Learning]]
