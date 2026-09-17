---
tipo: concetto
titolo: Disuguaglianza di Cauchy-Schwarz
tag: [analisi, algebra-lineare, probabilità, matematica]
cluster: analisi
fonti: 2
ultima-modifica: 2026-05-06
---

# Disuguaglianza di Cauchy-Schwarz

## Enunciato in $\mathbb{R}^N$

$$|\langle x, y \rangle| \leq \|x\|_2 \cdot \|y\|_2$$

con uguaglianza se e solo se $x$ e $y$ sono linearmente dipendenti.

**Dimostrazione:** considera il polinomio $p(t) = \|x + ty\|^2 = \|x\|^2 + 2t\langle x,y\rangle + t^2\|y\|^2 \geq 0$. Il discriminante deve essere $\leq 0$: $4\langle x,y\rangle^2 - 4\|x\|^2\|y\|^2 \leq 0$.

## Enunciato per variabili aleatorie

$$|E[XY]| \leq \sqrt{E[X^2] \cdot E[Y^2]}$$

Equivalentemente per il coefficiente di correlazione: $|\rho(X,Y)| \leq 1$.

## Enunciato per spazi $L^2$

Per $f, g \in L^2(E)$:
$$\left|\int_E f \cdot g\right| \leq \|f\|_{L^2} \cdot \|g\|_{L^2}$$

Questo è il caso $p=q=2$ della disuguaglianza di [[Spazi Lp|Hölder]].

## Connessioni

- In $\mathbb{R}^N$: [[Spazio metrico]] (prodotto scalare, norma $\|\cdot\|_2$)
- In $L^p$: [[Spazi Lp]] (caso speciale di Hölder con $p=q=2$)
- In probabilità: [[Varianza e covarianza]] (correlazione $|\rho| \leq 1$)
- Persona: [[Cauchy]] — [[Schwarz, Hermann Amandus]]

## Fonti

- [[Dispense AnalisiII — Galletti]] (§2, p. 27-37)
- [[Dispense Machine Learning — Galletti]] (§7, prodotto scalare)
