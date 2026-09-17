---
tipo: concetto
titolo: Funzione di perdita
tag: [ml, fondamenti]
cluster: ml
fonti: 1
ultima-modifica: 2026-04-30
---

# Funzione di perdita (Loss)

Funzione `L(y, ŷ)` che misura l'errore della previsione `ŷ` rispetto al valore vero `y`. È l'oggetto da minimizzare in valore atteso.

## Funzioni comuni

### Regressione
- **MSE (Mean Squared Error)**: `L(y, ŷ) = (y - ŷ)²`. Differenziabile, comoda, sensibile agli outlier. Per essa il predittore ottimo è `g*(x) = E[Y|X=x]`.
- **MAE (Mean Absolute Error)**: `L(y, ŷ) = |y - ŷ|`. Robusta agli outlier; il predittore ottimo è la mediana condizionale.

### Classificazione
- **0-1 loss**: `L(y, ŷ) = I(y ≠ ŷ)`. Coincide con la probabilità di errore `P(Y ≠ g(X))`. Predittore ottimo: classificatore di Bayes `g*(x) = arg max_y f(y|x)`.
- **BCE (Binary Cross-Entropy)**: usata per output probabilistici.

## Distinzioni

- **Loss `L(y, ŷ)`**: comoda per ottimizzazione (differenziabile).
- **Errore `|y - ŷ|`**: misura interpretabile.
- **Rischio `ℓ(g) = E[L(Y, g(X))]`**: funzionale (operare su funzioni).

## Loss e learner

La scelta di `L` determina il learner ottimo:
- MSE → [[Minimi quadrati]] (OLS) per modelli lineari.
- log-loss / KL → [[Stima di Massima Verosimiglianza]].

## Collegamenti

- Componente di: [[Rischio teorico]], [[Rischio empirico]]
- Fondamento di: [[ERM]]
- Casi particolari: vedi [[Minimi quadrati]] (MSE), [[Divergenza di Kullback-Leibler]] (log-loss)

## Fonti

- [[Dispense MatML — Galletti]] (pp. 9-10)
