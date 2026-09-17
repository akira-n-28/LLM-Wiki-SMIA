---
tipo: concetto
titolo: Random Forest
tag: [ml, ensemble, classificazione, regressione]
cluster: ml
ultima-modifica: 2026-04-30
---

# Random Forest

Metodo ensemble basato su **bagging** (bootstrap aggregating) di [[Decision Tree|alberi di decisione]]. L'idea è ridurre la *varianza* di un singolo albero (che ha bias basso ma alta varianza) addestrando molti alberi su sottoinsiemi randomici dei dati e mediando le predizioni.

## Algoritmo

1. **Splitta** i dati in partizioni random (bootstrap: campionamento con rimpiazzo).
2. **Addestra** un albero per ogni partizione. Tipicamente, in fase di split, si considera un sottoinsieme casuale delle feature — questo aumenta la diversità tra alberi.
3. **Predici** un nuovo punto facendolo passare per ogni albero.
4. **Combina** le predizioni:
   - Classificazione: voto di maggioranza (o media delle distribuzioni per classe).
   - Regressione: media dei valori predetti.

## Bias-varianza

- Un singolo albero profondo: **basso bias, alta varianza**.
- La media di molti alberi indipendenti: **stesso bias, varianza ridotta** ($\sim$ varianza del singolo $/n$ se indipendenti, di più altrimenti).

Il randomness su **dati** (bagging) e **feature** (random feature selection) decorrela gli alberi e abbassa ulteriormente la varianza dell'ensemble.

## Vantaggi pratici

- Pochi iperparametri sensibili (numero alberi, profondità max, feature per split).
- Buone performance "out of the box" su dati tabulari eterogenei.
- Out-of-bag error: stima gratis della generalizzazione (i campioni non usati per ogni albero).

## Confronto con il boosting

| | Random Forest | [[Gradient Boosting]] |
|---|---|---|
| Strategia | Riduce varianza | Riduce bias |
| Alberi | Indipendenti, profondi | Sequenziali, weak |
| Robustezza | Alta | Più sensibile a iperparametri |
| Tendenza | Underfit raro | Può overfittare |

## Collegamenti

- Mattoncino: [[Decision Tree]]
- Ensemble alternativi: [[AdaBoost]], [[Gradient Boosting]]
- Discusso in: [[Machine Learning]], [[Informatica per il Machine Learning]] (verrà collegato)

## Fonti

- [[Dispense Machine Learning — Galletti]] (§8, p. 26)
