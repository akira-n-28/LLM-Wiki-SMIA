---
tipo: concetto
titolo: Metriche di classificazione
tag: [ml, valutazione]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# Metriche di classificazione

Metriche per valutare la qualità di un modello di classificazione. Si basano sulla **confusion matrix** (caso binario):

$$
\text{Confusion Matrix} = \begin{pmatrix} TP & FP \\ FN & TN \end{pmatrix}
$$

dove TP = true positive, TN = true negative, FP = false positive, FN = false negative.

## Metriche principali

**Accuracy** — frazione di predizioni corrette:
$$
\text{Accuracy} = \frac{TP + TN}{TP + TN + FP + FN}
$$
*Attenzione:* su dataset sbilanciati (es. malattie rare) l'accuracy può essere fuorviante.

**Precision** — quanti dei positivi predetti sono davvero positivi:
$$
\text{Precision} = \frac{TP}{TP + FP}
$$

**Recall** (Sensitivity, TPR) — quanti dei positivi reali sono stati trovati:
$$
\text{Recall} = \frac{TP}{TP + FN}
$$

**F1-Score** — media armonica di precision e recall:
$$
F_1 = \frac{2 \cdot \text{Precision} \cdot \text{Recall}}{\text{Precision} + \text{Recall}} = \frac{2}{\frac{1}{\text{Precision}} + \frac{1}{\text{Recall}}}
$$

## Trade-off Precision–Recall

Abbassare la soglia di classificazione aumenta la recall e riduce la precision (e viceversa). La **Precision-Recall Curve** visualizza questo trade-off. È più informativa della ROC quando i positivi sono rari.

## Curva ROC e AUC

La **ROC** (Receiver Operating Characteristic) mostra come varia il True Positive Rate (= Recall) al variare del False Positive Rate:
$$
FPR = \frac{FP}{FP + TN}
$$

L'**AUC** (Area Under the Curve) quantifica la qualità complessiva:
- AUC = 1 → classificatore perfetto
- AUC = 0.5 → classificatore casuale (diagonale ROC)
- AUC < 0.5 → peggio del caso

## Caso multiclasse

La confusion matrix diventa $K \times K$. Si estende con approcci **one-vs-rest** per precision/recall/F1 per classe.

## Metriche per la regressione

- MSE: $\frac{1}{N}\sum(y_i - \hat{y}_i)^2$
- MAE: $\frac{1}{N}\sum|y_i - \hat{y}_i|$
- RMSE: $\sqrt{\text{MSE}}$

## Vs metriche di ranking

Le metriche di classificazione non catturano la qualità di un *ordinamento*: due sistemi con gli stessi TP ma in ordine diverso hanno stesso F1. Vedi [[Metriche di ranking]].

## Collegamenti

- Complementari per il ranking: [[Metriche di ranking]]
- Modello di classificazione: [[Regressione logistica]], [[Decision Tree]]
- Loss associata: [[Cross-entropy]], [[Funzione sigmoide]]
- Discusso in: [[Informatica per il Machine Learning]] (§5)

## Fonti

- [[Dispense InfML — Galletti]] (§5, pp. 15-17)
