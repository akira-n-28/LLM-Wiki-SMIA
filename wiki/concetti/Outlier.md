---
tipo: concetto
titolo: Outlier
tag: [statistica, fondamenti]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-04-30
---

# Outlier

Valore anomalo che si discosta significativamente dai valori attesi del campione. Definizione operativa basata sui quartili:

$$
x_i \text{ è outlier se } x_i > Q_3 + 1.5\,\Delta \quad\text{o}\quad x_i < Q_1 - 1.5\,\Delta
$$

dove `Q₁, Q₃` sono il primo e terzo quartile e `Δ = Q₃ - Q₁` è la **distanza interquartile** (IQR).

## Visualizzazione

Gli outlier sono i punti che cadono **oltre i baffi** del box-plot (segnati tipicamente con `×`). I baffi si estendono dal box (Q1–Q3) ai valori min/max **escludendo** gli outlier.

## Effetto su indici di sintesi

Gli outlier influenzano fortemente la [[Media campionaria]] (la "tirano" verso le code), mentre la mediana è una misura **robusta** che li ignora. Questo crea il classico disallineamento media/mediana/moda nelle distribuzioni asimmetriche:

- Asimmetria a destra (coda lunga a destra): Moda < Mediana < Media
- Asimmetria a sinistra (coda lunga a sinistra): Media < Mediana < Moda

## Collegamenti

- Affianca: [[Media campionaria]], [[Varianza campionaria]] (entrambe non robuste)
- Trattamento pratico: imputazione con mediana, oppure rimozione (con cautela)

## Fonti

- [[Dispense MatML — Galletti]] (def. 1.5, p. 3; box-plot p. 4)
