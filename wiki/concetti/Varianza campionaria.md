---
tipo: concetto
titolo: Varianza campionaria
tag: [statistica, fondamenti]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-04-30
---

# Varianza campionaria

Misura della dispersione dei valori di un campione attorno alla [[Media campionaria]]:

$$
s^2 = \frac{1}{n-1} \sum_{i=1}^{n} (x_i - \bar{x})^2
$$

## Perché `n-1`?

Il termine `n-1` (anziché `n`) corregge il bias dello stimatore: avendo calcolato `x̄` dai dati, abbiamo perso un grado di libertà. La dimostrazione classica si fa via `E[s²] = σ²` espandendo il quadrato e usando `Var(X̄) = σ²/n`:

$$
(n-1) \,\mathbb{E}[s^2] = \sum_i \mathbb{E}[X_i^2] - n\,\mathbb{E}[\bar{X}^2] = (n-1)\sigma^2.
$$

## Distribuzione (popolazione gaussiana)

Per `X₁, …, Xₙ ∼ i.i.d. N(μ, σ²)`:

$$
\frac{(n-1)\,s^2}{\sigma^2} \sim \chi^2_{n-1}
$$

Vedi [[Distribuzione chi-quadro]].

## Forma alternativa (utile per i conti)

$$
s^2 = \frac{1}{n-1}\left( \sum_i x_i^2 - n\bar{x}^2 \right)
$$

## Collegamenti

- Si calcola dopo: [[Media campionaria]]
- Distribuita come: [[Distribuzione chi-quadro]]
- Lo stimatore ML della varianza nel modello normale (`||y - Xβ̂||²/n`) è **biased**, mentre quello con `n-p` è non distorto — vedi [[Modello lineare normale]].

## Fonti

- [[Dispense MatML — Galletti]] (def. 1.4 e 1.9, pp. 2 e 6)
