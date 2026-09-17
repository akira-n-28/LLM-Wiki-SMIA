---
tipo: concetto
titolo: Cross-validation
tag: [ml, validazione]
cluster: ml
fonti: 2
ultima-modifica: 2026-05-04
---

# Cross-validation

Tecnica per stimare l'errore di generalizzazione di un modello senza richiedere un test set indipendente di grandi dimensioni.

## $k$-fold cross-validation

Si divide il dataset in $k$ parti (fold). Per ogni $i = 1, \ldots, k$:
1. Si usa la $i$-esima fold come **validation set**.
2. Si addestra il modello sulle altre $k-1$ fold.
3. Si calcola l'errore sulla fold di validazione.

L'errore stimato è la **media** dei $k$ errori. Tipicamente $k = 5$ o $k = 10$.

## Casi particolari

- **Hold-out:** $k = 1$, semplice split train/validation.
- **Leave-one-out (LOO):** $k = n$ (un campione per fold). Stima a bassa varianza, ma costo $n$ volte quello di un training.

## A cosa serve

- Diagnosticare [[Overfitting e underfitting|overfitting]].
- Selezionare iperparametri (grado polinomiale, $\alpha$ di [[Regolarizzazione di Tikhonov|Tikhonov]], profondità di un [[Decision Tree]]).
- Stimare un intervallo di confidenza dell'errore.

## Definizione formale (MatML)

Sia `T` un dataset con `|T| = n`. Lo partizioniamo in `K` sottoinsiemi disgiunti `c_1, …, c_K` con `n_k ≈ n/K`. Per ogni fold `k`, `T_{-k} = T \ c_k` è il training set ridotto. La stima cross-validated del rischio è:

$$
\mathrm{CV}_K := \sum_{k=1}^K \frac{n_k}{n} \ell_{c_k}(g_{T_{-k}}) = \frac{1}{n} \sum_{i=1}^n \mathrm{Loss}(y_i, g_{T_{-\kappa(i)}}(x_i))
$$

dove `κ(i)` è il fold di appartenenza dell'osservazione `i`.

## Trade-off nella scelta di K

- **K grande**: training set quasi completo → bias↓, ma i K modelli sono fortemente correlati → varianza↑.
- **K piccolo**: maggiore indipendenza tra i fold → varianza↓, ma training set ridotto → bias↑.
- **Leave-one-out** (`K = n`): stima a bias minimo, costo computazionale massimo.

## Relazione con ottimismo e rischio in-sample

La CV è l'alternativa alla correzione analitica via [[Ottimismo]] e [[Rischio in-sample]]:

| Approccio | Richiede | Limitazioni |
|---|---|---|
| Test set | Dati abbondanti | Spreca dati |
| Ottimismo (+ rischio in-sample) | Pochi dati, formula chiusa | Solo per modelli lineari |
| Cross-validation | Pochi dati, sufficiente calcolo | Generale |

## Alternative parametriche

[[BIC]] offre una penalizzazione analitica della complessità senza partizionare i dati.

## Collegamenti

- [[Overfitting e underfitting]]
- [[Regolarizzazione di Tikhonov]]
- Alternativa a: [[Ottimismo]], [[BIC]]
- Discusso in: [[Machine Learning]], [[Matematica per il Machine Learning]]

## Fonti

- [[Dispense Machine Learning — Galletti]] (§3.2, p. 10)
- [[Dispense MatML — Galletti]] (§2.6, pp. 23-24)
