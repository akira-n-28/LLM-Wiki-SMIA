---
tipo: concetto
titolo: Gradient Boosting
tag: [ml, ensemble, boosting, ottimizzazione]
cluster: ml
ultima-modifica: 2026-04-30
---

# Gradient Boosting

Metodo ensemble che generalizza [[AdaBoost]]: addestra una sequenza di weak learner ([[Decision Tree|alberi]] tipicamente) dove ogni nuovo modello cerca di **correggere gli errori del precedente**.

## Idea chiave

Per una loss differenziabile $L(y, F(x))$ (es. $\sum_i (y_i - F(x_i))^2$ — MSE), si itera:

1. Inizializza $F_0$ (es. media dei target).
2. Per $m = 0, 1, \ldots$:
   a. Calcola gli **pseudo-residui**:
      $$
      r_i^{(m)} = -\left.\frac{\partial L(y_i, F(x_i))}{\partial F(x_i)}\right|_{F = F_m}
      $$
   b. Addestra un weak learner $h_{m+1}$ a fittare $\{(x_i, r_i^{(m)})\}$ (NON i target originali).
   c. Aggiorna: $F_{m+1}(x) = F_m(x) + \gamma_{m+1}\, h_{m+1}(x)$, con $\gamma$ scelto per line search:
      $$
      \gamma_{m+1} = \arg\min_\gamma L(y, F_m(x) + \gamma h_{m+1}(x))
      $$

## Perché si chiama "gradient" boosting

Lo step (a) è esattamente il gradiente della loss rispetto alla *predizione*. L'aggiornamento $F_{m+1} = F_m + \gamma h_{m+1}$ è quindi un passo di **discesa del gradiente nello spazio dei modelli**, dove $h_{m+1}$ approssima la direzione $-\nabla L / \partial F$. Vedi [[Discesa del gradiente]].

## Caso MSE

Con $L = \sum_i (y_i - F(x_i))^2$:
$$
r_i^{(m)} = 2(y_i - F_m(x_i)) \quad\Longrightarrow\quad h_{m+1} \approx y_i - F_m(x_i)
$$

cioè il weak learner fitta letteralmente il **residuo** — l'errore del modello attuale.

## Caratteristiche

- Funziona bene su **dati tabulari eterogenei** — XGBoost, LightGBM, CatBoost sono implementazioni popolari.
- Per la classificazione multinomiale si usa il paradigma **one-vs-rest**.
- Più sensibile agli iperparametri (learning rate, profondità, numero alberi) rispetto a [[Random Forest]].
- Più facile da overfittare se non si regolarizza correttamente.

## Gradient Boosting vs Deep Learning

| | Gradient Boosting | Deep Learning |
|---|---|---|
| Dati ideali | Tabulari eterogenei | Dataset grandi (img, testo) |
| Quantità di dati | Anche piccoli | Molti |
| Interpretabilità | Buona | Scarsa |
| Tempo di training | Veloce | Lungo |
| Feature engineering | Manuale | Automatico (rappresentazioni apprese) |
| Transfer learning | No | Sì (fine-tuning) |

## Collegamenti

- Predecessore: [[AdaBoost]]
- Mattoncino: [[Decision Tree]]
- Confronto: [[Random Forest]]
- Sottostante: [[Discesa del gradiente]]
- Applicazione al ranking: [[Learning to Rank]] (LambdaMART = LambdaRank + GB decision trees)
- Discusso in: [[Machine Learning]], [[Informatica per il Machine Learning]] (§6.5)

## Fonti

- [[Dispense Machine Learning — Galletti]] (§8, pp. 27-29)
