---
tipo: fonte
titolo: Dispense Machine Learning — Galletti
autori: [Marco Galletti]
corso: Machine Learning
docente: Emanuele Rodolà
anno-accademico: 2024/2025
data-pubblicazione: 2025
data-ingest: 2026-04-30
file-raw: raw/appunti/machine_learning.pdf
pagine: 29
ultima-modifica: 2026-04-30
tag: [ml, dispense, galletti]
---

# Dispense di Machine Learning — Galletti

Riassunto del corso di **Machine Learning** del prof. **Emanuele Rodolà** (A.A. 2024/2025, SMIA Sapienza), redatto da **Marco Galletti** in 29 pagine. Sintetico ma rigoroso: copre dai modelli lineari agli ensemble passando per reti, SVD, PCA, embedding non lineari.

**Riferimento file raw:** `raw/appunti/machine_learning.pdf`

## Riassunto in 5 punti

1. **Modelli lineari come fondamento.** [[Regressione lineare]] derivata in forma chiusa via **equazione normale** $\Theta = (X^\top X)^{-1} X^\top y$, generalizzata con la pseudoinversa di Moore-Penrose. Estesa a [[Regressione polinomiale]] (giustificata da Stone-Weierstrass) e [[Regressione logistica]] per classificazione binaria. Quando il problema è sottodeterminato si usa la [[Regolarizzazione di Tikhonov]] (L2 ridge, oppure L1 per indurre sparsità).

2. **Ottimizzazione iterativa.** Quando manca la forma chiusa (es. regressione logistica, MLP), si ricorre a [[Discesa del gradiente]] e sue varianti — momentum, [[Stochastic Gradient Descent|SGD]] con mini-batch, learning rate scheduling.

3. **Reti neurali e backpropagation.** [[Multi-Layer Perceptron]] come composizione $(\sigma \circ f)^n$, espressività garantita dal [[Teorema di approssimazione universale]]. L'addestramento è efficiente grazie alla [[Backpropagation]], che è differenziazione automatica in **reverse mode** sul [[Grafo computazionale]] della rete.

4. **Algebra spettrale per ML.** [[Quoziente di Rayleigh]] → [[Power iteration]] → [[Singular Value Decomposition|SVD]] → [[Principal Component Analysis|PCA]]. SVD come "coltellino svizzero": approssimazione a basso rango (Eckart-Young), pseudoinversa, compressione, denoising. PCA come massimizzazione della varianza spiegata.

5. **Beyond lineare e ensemble.** Quando le distanze euclidee non bastano: [[Spazio metrico|spazi metrici]] generali, [[Embedding isometrico]], [[Multidimensional Scaling|MDS]], [[Stochastic Neighbor Embedding|SNE]] e [[t-SNE]] (con [[Cauchy]] nel target per code lunghe), tutti basati sulla [[Divergenza di Kullback-Leibler]]. E gli **ensemble**: [[Decision Tree]] aggregati per **bagging** ([[Random Forest]]) o **boosting** ([[AdaBoost]], [[Gradient Boosting]] interpretato come gradient descent nello spazio delle funzioni).

## Citazioni / passaggi notevoli

> "Il [[Teorema di approssimazione universale|teorema di approssimazione universale]]: per ogni insieme compatto $\Omega \subset \mathbb{R}^p$, lo spazio delle funzioni $\phi = \sigma(Wx + b)$ è denso in $C(\Omega)$." (p. 17)

> "[Gradient Boosting] è inizializzato con un modello $F_0$ (che sarà pessimo). Invece di computare $\partial L / \partial F$, fittiamo un modello weak learner $h_{m+1}$ a $F_0$." (p. 28)

> "AdaBoost tende a overfittare." (p. 28) — segnala il limite intrinseco rispetto al gradient boosting.

## Tono e qualità delle dispense

- Notazione standard, formule pulite. Pochi refusi (es. "outcame" p. 2, "a' " latex non sempre uniforme nella sezione 2).
- Le sezioni 6 (PCA/SVD) e 8 (Ensemble) sono particolarmente curate.
- La sezione 2 (algebra lineare) è un richiamo veloce: dà per scontato la padronanza già acquisita in altri corsi.

## Pagine wiki create da questa ingest

**Concetti** (25):
- [[Curse of dimensionality]], [[Norma di Frobenius]]
- [[Regressione lineare]], [[Regressione polinomiale]], [[Regressione logistica]]
- [[Cross-entropy]], [[Overfitting e underfitting]], [[Cross-validation]]
- [[Regolarizzazione di Tikhonov]]
- [[Discesa del gradiente]], [[Stochastic Gradient Descent]]
- [[Multi-Layer Perceptron]], [[Backpropagation]], [[Grafo computazionale]], [[Teorema di approssimazione universale]]
- [[Singular Value Decomposition]], [[Principal Component Analysis]], [[Power iteration]], [[Quoziente di Rayleigh]]
- [[Spazio metrico]], [[Embedding isometrico]]
- [[Multidimensional Scaling]], [[Stochastic Neighbor Embedding]], [[t-SNE]], [[Divergenza di Kullback-Leibler]]
- [[Decision Tree]], [[Random Forest]], [[AdaBoost]], [[Gradient Boosting]]

**Persone** (4): [[Cauchy]], [[Weierstrass]], [[Tikhonov]], [[Frobenius]]

**Aggiornamenti**: [[Machine Learning]] passa a 🟢.

## Contraddizioni rilevate

Nessuna — è la prima fonte ingerita in profondità, non c'è nulla da contraddire.

## Ganci per ingest futuri

Punti dove altri corsi entreranno in dialogo con queste pagine:

- **[[Metodi Numerici]]** rivedrà [[Singular Value Decomposition|SVD]], [[Power iteration]], [[Norma di Frobenius]], [[Regolarizzazione di Tikhonov]] dal lato algoritmico/numerico.
- **[[Modelli Matematici per la Fisica II]]** riprende [[Divergenza di Kullback-Leibler]] (entropia di Shannon, principio di massima entropia) e dovrebbe collegare il modello di Hopfield agli MLP/reti neurali.
- **[[Ottimizzazione]]** approfondirà [[Discesa del gradiente]], convergenza, Tikhonov, problema dell'addestramento.
- **[[Informatica per il Machine Learning]]** estenderà [[Multi-Layer Perceptron]] a RNN/LSTM/Word Embedding e [[Random Forest]]/[[Gradient Boosting]] a Learning to Rank.
- **[[Analisi Matematica II]]** fornirà la base topologica di [[Spazio metrico]] (la dispensa qui ha solo l'essenziale).
- **[[Matematica per il Machine Learning]]** (Agliari) rifletterà su rischio empirico/teorico e bias-variance: sintetizzerà con [[Overfitting e underfitting]].
