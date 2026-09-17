---
tipo: concetto
titolo: Distribuzione Normale Multivariata
tag: [probabilità, statistica, ml]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Distribuzione Normale Multivariata

Generalizzazione della distribuzione normale al caso `d`-dimensionale. Un vettore aleatorio `X ∈ ℝ^d` segue una normale multivariata con media `μ` e matrice di covarianza `Σ` (definita positiva):

$$
X \sim \mathcal{N}(\mu, \Sigma)
$$

con densità:

$$
f_X(x) = \frac{1}{\sqrt{(2\pi)^d \det\Sigma}} \exp\!\left(-\frac{1}{2}(x - \mu)^T \Sigma^{-1} (x - \mu)\right)
$$

## Costruzione via trasformazione lineare

Si parte da `Z ∼ N(0, I_d)` (componenti indipendenti):

$$
f_Z(z) = (2\pi)^{-d/2} \exp\!\left(-\tfrac{1}{2} z^T z\right)
$$

Fattorizzando `Σ = BB^T` (decomposizione di Cholesky), si pone `X = μ + BZ`. Per il teorema di trasformazione:

$$
f_X(x) = \frac{1}{|\det B|} f_Z(B^{-1}(x-\mu)) \quad \Rightarrow \quad X \sim \mathcal{N}(\mu, BB^T = \Sigma)
$$

### Teorema: trasformazioni affini

Sia `Z` un vettore aleatorio con media `μ_Z` e covarianza `Σ_Z`. Allora `X = μ + AZ` ha:
- Media: `μ_X = μ + A μ_Z`
- Covarianza: `Σ_X = A Σ_Z A^T`

## Proprietà chiave

- Le **trasformazioni affini** di vettori normali sono ancora normali.
- Le **distribuzioni marginali** di un vettore normale sono normali.
- Le **distribuzioni condizionate** rimangono normali.

Queste proprietà rendono la normale multivariata ideale per modelli analiticamente trattabili (modello lineare normale, apprendimento Bayesiano con prior gaussiano).

## Teorema fondamentale: connessione con χ²

**Teorema 2.4 (MatML).** Sia `X ∼ N(μ, Σ)` con `det Σ > 0`. Allora:

$$
(X - \mu)^T \Sigma^{-1} (X - \mu) \sim \chi^2_d
$$

**Dimostrazione.** Poniamo `Y = B^{-1}(X - μ) = Z`, quindi `Z ∼ N(0, I_d)` e:

$$
(X-\mu)^T \Sigma^{-1} (X-\mu) = Z^T Z = \sum_{i=1}^d Z_i^2 \sim \chi^2_d
$$

La seconda uguaglianza segue dalla [[Funzione generatrice dei momenti]] della somma di quadrati di normali standard.

## Modello lineare normale

Nel [[Modello lineare normale]], `Y = Xβ + σZ`, `Z ∼ N(0, I_n)`, il vettore risposta è:

$$
Y \sim \mathcal{N}(X\beta,\, \sigma^2 I_n)
$$

## Decomposizione di Cholesky

Per generare campioni da `N(μ, Σ)` numericamente: fattorizza `Σ = LL^T` (Cholesky), genera `Z ∼ N(0, I_d)`, restituisci `μ + LZ`.

## Chi-quadro non centrale

Se `X ∼ N(μ, I_n)` con `μ ≠ 0`:

$$
\|X\|^2 \sim \chi^2_n(\|\mu\|^2) \qquad \text{(chi-quadro non centrale, parametro } \|\mu\|^2\text{)}
$$

## Collegamenti

- Componente di: [[Modello lineare normale]]
- Connessa a: [[Distribuzione chi-quadro]] (via forma quadratica)
- Generata via: [[Funzione generatrice dei momenti]] (dimostrazione)
- Prior in: [[Apprendimento Bayesiano]] (prior gaussiano su μ)

## Fonti

- [[Dispense MatML — Galletti]] (§2.8, teorema 2.4, pp. 26-29)
