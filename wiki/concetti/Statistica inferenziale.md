---
tipo: concetto
titolo: Statistica inferenziale
tag: [statistica, fondamenti]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-04-30
---

# Statistica inferenziale

Branca della statistica che, a partire da un campione, **inferisce informazioni sulla popolazione** da cui è stato estratto, quantificando l'incertezza dell'inferenza.

## Strumenti

- [[Intervallo di confidenza]]: intervallo `[θ₁, θ₂]` tale che `P(θ₁ < θ < θ₂) = 1-α`.
- [[Test di ipotesi]]: si formula un'ipotesi nulla `H₀` e si cercano nei dati evidenze contro di essa (p-value).
- Distribuzioni di riferimento: [[Distribuzione t-Student]] per la media, [[Distribuzione chi-quadro]] per la varianza, [[Distribuzione F di Fisher-Snedecor]] per il rapporto di varianze.

## Logica dell'evidenza

> Se non si trova evidenza contraria sufficientemente forte, l'ipotesi nulla **non è né vera né falsa**: semplicemente "si fallisce nel rifiutare H₀". (cfr. [[Dispense MatML — Galletti]], oss. 1.3)

Questo principio è cruciale: il test cerca **prove contro** H₀, non a favore.

## Collegamenti

- Si contrappone a: [[Statistica descrittiva]]
- Fondamento per: [[Apprendimento statistico]], [[Apprendimento Bayesiano]]
- Le distribuzioni della statistica t-Student/χ² ricompaiono come posterior nel framework Bayesiano

## Fonti

- [[Dispense MatML — Galletti]] (def. 1.2, p. 2; sezione 1.3, pp. 5-9)
