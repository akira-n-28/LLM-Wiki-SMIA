---
tipo: concetto
titolo: Regressione polinomiale
tag: [ml, regressione]
cluster: ml
fonti: 2
ultima-modifica: 2026-05-04
---

# Regressione polinomiale

Estensione della [[Regressione lineare]] in cui le feature sono potenze del regressore originale: $y_i = b + \sum_{j=1}^k a_j x_i^j$. Il modello è **polinomiale nei dati** ma resta **lineare nei parametri**, quindi la soluzione passa ancora per l'equazione normale con la matrice di design

$$
X = \begin{pmatrix} x_1^k & x_1^{k-1} & \cdots & x_1 & 1 \\ \vdots & & & & \vdots \\ x_n^k & x_n^{k-1} & \cdots & x_n & 1 \end{pmatrix}
$$

## Giustificazione teorica: Stone-Weierstrass

> **Teorema (Stone-Weierstrass).** Sia $f : [a, b] \to \mathbb{R}$ continua. Per ogni $\varepsilon > 0$ esiste un polinomio $p$ tale che $|f(x) - p(x)| < \varepsilon$ per ogni $x \in [a, b]$.

Quindi *ogni* funzione continua può essere approssimata uniformemente con un polinomio di grado sufficientemente alto.

## Il pericolo: overfitting

Aumentare il grado migliora l'errore sul training, ma il modello inizia a fittare anche il rumore. Vedi [[Overfitting e underfitting]] e contromisure: [[Cross-validation]], [[Regolarizzazione di Tikhonov]].

## Framework formale (MatML)

La matrice del disegno è la [[Matrice di Vandermonde]] `X ∈ ℝ^{n×p}`, con `X_{ij} = u_i^{j-1}`. La soluzione [[Minimi quadrati|OLS]] è:

$$
\hat\beta = (X^T X)^{-1} X^T y
$$

Sotto `U ∼ U(0,1)` il valore atteso di `X^T X / n` converge alla [[Matrice di Hilbert]]:

$$
\mathbb{E}\!\left[\tfrac{1}{n} X^T X\right] = H_p, \quad H_{ij} = \frac{1}{i+j-1}
$$

Il **miglior modello teorico** `g^{G_p}` nella classe soddisfa il sistema:

$$
H_p \beta = \tilde{H} \beta^*
$$

dove `H̃` è il blocco `p × 4` della matrice di Hilbert (4 = grado della ground truth + 1).

### Decomposizione del rischio

$$
\ell(g_\tau^{G_p}) = \ell^* + \underbrace{\mathbb{E}\!\left[(X^T \beta^{G_p} - X^T \beta^*)^2\right]}_{\text{Errore di approssimazione}} + \underbrace{\mathbb{E}\!\left[(X^T \hat\beta - X^T \beta^{G_p})^2\right]}_{\text{Errore statistico}}
$$

Aumentare `p`: approssimazione ↓, stima ↑. Vedi [[Errore di approssimazione e di stima]] e [[Bias-Variance trade-off]].

## Collegamenti

- Estensione di: [[Regressione lineare]]
- Persone: [[Weierstrass]]
- Strumento: [[Matrice di Vandermonde]], [[Matrice di Hilbert]]
- Risolto con: [[Minimi quadrati]]
- Discusso in: [[Machine Learning]], [[Matematica per il Machine Learning]]

## Fonti

- [[Dispense Machine Learning — Galletti]] (§3.2, pp. 9-10)
- [[Dispense MatML — Galletti]] (esempi 2.3, 2.5-2.6, pp. 14-21)
