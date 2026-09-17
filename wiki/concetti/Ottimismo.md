---
tipo: concetto
titolo: Ottimismo
tag: [ml, statistica, fondamenti]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# Ottimismo

Divario tra il [[Rischio in-sample]] e la training loss per un modello addestrato su `τ`:

$$
\mathrm{OP}_\tau = \ell_{\mathrm{in}}(g_\tau^G) - \ell_\tau(g_\tau^G)
$$

Sempre `OP_τ ≥ 0`: la training loss sottostima sistematicamente il rischio su dati non visti.

## Ottimismo atteso

Poiché `OP_τ` dipende dal training set estratto, si media su tutte le possibili realizzazioni dei target `Y` (feature `X` fisse):

$$
\mathbb{E}_{T|X}[\mathrm{OP}_T] = \frac{2}{n} \sum_{i=1}^n \mathrm{Cov}_{T|X}\!\left(g_\tau^G(x_i),\, y_i\right)
$$

Questo vale per **squared error loss** e **0-1 loss**.

## Interpretazione

- **Modello indipendente dai dati**: covarianza nulla → ottimismo atteso = 0.
- **Interpolazione perfetta** (`ŷ_i = y_i`): `Cov(y_i, y_i) = Var(y_i) = ℓ*` → ottimismo atteso = `2ℓ*`.
- In generale: più il modello è flessibile (alta complessità), più l'ottimismo atteso è alto.

## Caso lineare (OLS)

Per `g_τ^G(x_i) = x_i^T \hat\beta` con `\hat\beta = X^\dagger y`:

$$
\mathbb{E}_{T|X}[\mathrm{OP}_T] = \frac{2}{n} \mathrm{Tr}\!\left(\mathrm{Cov}(X\hat\beta, y)\right) = \frac{2}{n} \ell^* \mathrm{Tr}(XX^\dagger) = \frac{2\ell^* p}{n}
$$

dove si usa `Tr(XX†) = Tr(X†X) = Tr(I_p) = p`.

## Correzione della training loss

$$
\hat\ell_{\mathrm{in}} = \ell_\tau + \frac{2\ell^* p}{n}
$$

Questa correzione è analoga alla penalità del [[BIC]] (entrambe proporzionali a `p/n`).

## Collegamenti

- Definito da: [[Rischio in-sample]]
- Calcolato in: [[Minimi quadrati]] (via traccia della matrice di proiezione)
- Alternativa: [[Cross-validation]], [[BIC]]
- Vedi anche: [[Bias-Variance trade-off]]

## Fonti

- [[Dispense MatML — Galletti]] (§2.5, teorema 2.2, esempio 2.7, pp. 22-23)
