---
tipo: concetto
titolo: Metodo della funzione inversa
tag: [probabilità, statistica-computazionale]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Metodo della funzione inversa

Tecnica per generare campioni da una distribuzione continua arbitraria `X ∼ F_X` sfruttando la **trasformazione quantile**. Richiede che la CDF `F_X` sia strettamente crescente e invertibile analiticamente.

## Principio

Se `U ∼ U(0,1)`, allora `X = F_X^{-1}(U)` ha esattamente la distribuzione desiderata. Dimostrazione:

$$
P[F_X^{-1}(U) \leq x] = P[U \leq F_X(x)] = F_X(x)
$$

L'ultima uguaglianza usa che la CDF di una `U(0,1)` è `P(U ≤ u) = u`.

## Algoritmo

```
Input:  CDF F_X, una realizzazione u ∼ U(0,1)
Output: x ∼ F_X

x ← F_X⁻¹(u)
```

## Esempio: distribuzione di Rayleigh

Densità `f_R(r) = r e^{-r²/2}`, `r > 0`. CDF:

$$
F_R(r) = 1 - e^{-r^2/2}
$$

Invertendo (`u = F_R(r)`):

$$
R = \sqrt{-2\log(1-u)} \approx \sqrt{-2\log U} \quad \text{(per simmetria di U)}
$$

Questo è esattamente il generatore radiale dell'[[Algoritmo di Box-Muller]].

## Esempio: distribuzione esponenziale

`f(x) = λ e^{-λx}`, `F(x) = 1 - e^{-λx}`. Inversa:

$$
X = -\frac{1}{\lambda}\log(1 - U) = -\frac{\log U}{\lambda}
$$

## Limiti

- Richiede `F_X^{-1}` in forma chiusa — spesso non disponibile.
- Per distribuzioni complesse (normale, t, gamma) si usano approssimazioni numeriche o metodi alternativi.

## Alternativa quando F_X⁻¹ non è disponibile

- [[Metodo accept-reject]]: non richiede la CDF, solo un maggiorante.
- [[Metropolis-Hastings]]: non richiede nemmeno la normalizzazione.

## Teorema di probabilità integrale

La trasformazione `U = F_X(X)` è l'opposto: se `X ∼ F_X` continua, allora `F_X(X) ∼ U(0,1)`. Questo risultato è la base del metodo inverso e ha applicazioni in teoria statistica (test di aderenza).

## Connessione con il campionamento MC

Tutti i [[Metodi Monte Carlo]] usano questo principio come blocco base: si trasformano uniformi in campioni dalla distribuzione desiderata.

## Collegamenti

- Usato in: [[Algoritmo di Box-Muller]] (caso Rayleigh), [[Metodi Monte Carlo]]
- Alternativa: [[Metodo accept-reject]], [[Metropolis-Hastings]]
- Basato su: [[Generatore MRG]] (per le uniformi)

## Fonti

- [[Dispense MatML — Galletti]] (§3.4, esempio 3.2, pp. 45-46)
