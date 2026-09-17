---
tipo: concetto
titolo: Limite di una funzione
tag: [analisi, matematica, analisi-1]
cluster: analisi
fonti: 1
ultima-modifica: 2026-05-06
---

# Limite di una funzione

## Definizione topologica

Data $f:A\subset\mathbb{R}\to\mathbb{R}$ e $x_0$ punto di accumulazione per $A$, diciamo che:
$$\lim_{x\to x_0} f(x) = l \in \overline{\mathbb{R}}$$
se $\forall V$ intorno di $l$, $\exists U$ intorno di $x_0$ t.c. $f(x)\in V\ \forall x\in A\cap(U\setminus\{x_0\})$.

## Definizione ε-δ (caso $l, x_0 \in \mathbb{R}$)

$$\forall\varepsilon>0\ \exists\delta>0\ |\ |f(x)-l|<\varepsilon\ \forall x\in A,\, 0<|x-x_0|<\delta$$

## Proprietà fondamentali

**Unicità.** Se il limite esiste è unico.

**Limite destro/sinistro.** $\lim_{x\to x_0^+} f(x)$ e $\lim_{x\to x_0^-} f(x)$. Il limite bilaterale esiste $\Leftrightarrow$ i due limiti unilaterali coincidono.

**Algebra dei limiti.** Se $\lim_{x\to x_0} f(x)=l_1$ e $\lim_{x\to x_0} g(x)=l_2$:
$$\lim(f\pm g)=l_1\pm l_2,\quad \lim(fg)=l_1 l_2,\quad \lim\frac{f}{g}=\frac{l_1}{l_2}\ (l_2\neq 0)$$

**Permanenza del segno.** Se $l>0$ allora $\exists U$ intorno di $x_0$: $f(x)>0\ \forall x\in A\cap U$.

**Confronto.** Se $f_1(x)\leq f_2(x)$ in un intorno di $x_0$ allora $l_1\leq l_2$.

**Teorema dei due carabinieri (squeeze theorem).** Se $f_1\leq g\leq f_2$ vicino a $x_0$ e $\lim f_1 = \lim f_2 = l$, allora $\lim g = l$.

**Composizione.** Se $\lim_{x\to x_0} f(x)=y_0$ e $g$ è continua in $y_0$, allora $\lim_{x\to x_0} g(f(x))=g(y_0)$.

## Forme indeterminate

$\frac{0}{0}$, $\frac{\infty}{\infty}$, $0\cdot\infty$, $\infty-\infty$, $0^0$, $1^\infty$, $\infty^0$ — non applicare l'algebra dei limiti; usare o-piccoli, regola di L'Hôpital o cambio di variabile.

## Gerarchia degli infiniti (per $x\to+\infty$)

$$\log_a(x) \ll x^\alpha \ll a^x \ll x! \quad \forall \alpha>0,\ a>1$$

Ossia $\log_a x = o(x^\alpha)$ e $x^\alpha = o(a^x)$ per $x\to+\infty$.

## Connessioni

- Limiti notevoli e o-piccoli: [[Limiti notevoli]]
- Continuità: [[Continuità di una funzione]] (limite = valore della funzione)
- Derivata: [[Derivata]] (rapporto incrementale per $h\to 0$)
- Successioni: [[Successioni]] (limite di $(a_n)$ è un caso particolare)

## Fonti

- [[Dispense AnalisiI — Galletti]] (§2, pp. 29-59)
