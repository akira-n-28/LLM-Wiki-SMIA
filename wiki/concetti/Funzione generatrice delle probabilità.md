---
tipo: concetto
titolo: Funzione generatrice delle probabilità
tag: [probabilità, analisi, processi-stocastici]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Funzione generatrice delle probabilità (PGF)

Data una variabile aleatoria `T ∈ ℕ` con `P(T = n) = pₙ ≥ 0` e `Σpₙ = 1`, la **funzione generatrice delle probabilità** è:

$$
G(s) = E\!\left[s^T\right] = \sum_{n=0}^{\infty} p_n s^n, \qquad |s| \leq 1
$$

## Proprietà fondamentali

- `G(0) = p₀ = P(T = 0)`
- `G(1) = 1` (somma delle probabilità)
- `|G(s)| ≤ 1` per `|s| ≤ 1` (convergenza assoluta)

## Estrazione dei momenti

Derivando rispetto a `s` e prendendo il limite per `s → 1⁻`:

$$
E[T] = \lim_{s \to 1^-} G'(s) = \sum_{n=1}^\infty n\,p_n
$$

$$
\mathrm{Var}[T] = \lim_{s\to 1^-} G''(s) - \left(\lim_{s\to 1^-} G'(s)\right)^2 + \lim_{s\to 1^-} G'(s)
$$

Perché: `G''(s) = Σ n(n-1)pₙsⁿ⁻²` → `G''(1) = E[T²] - E[T]`.

## Convoluzione e somma di v.a. indipendenti

Se `T₁` e `T₂` sono indipendenti: `G_{T₁+T₂}(s) = G_{T₁}(s) · G_{T₂}(s)`.

## Applicazione: tempo di ritorno nella passeggiata

Per la [[Passeggiata aleatoria]], si definisce `H(s) = Σ h(k)s^k` dove `h(n) = P(Xₙ = 0 | X₀ = 0)`:

$$
H(s) = (1 - 4pqs^2)^{-1/2}, \quad |s| < \frac{1}{2\sqrt{pq}}
$$

La PGF del tempo di primo ritorno `GT(s)` soddisfa `GT(s)·H(s) = H(s) - 1`.

## Differenza dalla funzione generatrice dei momenti

La [[Funzione generatrice dei momenti]] `M(t) = E[e^{tX}]` usa `e^t` invece di `s`; le due sono legate da `M(t) = G(eᵗ)` per v.a. intere non negative.

## Connessione con i corsi

- [[Processi Stocastici]]: §4, usata per analizzare il ritorno nell'origine della passeggiata aleatoria.
- [[Distribuzione di Poisson]]: la PGF di `Poi(λ)` è `G(s) = e^{λ(s-1)}`.

## Fonti

- [[Dispense Processi Stocastici — Galletti]] (§4, pp. 13-15)
