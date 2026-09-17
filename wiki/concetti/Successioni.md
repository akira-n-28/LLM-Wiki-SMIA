---
tipo: concetto
titolo: Successioni
tag: [analisi, matematica, analisi-1]
cluster: analisi
fonti: 1
ultima-modifica: 2026-05-06
---

# Successioni reali e serie numeriche

## Successioni

Una **successione reale** è una funzione $a:\mathbb{N}\to\mathbb{R}$, scritta $(a_n)_{n\in\mathbb{N}}$.

**Convergenza.** $\lim_{n\to+\infty}a_n=l$ se $\forall\varepsilon>0\ \exists N\in\mathbb{N}:\ |a_n-l|<\varepsilon\ \forall n>N$.

**Successioni monotone.** Se $(a_n)$ è crescente, $\lim a_n = \sup\{a_n:n\in\mathbb{N}\}$ (finito o $+\infty$).

**Sottosuccessioni.** Data $h:\mathbb{N}\to\mathbb{N}$ strettamente crescente, $\tilde{a}_n=a_{h(n)}$ è una sottosuccessione. Se $a_n\to l$ allora ogni sottosuccessione converge a $l$ (non vale il viceversa: $(-1)^n$).

**Teorema di Bolzano-Weierstrass.** Ogni successione **limitata** ha una sottosuccessione convergente.

*Dimostrazione:* per bisezione iterata dell'intervallo $[-M,M]$: si costruisce una catena di intervalli inscatolati $I_0\supset I_1\supset\ldots$ con $|I_k|=2M/2^k$ e si estrae la sottosuccessione; il limite è l'unico punto comune.

## Serie numeriche

Data $(a_k)_{k\in\mathbb{N}}$, la **serie** è $\sum_{k=0}^\infty a_k := \lim_{n\to+\infty} s_n$ con $s_n=\sum_{k=0}^n a_k$ (somme parziali).

**Serie geometrica.** $\sum_{k=0}^\infty r^k = \frac{1}{1-r}$ se $|r|<1$; diverge se $|r|\geq 1$.

**Condizione necessaria di convergenza.** $\sum a_k < +\infty \Rightarrow a_k\to 0$ (non sufficiente: serie armonica).

**Serie armonica generalizzata.** $\sum_{k=1}^\infty \frac{1}{k^\alpha}$: converge $\Leftrightarrow \alpha>1$.

## Criteri di convergenza

| Criterio | Enunciato |
|---|---|
| **Confronto** | $0\leq a_k\leq b_k$: se $\sum b_k<+\infty$ allora $\sum a_k<+\infty$; se $\sum a_k=+\infty$ allora $\sum b_k=+\infty$ |
| **Confronto asintotico** | $a_k/b_k\to l\in(0,+\infty)$: $\sum a_k$ e $\sum b_k$ hanno lo stesso carattere |
| **Rapporto** | $a_{k+1}/a_k\to r$: converge se $r<1$, diverge se $r>1$, non si applica se $r=1$ |
| **Leibniz** | Serie alternante $\sum(-1)^k a_k$ con $a_k\geq 0$ decrescente $\to 0$: converge |

**Convergenza assoluta.** $\sum|a_k|<+\infty \Rightarrow \sum a_k$ converge, e $|\sum a_k|\leq\sum|a_k|$.

## Connessioni

- Limite di successione vs limite di funzione: [[Limite di una funzione]]
- Criteri per serie si usano nella convergenza della serie di Taylor: [[Polinomi di Taylor]]
- Relazione serie/integrali impropri (criterio integrale di Cauchy): [[Integrale di Riemann]]

## Fonti

- [[Dispense AnalisiI — Galletti]] (§3, pp. 60-87)
