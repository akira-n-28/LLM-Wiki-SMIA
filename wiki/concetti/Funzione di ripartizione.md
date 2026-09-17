---
tipo: concetto
titolo: Funzione di ripartizione
aliases: ["CDF", "Cumulative Distribution Function"]
tag: [probabilità, fondamenti]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-06
---

# Funzione di ripartizione (CDF)

Per una [[Variabile aleatoria]] $X$, la **funzione di ripartizione** (Cumulative Distribution Function, CDF) è:

$$
F_X(x) = P(X \leq x), \qquad x \in \mathbb{R}
$$

Caratterizza completamente la distribuzione di $X$: due v.a. con la stessa CDF hanno la stessa legge.

## Proprietà fondamentali

1. **Monotonia non decrescente:** $x \leq y \Rightarrow F_X(x) \leq F_X(y)$.
2. **Limiti:** $\lim_{x \to -\infty} F_X(x) = 0$ e $\lim_{x \to +\infty} F_X(x) = 1$.
3. **Continuità a destra:** $\lim_{y \to x^+} F_X(y) = F_X(x)$ (in molte fonti italiane si usa la convenzione opposta).
4. **Salti = masse di probabilità:** $P(X = x) = F_X(x) - F_X(x^-)$. La CDF è continua sse $X$ non ha atomi.

## Caso discreto vs continuo

- **Discreto:** $F_X(x) = \sum_{y \leq x} P(X = y)$. È una **funzione a scalini** con salti pari alle masse $P(X = x)$.
- **Continuo:** $F_X(x) = \int_{-\infty}^x f_X(t)\, dt$ con $f_X$ densità di probabilità. $F_X$ è continua e q.o. derivabile, $F_X'(x) = f_X(x)$.
- **Misto:** ammesso (es. $X$ con un atomo in 0 e densità altrove).

## Calcolo di probabilità da CDF

$$
P(a < X \leq b) = F_X(b) - F_X(a)
$$
$$
P(X > x) = 1 - F_X(x)
$$
$$
P(X = x) = F_X(x) - F_X(x^-) \quad \text{(salto in } x\text{)}
$$

## Funzione di ripartizione congiunta

Per $\mathbf{X} = (X_1, \ldots, X_n)$:

$$
F_\mathbf{X}(x_1, \ldots, x_n) = P(X_1 \leq x_1, \ldots, X_n \leq x_n)
$$

**Marginale:** $F_{X_1}(x_1) = \lim_{x_2, \ldots, x_n \to \infty} F_\mathbf{X}(x_1, \ldots, x_n)$.

**Indipendenza:** $X_1, \ldots, X_n$ indipendenti $\iff F_\mathbf{X}(x_1, \ldots, x_n) = \prod_i F_{X_i}(x_i)$.

## Quantili

Il **quantile** di ordine $q \in (0, 1)$ è $F_X^{-1}(q) = \inf\{x : F_X(x) \geq q\}$. Per $F_X$ continua e strettamente crescente, è l'inversa.

**Mediana:** $F_X^{-1}(1/2)$. **Quartili:** $F_X^{-1}(1/4), F_X^{-1}(3/4)$.

## Trasformazione integrale

**Universal Probability Integral Transform:** se $F_X$ è continua, $U = F_X(X) \sim \mathrm{Unif}(0, 1)$. Da qui il [[Metodo della funzione inversa]] per simulare $X$: parti da $U$ uniforme, calcola $X = F_X^{-1}(U)$.

## Empirica e Glivenko-Cantelli

La **CDF empirica** di un campione $X_1, \ldots, X_n$ è:
$$
\hat F_n(x) = \frac{1}{n} \sum_{i=1}^n \mathbf{1}_{\{X_i \leq x\}}
$$

**Teorema di Glivenko-Cantelli:** $\sup_x |\hat F_n(x) - F_X(x)| \to 0$ quasi certamente per $n \to \infty$. Il "fundamental theorem of statistics" — la CDF empirica converge uniformemente alla vera CDF.

## Connessioni

- Densità: [[Variabile aleatoria]] (caso continuo: $F_X' = f_X$)
- Quantili: [[Statistica descrittiva]] (mediana, quartili, percentili)
- Stima: [[Stimatore]] (CDF empirica come stimatore non parametrico)
- Simulazione: [[Metodo della funzione inversa]]
- Teorema centrale: [[Legge dei Grandi Numeri]] (Glivenko-Cantelli è "uniforme")

## Fonti

- [[Dispense ProbStat — Galletti]] (§2.4, §5)
