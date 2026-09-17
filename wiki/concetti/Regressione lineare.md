---
tipo: concetto
titolo: Regressione lineare
tag: [ml, ottimizzazione, regressione]
cluster: ml
ultima-modifica: 2026-04-30
---

# Regressione lineare

Modello statistico più semplice per stimare la relazione tra una variabile target $y$ e una o più feature $x$. L'ipotesi è che $y \approx a x + b$ (univariata) o $y = A x + b$ (multivariata). I parametri $\Theta = \{a, b\}$ minimizzano l'errore **quadratico medio**:

$$
\ell(\Theta) = \sum_{i=1}^n (y_i - f_\Theta(x_i))^2
$$

## Forma matriciale e soluzione chiusa

Ponendo $X$ matrice di design (colonna di 1 per il bias) e $y$ vettore dei target:

$$
\ell(\Theta) = \|y - X\Theta\|_2^2
$$

Annullando il gradiente $\nabla_\Theta \ell = -2X^\top y + 2X^\top X \Theta = 0$ si ottiene l'**equazione normale**:

$$
X^\top X\, \Theta = X^\top y \quad\Longrightarrow\quad \Theta = \underbrace{(X^\top X)^{-1} X^\top}_{X^\dagger}\, y
$$

dove $X^\dagger$ è la **pseudoinversa di Moore-Penrose** (vedi [[Singular Value Decomposition]]). Se $X$ è quadrata e invertibile, $X^\dagger = X^{-1}$.

## Caratteristiche

- È **lineare nei parametri**, non nei dati: la stessa formula vale per la [[Regressione polinomiale]] usando feature $x, x^2, \ldots, x^k$.
- La loss MSE è **convessa e differenziabile**: il minimo globale esiste e coincide con il punto stazionario.
- Quando $X^\top X$ è singolare o mal condizionata si usa la [[Regolarizzazione di Tikhonov]] (ridge).

## Regolarizzazione

Nella regressione multivariata l'overfitting è possibile quando il modello è più complesso del task. La penalità generale ha la forma:

$$\text{Cost}(h) = \text{MSE}(y, \hat{y}) + \lambda \cdot L_q(w)$$

- **$q=2$ (Ridge / Tikhonov):** [[Regolarizzazione di Tikhonov]] — riduce i pesi, soluzione chiusa $\hat{w} = (X^\top X + \lambda I)^{-1} X^\top y$.
- **$q=1$ (Lasso):** [[Lasso e Elastic Net]] — induce sparsità, annulla esattamente alcuni pesi.
- **Elastic Net:** [[Lasso e Elastic Net]] — combina L1 e L2; supera i limiti del Lasso con variabili correlate.

## Collegamenti

- Versione probabilistica con output binario: [[Regressione logistica]]
- Regolarizzazione L2: [[Regolarizzazione di Tikhonov]]
- Regolarizzazione L1 e mista: [[Lasso e Elastic Net]]
- Metodo iterativo alternativo alla forma chiusa: [[Discesa del gradiente]]
- Discusso in: [[Machine Learning]], [[Informatica per il Machine Learning]] (§3)

## Fonti

- [[Dispense Machine Learning — Galletti]] (§3.1, pp. 5-9)
