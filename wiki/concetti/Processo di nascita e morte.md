---
tipo: concetto
titolo: Processo di nascita e morte
tag: [probabilità, processi-stocastici, catene-di-markov]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Processo di nascita e morte

Classe speciale di [[Catena di Markov]] in cui le transizioni sono permesse solo tra stati **adiacenti**: dallo stato `i` si può andare a `i+1` ("nascita"), `i-1` ("morte"), o restare in `i`. La matrice di transizione soddisfa `Pᵢⱼ = 0` se `|i-j| ≥ 2`.

```
1 → 2 → 3 → ⋯ → N
  ↩   ↩   ↩       ↩
```

## Distribuzione stazionaria via bilancio dettagliato

I processi di nascita e morte soddisfano le **equazioni del [[Bilancio dettagliato]]**:

$$
\pi_i P_{i,i+1} = \pi_{i+1} P_{i+1,i}
$$

Questo permette di trovare `π` ricorsivamente: partendo da `π₁ = a > 0`:

$$
\pi_i = a \prod_{\ell=1}^{i-1} \frac{P_{\ell,\ell+1}}{P_{\ell+1,\ell}}
$$

dove `a` è la costante di normalizzazione determinata da `Σπᵢ = 1` (se la somma converge).

## Versione a tempo continuo

Con tassi di salto `λ(i)` (nascita) e `µ(i)` (morte), la matrice generatrice è:

$$
Q_{i,i+1} = \lambda(i), \quad Q_{i,i-1} = \mu(i), \quad Q_{ii} = -(\lambda(i) + \mu(i))
$$

La distribuzione stazionaria soddisfa `π(i)λ(i) = π(i+1)µ(i+1)`.

## Processo di Poisson come caso speciale

Il [[Processo di nascita e morte|processo di Poisson]] a intensità `λ` è un processo di nascita pura con `λ(i) = λ` (costante) e `µ(i) = 0`. Gli stati sono `N = 0, 1, 2, …` e rappresentano il numero di eventi accumulati.

## Equazione logistica

Nel limite continuo (molti individui), il processo di nascita e morte con `λ(i) ∝ i` e `µ(i) ∝ i²` si approssima con:

$$
x'(t) = \lambda x(t) - \mu x(t)^2
$$

L'equilibrio stabile è `x = λ/µ` (capacità portante). Soluzione esatta: `x(t) = λx₀ / (µx₀ + (λ-µx₀)e^{-λt})`.

## Connessione con i corsi

- [[Processi Stocastici]]: §5.1, nucleo teorico del corso per processi a tempo continuo.
- [[Bilancio dettagliato]]: la condizione di bilancio dettagliato è **necessaria e sufficiente** per questi processi.
- [[Distribuzione esponenziale]]: i tempi di permanenza in ogni stato sono Exp(λ(i)+µ(i)).

## Fonti

- [[Dispense Processi Stocastici — Galletti]] (§5.1, §5.2.3, pp. 18-24)
