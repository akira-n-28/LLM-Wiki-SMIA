---
tipo: concetto
titolo: Distribuzione F di Fisher-Snedecor
tag: [statistica, distribuzioni]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-04-30
---

# Distribuzione F di Fisher-Snedecor

Distribuzione del **rapporto** di due chi-quadro indipendenti, ciascuna divisa per i propri gradi di libertà.

## Costruzione

Siano `U ∼ χ²_m` e `V ∼ χ²_n` indipendenti. Allora:

$$
F = \frac{U/m}{V/n} \sim F_{m,n}
$$

## Densità

$$
f(x) = \frac{\Gamma\!\left(\frac{m+n}{2}\right) (m/n)^{m/2}\, x^{m/2 - 1}}{\Gamma(m/2)\Gamma(n/2)\,\left(1 + \frac{m}{n}x\right)^{(m+n)/2}}, \quad x > 0
$$

## Momenti

$$
\mathbb{E}[X] = \frac{n}{n-2}, \quad n > 2
$$

$$
\text{Var}(X) = \frac{2n^2(m+n-2)}{m(n-2)^2(n-4)}, \quad n > 4
$$

## Usi

- ANOVA (analisi della varianza): test F per confrontare modelli annidati.
- Test su rapporti di varianze.
- [[Modello lineare normale]]: confronto di modelli a complessità diverse.

## Collegamenti

- Costruita da: [[Distribuzione chi-quadro]] (rapporto)
- Indirettamente legata a: [[Distribuzione t-Student]] (ricorda: `t² ∼ F_{1,ν}`)
- Onomastica: [[Fisher, Ronald]], George Snedecor

## Fonti

- [[Dispense MatML — Galletti]] (def. 2.6 e teor. 2.5, p. 29)
