---
tipo: concetto
titolo: Funzione generatrice dei momenti
tag: [probabilità, statistica, mmf]
cluster: probabilistica
fonti: 2
ultima-modifica: 2026-05-06
---

# Funzione generatrice dei momenti (MGF)

Data una variabile aleatoria `X`, la funzione generatrice dei momenti è:

$$
M_X(s) = \mathbb{E}[e^{sX}], \quad s \in \mathbb{R}
$$

## Proprietà fondamentali

- **Unicità**: se `M_X(s) = M_Y(s)` per ogni `s` in un intorno di 0, allora `X =^d Y`.
- **Momenti**: il `k`-esimo momento si ottiene derivando `k` volte e valutando in 0:
  $$\mathbb{E}[X^k] = M_X^{(k)}(0)$$
- **Indipendenza**: se `X ⊥ Y`, allora `M_{X+Y}(s) = M_X(s) M_Y(s)`.

## MGF della distribuzione Gamma

Per `X ∼ Gamma(α, λ)` con densità `f(x) = λ^α x^{α-1} e^{-λx} / Γ(α)`:

$$
M_X(s) = \left(\frac{\lambda}{\lambda - s}\right)^\alpha, \quad s < \lambda
$$

## MGF della distribuzione chi-quadro

`χ²_n = Gamma(n/2, 1/2)`, quindi:

$$
M_{\chi^2_n}(s) = (1 - 2s)^{-n/2}, \quad s < \frac{1}{2}
$$

## Uso chiave: dimostrazione che la norma al quadrato di un vettore gaussiano è χ²

Sia `Z ∼ N(0, I_n)`. Allora:

$$
\mathbb{E}[e^{s Z_1^2}] = \frac{1}{\sqrt{2\pi}} \int_{-\infty}^{+\infty} e^{sz^2} e^{-z^2/2}\,dz = \frac{1}{\sqrt{1 - 2s}}, \quad s < \tfrac{1}{2}
$$

Per indipendenza delle componenti:

$$
M_{\|Z\|^2}(s) = \prod_{i=1}^n \mathbb{E}[e^{sZ_i^2}] = (1-2s)^{-n/2}
$$

Questa coincide con la MGF di `Gamma(n/2, 1/2) = χ²_n`. Per unicità della MGF, `‖Z‖² ∼ χ²_n`.

## Collegamento con la distribuzione Normale Multivariata

Per `X ∼ N(μ, Σ)`, il fatto che `(X-μ)^T Σ^{-1} (X-μ) ∼ χ²_d` si dimostra via MGF dopo aver fattorizzato `Σ = BB^T` (vedi [[Distribuzione Normale Multivariata]]).

## Collegamento con chi-quadro non centrale

Se `X ∼ N(μ, I_n)` con `μ ≠ 0`, allora `‖X‖² ∼ χ²_n(‖μ‖²)` (chi-quadro non centrale). Emerge nei test statistici.

## Funzione generatrice dei cumulanti

$$K_X(t) = \log \zeta_X(t) = \log \mathbb{E}[e^{tX}]$$

I **cumulanti** $\kappa_n$ sono i coefficienti dello sviluppo di Taylor: $K_X(t) = \sum_{n=1}^\infty \frac{t^n}{n!}\kappa_n$.

$$\kappa_1 = K_X'(0) = \mathbb{E}[X], \qquad \kappa_2 = K_X''(0) = \text{Var}(X), \qquad \kappa_n = 0\ \forall n\geq 3 \text{ per } X \text{ gaussiana}$$

**Dimostrazione del TLC via cumulanti.** Per $\hat{S}_n = (S_n - n\mu)/(\sigma\sqrt{n})$ con $X_i$ i.i.d.:

$$\kappa_l(\hat{S}_n) = \frac{\kappa_l(X)}{\sigma^l} \cdot \frac{n}{n^{l/2}} \xrightarrow{n\to\infty} \begin{cases} 1 & l=2 \\ 0 & l \geq 3 \end{cases}$$

Dunque $K_{\hat{S}_n}(t) \to \frac{t^2}{2}$ (MGF della gaussiana standard), e $\hat{S}_n \xrightarrow{d} \mathcal{N}(0,1)$.

## Applicazione alle grandi deviazioni

La funzione di tasso di Cramér è il negativo della trasformata di Legendre di $K_X$:

$$\Omega_X(u) = -\min_\lambda [K_X(\lambda) - \lambda u]$$

(Vedi [[Teoria delle grandi deviazioni]].)

## Connessioni

- Strumento per: [[Distribuzione chi-quadro]], [[Distribuzione Gamma]], [[Distribuzione Normale Multivariata]]
- Grandi deviazioni: [[Teoria delle grandi deviazioni]]
- Usato in: dimostrazione TLC (MMF II), dimostrazione teorema 2.4 (MatML)

## Fonti

- [[Dispense MatML — Galletti]] (§2.8, pp. 27-29)
- [[Dispense MMFII — Galletti]] (§1, pp. 2-14)
