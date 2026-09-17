---
tipo: concetto
titolo: Bootstrap
tag: [ml, statistica, statistica-computazionale]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# Bootstrap (Ricampionamento)

Tecnica per stimare la distribuzione campionaria di una statistica **senza conoscere la vera distribuzione `f`**. Si approssima `f` con la **CDF empirica** del campione osservato, poi si simula da essa.

## Idea

Dato `τ = {x_1, …, x_N}` i.i.d. da `f` incognita: si generano `B` campioni bootstrap `τ*_b = {x*_{1,b}, …, x*_{N,b}}` estraendo **con reinserimento** da `τ`. Per ogni campione bootstrap si calcola la statistica di interesse `θ̂_b = T(τ*_b)`.

## Algoritmo

```
Dato: τ = {x₁, …, xₙ}
Per b = 1, …, B:
  Per t = 1, …, N:
    U ∼ U(0,1)
    I ← ⌈N·U⌉        (indice intero in {1,…,N})
    x*ₜ ← xᵢ
  τ*_b ← {x*₁, …, x*ₙ}
  θ̂_b ← T(τ*_b)
Distribuzione bootstrap: {θ̂₁, …, θ̂_B}
```

## Stime bootstrap formali

Dati i `B` valori bootstrap `θ̂_1*, …, θ̂_B*` e la loro media `θ̄* = (1/B) Σ_b θ̂_b*`:

$$
\widehat{\mathrm{Var}}(\hat\theta) = \frac{1}{B}\sum_{b=1}^B (\hat\theta_b^* - \bar\theta^*)^2
$$

$$
\widehat{\mathrm{Bias}}(\hat\theta) = \bar\theta^* - \hat\theta_{\mathrm{obs}}
$$

$$
\widehat{\mathrm{MSE}}(\hat\theta) = \widehat{\mathrm{Var}}(\hat\theta) + [\widehat{\mathrm{Bias}}(\hat\theta)]^2
$$

## Intervalli di confidenza bootstrap

**Metodo normale:** assume che `θ̂` sia approssimativamente normale con SE = `Ŝ* = √V̂ar(θ̂)`:

$$
\mathrm{CI} = \left[\hat\theta_{\mathrm{obs}} \pm z_{1-\alpha/2}\,\hat S^*\right]
$$

**Metodo percentile:** ordina `θ̂_1*, …, θ̂_B*` in ordine crescente; usa i quantili bootstrap direttamente:

$$
\mathrm{CI} = \left[\hat\theta^*_{(\lceil B\alpha/2\rceil)},\; \hat\theta^*_{(\lfloor B(1-\alpha/2)\rfloor)}\right]
$$

Il metodo percentile è preferibile quando la distribuzione di `θ̂` è asimmetrica; il metodo normale è più semplice ma richiede quasi-normalità.

## Esempio: quoziente di uniformi

`x_i = U_i/V_i` con `U_i, V_i ∼ U(0,1)`. Bootstrap permette di stimare la distribuzione della mediana `X̃` o della media `X̄` senza conoscerne la distribuzione analitica.

## Esempio: cammino aleatorio su grafo

Si simula un cammino aleatorio su un grafo (es. catena di Markov su stati discreti) e si stima `E[R]` (tempo di ritorno) e `E[C]` (costo medio per passo). Poiché la distribuzione di queste statistiche non è nota in forma chiusa, il bootstrap ricampiona le traiettorie osservate e stima Var e CI tramite i metodi sopra.

## Quando funziona

- Campione "grande": la CDF empirica approssima bene `f`.
- Statistiche regolari (differenziabili): il bootstrap è asintoticamente consistente.

## Limitazioni

- Non funziona bene per statistiche non regolari (es. massimo, percentili estremi).
- Non appropriato per dati dipendenti (serie temporali) — si usa il block bootstrap.
- Richiede che il campione sia rappresentativo della popolazione.

## Connessione con i Metodi Monte Carlo

Il bootstrap è un caso speciale di [[Metodi Monte Carlo]]: si usa la CDF empirica come distribuzione "di campionamento" e si generano campioni da essa tramite [[Generatore MRG]].

## Connessione con la stima del rischio

Il bootstrap può stimare l'errore di generalizzazione di un modello (alternativa a [[Cross-validation]]):
- `.632 Bootstrap`: combina bootstrap e training error per correggere l'ottimismo.
- Bootstrap è più costoso di CV ma può dare stime più stabili per campioni piccoli.

## Connessione con l'[[Intervallo di confidenza]]

Gli intervalli bootstrap hanno giustificazione frequentista (copertura asintotica `1-α`) anche per statistiche senza distribuzione campionaria nota in forma chiusa.

## Persone

Introdotto da [[Efron, Bradley]] (1979). Il nome viene dall'"alzarsi per i lacci degli stivali" (bootstrap), metafora dell'auto-aiuto senza risorse esterne.

## Connessione con i corsi

- [[Apprendimento statistico]]: bootstrap per la stima dell'errore di generalizzazione e del bias.
- [[Statistica inferenziale]]: intervalli di confidenza bootstrap.

## Collegamenti

- Caso speciale di: [[Metodi Monte Carlo]]
- Strumento: [[Generatore MRG]]
- Alternativa per stima del rischio: [[Cross-validation]], [[Ottimismo]]
- Stima di: varianza, bias, intervalli di confidenza

## Fonti

- [[Dispense MatML — Galletti]] (§3.11.1, algoritmo 7, pp. 55-58)
