---
tipo: concetto
titolo: Metodo accept-reject
tag: [probabilità, statistica-computazionale]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Metodo accept-reject (Acceptance-Rejection)

Tecnica di campionamento per distribuzioni **difficili da trattare direttamente**. Richiede solo di saper valutare la densità target `f(x)` e di avere una densità ausiliaria `g(x)` (facilmente campionabile) con:

$$
f(x) \leq C \cdot g(x) \quad \forall x, \quad C \geq 1
$$

## Algoritmo

1. Estrai `X ∼ g(·)`.
2. Costruisci `Y ∼ U(0, C·g(X))` (campionamento uniforme sotto la curva maggiorante).
3. Se `Y ≤ f(X)`: accetta `X` come campione da `f`.  
   Altrimenti: scarta e ricomincia.

## Efficienza

La probabilità di accettazione è:

$$
P(\text{accetta}) = \frac{\int f(x)\,dx}{\int Cg(x)\,dx} = \frac{1}{C}
$$

Più `C` è vicino a 1, più `g` approssima `f` e più l'algoritmo è efficiente. Un `C` grande comporta molti rifiuti.

## Proprietà chiave

- Non richiede la costante di normalizzazione di `f` (purché si conosca una versione non normalizzata `f̃(x) = Z f(x)`): basta avere `f̃(x) ≤ C' g(x)`.
- Genera campioni **esattamente** distribuiti secondo `f` (non in modo approssimato come MCMC).
- Produce campioni **indipendenti** (a differenza delle catene di Markov).

## Interpretazione geometrica

Si genera un punto `(X, Y)` uniformemente nell'area sotto `Cg(x)`. Si accetta solo se `(X, Y)` cade anche sotto `f(x)`. Le ascisse accettate sono distribuite secondo `f`.

## Quando usarlo

- `f` non ha CDF invertibile (→ non si può usare [[Metodo della funzione inversa]]).
- `f` è nota a meno di costante di normalizzazione.
- Si può costruire un maggiorante `Cg` efficiente.

## Limitazioni

- In alta dimensionalità, `C` diventa enorme (il rapporto `f/g` oscilla molto), rendendo l'algoritmo impraticabile. In `ℝ^d` si preferisce [[Metropolis-Hastings]].
- Scegliere `g` ottimale richiede conoscenza di `f`.

## Esempio

Per campionare dalla distribuzione Beta: `f(x) ∝ x^{a-1}(1-x)^{b-1}` su `[0,1]`, si usa `g = U(0,1)` e `C = max f(x)`.

## Collegamento con Metropolis-Hastings

M-H generalizza accept-reject al caso MCMC: la probabilità di accettazione `α(x,y) = min(f(y)q(x|y)/(f(x)q(y|x)), 1)` recupera la logica di accettazione/rifiuto ma produce campioni correlati (catena di Markov). L'indipendenza è sacrificata per la flessibilità.

## Collegamento con l'apprendimento Bayesiano

Campionare dalla posterior `g(θ|τ) ∝ g(τ|θ) g(θ)` è spesso il collo di bottiglia computazionale del [[Apprendimento Bayesiano]]. Accept-reject è praticabile solo quando prior e likelihood danno un maggiorante efficiente.

## Connessione con l'integrazione Monte Carlo

Accept-reject può essere visto come una stima MC del rapporto aree `1/C`. Il metodo di campionamento è duale alla stima di integrali.

## Connessione con importanza campionata

Una variante è **importance sampling**: invece di rifiutare, si pesano i campioni con `w(x) = f(x)/(Cg(x))`. Equivalente in aspettativa, più efficiente per stime di integrali.

## Collegamenti

- Alternativa a: [[Metodo della funzione inversa]] (quando CDF non è invertibile)
- Meno scalabile di: [[Metropolis-Hastings]] in alta dimensionalità
- Usato in: [[Metodi Monte Carlo]]
- Basato su: [[Generatore MRG]]

## Fonti

- [[Dispense MatML — Galletti]] (§3.5, pp. 46-47)
