---
tipo: concetto
titolo: Test di ipotesi
tag: [statistica, inferenza]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-04-30
---

# Test di ipotesi

Procedura per verificare se i dati forniscono **evidenza contro** un'ipotesi sul valore di un parametro.

## Struttura

1. **Ipotesi nulla** `H₀`: ipotesi di partenza (es. `μ_M = μ_F`, "il farmaco non ha effetto").
2. **Ipotesi alternativa** `H₁`: la negazione (a una o due code).
3. **Statistica test**: una funzione del campione la cui distribuzione sotto `H₀` è nota (es. `T = (x̄ - μ₀)/(s/√n) ∼ tₙ₋₁`).
4. **p-value**: probabilità, sotto `H₀`, di osservare un valore estremo come quello campionario.
5. **Decisione**: se p-value `< α` (es. 0.05), si **rifiuta** H₀.

## Logica dell'evidenza (cruciale)

> L'obiettivo non è dimostrare che H₀ sia vera, ma cercare evidenza contro di essa.

Se non si trova evidenza, **non si dimostra H₀**: semplicemente "si fallisce nel rifiutarla". Asimmetria fondamentale.

## Test a due code

Per `H₁: μ ≠ μ₀`, si rifiuta se `|T| > t_{α/2, n-1}`. Le due code hanno area `α/2` ciascuna.

$$
P(T > t_{\alpha/2,\,n-1}) = \alpha/2
$$

α più piccolo ⇒ code più piccole ⇒ richiesta di evidenza più estrema ⇒ maggior **confidenza** `1-α`.

## Esempio (test farmaco colesterolo)

Riduzione media `x̄ = 14.8` mg/dL, `s = 6.4`, `n = 50`. Sotto `H₀: μ = 0`:

$$
T = \frac{14.8}{6.4/\sqrt{50}} \approx 16.35 \gg t_{0.995,\,49} \approx 2.678
$$

p-value tendente a zero ⇒ rifiuto netto di `H₀`.

## Collegamenti

- Strumento di: [[Statistica inferenziale]]
- Distribuzioni di riferimento: [[Distribuzione t-Student]], [[Distribuzione chi-quadro]], [[Distribuzione F di Fisher-Snedecor]]
- Duale di: [[Intervallo di confidenza]]

## Fonti

- [[Dispense MatML — Galletti]] (def. 1.10 e oss. 1.3-1.4, pp. 7-8)
