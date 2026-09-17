---
tipo: concetto
titolo: Overfitting e underfitting
tag: [ml, generalizzazione]
cluster: ml
ultima-modifica: 2026-04-30
---

# Overfitting e underfitting

Due fallimenti speculari della scelta di capacità di un modello.

- **Overfitting:** il modello si adatta troppo ai dati di training, imparando *anche il rumore*. Errore basso sul training, alto sul test. Tipico di modelli con troppi parametri ([[Regressione polinomiale]] di grado alto, [[Multi-Layer Perceptron|MLP]] sovradimensionati, [[Decision Tree]] profondi).
- **Underfitting:** il modello non ha capacità sufficiente per catturare la struttura. Errore alto su training e test.

Il punto di equilibrio è il classico trade-off **bias-varianza**: capacità troppo bassa ⇒ alto bias; capacità troppo alta ⇒ alta varianza.

## Strategie contro l'overfitting

- **[[Cross-validation]]** (in particolare $k$-fold) per stimare l'errore di generalizzazione.
- **Regolarizzazione**: [[Regolarizzazione di Tikhonov]] (L2, ridge), L1 (lasso, induce sparsità).
- **Early stopping** durante l'ottimizzazione iterativa.
- **Dropout** (per le reti neurali).
- **Riduzione di dimensionalità** ([[Principal Component Analysis|PCA]], [[Singular Value Decomposition|SVD]]).
- **Ensemble** di modelli ([[Random Forest]], [[Gradient Boosting]]).

## Collegamenti

- [[Curse of dimensionality]] — peggiora il problema in alte dimensioni.
- [[Cross-validation]] — diagnostica.
- [[Regolarizzazione di Tikhonov]] — rimedio.

## Fonti

- [[Dispense Machine Learning — Galletti]] (§3.2, p. 9)
