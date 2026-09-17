---
tipo: concetto
titolo: Decision Tree
tag: [ml, classificazione, regressione]
cluster: ml
ultima-modifica: 2026-04-30
---

# Decision Tree (albero di decisione)

Modello a **albero binario** in cui ogni nodo interno rappresenta una *domanda* su una feature ("$x_j > t$?") e ogni cammino dalla radice a una foglia rappresenta una sequenza di decisioni. Le foglie portano la predizione finale.

## Tipi di output

- **Classificazione**: ogni foglia contiene la classe maggioritaria dei dati che vi cadono. Lo split interno **massimizza il guadagno di informazione** $\Delta H = H_{\text{prima}} - H_{\text{dopo}}$ (entropia che diminuisce ⇔ partizione più "pura").
- **Regressione** (regression tree): ogni foglia contiene la media dei target dei dati. Lo split interno **minimizza l'MSE pesato**:
  $$
  \frac{n_{\text{left}}}{n} \cdot \mathrm{MSE}_{\text{left}} + \frac{n_{\text{right}}}{n} \cdot \mathrm{MSE}_{\text{right}}
  $$

## Algoritmo LEARN-DECISION-TREE

Algoritmo greedy top-down per costruire un albero di classificazione. A ogni nodo:

1. Scegli la feature $a^*$ e la soglia $t$ che massimizzano il **guadagno di informazione**:
$$\text{Gain}(S, a, t) = H(S) - \frac{|S_\text{left}|}{|S|} H(S_\text{left}) - \frac{|S_\text{right}|}{|S|} H(S_\text{right})$$
dove $H(S) = -\sum_c p_c \log p_c$ è l'**entropia** di Shannon della distribuzione delle classi in $S$.
2. Crea due figli con i sottoinsiemi $S_\text{left}$, $S_\text{right}$.
3. Fermati se: tutti gli esempi hanno la stessa classe, o la profondità massima è raggiunta.

Il Gain misura la riduzione di entropia (impurità) prodotta dallo split. In alternativa si usa l'indice di Gini.

## Decision stump

Caso degenere: albero a un solo livello (singolo split). È il prototipico **weak learner** nei metodi ensemble (vedi [[AdaBoost]]).

## Profondità e complessità

A profondità $k$ lo split usa al più $k-1$ feature in interazione. Alberi profondi catturano interazioni complesse ma soffrono di [[Overfitting e underfitting|overfitting]] — si limita con `max_depth`, `min_samples_leaf`, pruning.

## Vantaggi e limiti

✅ Interpretabili (un albero piccolo si "legge"); robusti a feature di scala mista; gestiscono dati numerici e categorici.

⚠️ Variano molto con piccole perturbazioni del training set (alta varianza). Mitigato dagli ensemble: [[Random Forest]], [[Gradient Boosting]].

## Collegamenti

- Aggregazione: [[Random Forest]] (bagging), [[AdaBoost]], [[Gradient Boosting]] (boosting)
- Discusso in: [[Machine Learning]], [[Algoritmi e Complessità]] (versione algoritmica)

## Fonti

- [[Dispense Machine Learning — Galletti]] (§8, pp. 25-26)
- [[Dispense InfML — Galletti]] (§8, pp. 27-31)
