---
tipo: concetto
titolo: Rischio in-sample
tag: [ml, statistica, fondamenti]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# Rischio in-sample

Misura quanto il modello si comporterebbe su **nuove risposte** generate dagli stessi input del training set. Fissa le feature osservate `x_1, …, x_n` ma estrae un nuovo set di target `y'` dalla vera distribuzione:

$$
\tau = \{(x_1, y_1), \ldots, (x_n, y_n)\} \qquad \tau' = \{(x_1, y'_1), \ldots, (x_n, y'_n)\}
$$

$$
\ell_{\mathrm{in}}(g_\tau^G) = \mathbb{E}_{Y'}\!\left[\frac{1}{n} \sum_{i=1}^n \mathrm{Loss}(Y'_i,\, g_\tau^G(x_i))\right]
$$

## Motivazione

La **training loss** `ℓ_τ(g_τ^G)` è biased verso il basso: il modello è stato ottimizzato esattamente su quei dati, quindi sottostima il rischio reale. Il rischio in-sample corregge questo bias tenendo fissi gli input (la parte "strutturale") ma usando risposte fresche.

## Relazione con training loss e ottimismo

$$
\ell_{\mathrm{in}}(g_\tau^G) = \ell_\tau(g_\tau^G) + \underbrace{\mathrm{OP}_\tau}_{\text{Ottimismo}}
$$

L'[[Ottimismo]] `OP_τ = ℓ_in - ℓ_τ` misura di quanto la training loss sottostimi il rischio in-sample.

## Stima del rischio reale

Il rischio in-sample è un proxy del rischio di generalizzazione `ℓ(g_τ^G)`. Non coincidono (il rischio reale usa anche input nuovi), ma sono correlati: stimare `ℓ_in` via `ℓ_τ + E[OP]` dà una correzione analitica utile quando i dati sono scarsi.

$$
\ell_{\mathrm{in}} \approx \ell_\tau + \frac{2\ell^* p}{n} \qquad \text{(OLS con } p \text{ parametri)}
$$

## Alternativi alla stima del rischio

| Metodo | Richiede |
|---|---|
| Test set | Dati abbondanti |
| Rischio in-sample + Ottimismo | Formula chiusa (solo modelli lineari) |
| [[Cross-validation]] | Calcolo aggiuntivo, generalità |
| [[BIC]] | Modello parametrico |

## Collegamenti

- Definisce: [[Ottimismo]]
- Stimato via: [[Cross-validation]], [[BIC]]
- Caso lineare: [[Minimi quadrati]]

## Fonti

- [[Dispense MatML — Galletti]] (§2.5, pp. 22-23)
