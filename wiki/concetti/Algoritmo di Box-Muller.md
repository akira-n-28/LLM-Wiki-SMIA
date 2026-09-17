---
tipo: concetto
titolo: Algoritmo di Box-Muller
tag: [probabilità, statistica-computazionale]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Algoritmo di Box-Muller

Metodo per generare **coppie di normali standard indipendenti** `X, Y ∼ N(0,1)` a partire da due uniformi `U_1, U_2 ∼ U(0,1)`.

## Derivazione

La densità congiunta di `(X, Y)` in coordinate cartesiane è:

$$
f_{X,Y}(x,y) = \frac{1}{2\pi} \exp\!\left(-\frac{x^2+y^2}{2}\right)
$$

Passando a coordinate polari `X = R cos Θ`, `Y = R sin Θ`, con Jacobiano `|J| = r`:

$$
f_{R,\Theta}(r,\theta) = \underbrace{\frac{1}{2\pi}}_{f_\Theta(\theta)} \cdot \underbrace{r e^{-r^2/2}}_{f_R(r)}
$$

Poiché la densità congiunta è il prodotto delle marginali, `R ⊥ Θ`:
- `Θ ∼ U(0, 2π)` → `Θ = 2πU_2`
- `R` ha densità `f_R(r) = r e^{-r^2/2}` → via [[Metodo della funzione inversa]]: `R = √{-2 log U_1}`

## Algoritmo

```
Input:  U₁, U₂ ∼ U(0,1) indipendenti
Output: X, Y  ∼ N(0,1) indipendenti

R ← √(-2 log U₁)
Θ ← 2π U₂
X ← R cos(Θ)
Y ← R sin(Θ)
```

## Efficienza

Genera **due** normali per coppia di uniformi — nessuno spreco.

## Caso multivariato

Per generare `X ∼ N(μ, Σ)`:
1. Fattorizzare `Σ = LL^T` (decomposizione di Cholesky).
2. Generare `Z = [Z_1, …, Z_n]^T` con `Z_i ∼ N(0,1)` i.i.d. (via Box-Muller).
3. Restituire `X = μ + LZ`.

## Derivazione dell'inversa radiale

La CDF di `R` è `F_R(r) = 1 - e^{-r^2/2}`. Invertendo: `R = √{-2 log(1-U)}`. Poiché `1-U ∼ U(0,1)`, si può usare direttamente `R = √{-2 log U}`.

## Connessione con la funzione generatrice dei momenti

Il fatto che `‖Z‖² = R² = -2 log U_1 ∼ χ²_1` per un'unica componente, e `‖Z‖² ∼ χ²_d` per il vettore `d`-dimensionale, si verifica via [[Funzione generatrice dei momenti]].

## Limitazione: discontinuità numerica

Se `U_1` è troppo vicino a 0, `log U_1` diverge. In pratica si clamp `U_1 ∈ (ε, 1)`.

## Alternativa: metodo di Marsaglia (polar)

Evita i calcoli di `sin` e `cos` (costosi) usando un accept-reject sull'unitario.

## Persone

[[Box, George]], [[Muller, Mervin]] — proposto nel 1958.

## Collegamenti

- Usato in: [[Metodi Monte Carlo]], campionamento dalla [[Distribuzione Normale Multivariata]]
- Si basa su: [[Metodo della funzione inversa]] (per la componente radiale), [[Generatore MRG]]
- MGF relata: [[Funzione generatrice dei momenti]]

## Fonti

- [[Dispense MatML — Galletti]] (§3.3, esempio 3.1, pp. 44-45)
