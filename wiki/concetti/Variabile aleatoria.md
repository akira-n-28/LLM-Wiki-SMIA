---
tipo: concetto
titolo: Variabile aleatoria
tag: [probabilità, fondamenti]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-06
---

# Variabile aleatoria

Una **variabile aleatoria** è una funzione $X : S \to \mathbb{R}$ definita su uno [[Spazio di probabilità]] $(S, \mathcal{F}, P)$, misurabile rispetto alla σ-algebra $\mathcal{F}$.

Intuitivamente: assegna un numero reale a ogni esito elementare dello spazio campionario. Si distingue tra **discrete** (immagine finita o numerabile) e **continue** (immagine in un intervallo di $\mathbb{R}$).

## Tipi fondamentali

| Tipo | Definizione | E[X] |
|------|-------------|------|
| Costante | X(ω) = c ∀ω | c |
| **Bernoulli** Ber(p) | P(X=1)=p, P(X=0)=1-p | p |
| **Binomiale** B(n,p) | P(X=k) = C(n,k)·pᵏ·(1-p)ⁿ⁻ᵏ | np |
| **Geometrica** Geo(p) | P(X=k) = (1-p)^(k-1)·p | 1/p |
| **Poisson** Poi(λ) | P(X=k) = e^{-λ}λᵏ/k! | λ |
| Uniforme discreta su [1..n] | P(X=j) = 1/n | (n+1)/2 |

## Funzione di ripartizione

$$
F(x) = P(X \leq x) = \sum_{y \leq x} P(X = y)
$$

Proprietà: `0 ≤ F(x) ≤ 1`, crescente, `lim_{x→+∞} F(x) = 1`, `lim_{x→-∞} F(x) = 0`. È continua a destra (a sinistra nelle dispense Galletti).

## Densità discreta

La funzione `p_X(x) = P(X = x)` con `Σ_x p_X(x) = 1` è la **massa di probabilità** di X.

## Variabili aleatorie congiunte

Per `X, Y : S → ℝ`:
- **Densità congiunta**: `p(x,y) = P(X=x ∩ Y=y)`
- **Densità marginale**: `p_X(x) = Σ_y p(x,y)`
- **Indipendenza**: `p(x,y) = p_X(x)·p_Y(y)` per ogni `x, y`

## Variabili aleatorie continue

Una v.a. $X$ è **continua** se la sua [[Funzione di ripartizione]] $F_X(x) = P(X \leq x)$ è continua e quasi ovunque derivabile. Esiste allora una funzione $f_X : \mathbb{R} \to [0, +\infty)$, detta **densità di probabilità (PDF)**, tale che:

$$
F_X(x) = \int_{-\infty}^{x} f_X(t)\, dt, \qquad P(a \leq X \leq b) = \int_a^b f_X(t)\, dt
$$

**Proprietà della PDF:** $f_X(x) \geq 0$ e $\int_\mathbb{R} f_X(x)\,dx = 1$. Diversamente dal caso discreto, $f_X(x)$ **non è una probabilità** (può essere $> 1$); $P(X = x) = 0$ per ogni $x$.

**Valore atteso e varianza nel caso continuo:**
$$
E[X] = \int_\mathbb{R} x\, f_X(x)\, dx, \qquad \mathrm{Var}(X) = \int_\mathbb{R} (x - E[X])^2\, f_X(x)\, dx
$$

**Distribuzioni continue notevoli:**

| Distribuzione | PDF | E[X] | Var(X) |
|---|---|---|---|
| Uniforme su $[a,b]$ | $\frac{1}{b-a} \cdot \mathbf{1}_{[a,b]}$ | $(a+b)/2$ | $(b-a)^2/12$ |
| Esponenziale $\mathcal{E}(\lambda)$ | $\lambda e^{-\lambda x} \mathbf{1}_{x\geq 0}$ | $1/\lambda$ | $1/\lambda^2$ |
| Normale $\mathcal{N}(\mu, \sigma^2)$ | $\frac{1}{\sigma\sqrt{2\pi}}e^{-(x-\mu)^2/(2\sigma^2)}$ | $\mu$ | $\sigma^2$ |

Vedi [[Distribuzione esponenziale]], [[Distribuzione Normale Multivariata]] per il caso vettoriale.

**Caso vettoriale:** $\mathbf{X} = (X_1, \ldots, X_n)$ ha **densità congiunta** $f_\mathbf{X}: \mathbb{R}^n \to [0, +\infty)$ con $\int_{\mathbb{R}^n} f_\mathbf{X} = 1$. Indipendenza: $f_\mathbf{X}(x_1, \ldots, x_n) = \prod_i f_{X_i}(x_i)$.

## Connessione con la statistica

In [[Matematica per il Machine Learning]], le osservazioni `(Xᵢ, Yᵢ)` del training set sono variabili aleatorie i.i.d. con distribuzione congiunta `f(x,y)`. Il [[Rischio teorico]] è un valore atteso su questa distribuzione.

## Connessione con i processi stocastici

[[Catena di Markov]] è una sequenza di variabili aleatorie `X_0, X_1, X_2, …` con una struttura di dipendenza condizionata specifica.

## Connessione con il teorema di Bayes

Nel [[Apprendimento Bayesiano]], il parametro `θ` è trattato come una variabile aleatoria (con prior `P(θ)`), non come un valore fisso ignoto.

## Persone

Formalizzazione dovuta a [[Kolmogorov, Andrey]] e al programma di assiomatizzazione della probabilità del 1933.

## Collegamenti

- Dipende da: [[Spazio di probabilità]]
- Caso continuo: [[Distribuzione esponenziale]], [[Distribuzione Normale Multivariata]], [[Distribuzione t-Student]]
- Caso discreto: [[Distribuzione di Poisson]], [[Distribuzione geometrica]]
- Usata in: [[Valore atteso]], [[Varianza e covarianza]], [[Attesa condizionata]]

## Fonti

- [[Dispense ProbStat — Galletti]] (§2.2, pp. 17-18)
