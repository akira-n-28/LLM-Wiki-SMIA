---
tipo: concetto
titolo: Spazi Lp
tag: [analisi, matematica, analisi-2, analisi-funzionale]
cluster: analisi
fonti: 1
ultima-modifica: 2026-05-06
---

# Spazi $L^p$

## Definizione

Sia $E\subseteq\mathbb{R}^N$ misurabile e $p\geq 1$. Lo spazio $L^p(E)$ è:
$$L^p(E) = \left\{f:E\to\bar{\mathbb{R}}\ \middle|\ f \text{ misurabile},\ \int_E|f(x)|^p\,dx<+\infty\right\}$$

Si definisce la relazione di equivalenza $f\sim g\Leftrightarrow f=g$ quasi ovunque. Lo spazio $L^p(E)$ è l'insieme quoziente.

La **norma** è:
$$\|f\|_{L^p(E)} = \left(\int_E|f(x)|^p\,dx\right)^{1/p}$$

## Proprietà algebriche

$L^p(E)$ è un **sottospazio vettoriale**: se $f,g\in L^p$ e $c\in\mathbb{R}$, allora $cf,f+g\in L^p$.

La norma è ben definita (grazie all'equivalenza q.o.): $\|f\|_{L^p}=0\Leftrightarrow f=0$ in $L^p$.

## Disuguaglianze fondamentali

**Esponenti coniugati.** $p,q\in(1,+\infty)$ sono coniugati se $\frac{1}{p}+\frac{1}{q}=1$.

**Disuguaglianza di Young.** Per $a,b\geq 0$ e $p,q$ coniugati:
$$ab \leq \frac{a^p}{p}+\frac{b^q}{q}$$
(con uguaglianza $\Leftrightarrow a^p=b^q$).

**Disuguaglianza di Hölder.** Se $f\in L^p(E)$, $g\in L^q(E)$ con $p,q$ coniugati:
$$\int_E|f(x)g(x)|\,dx \leq \|f\|_{L^p}\|g\|_{L^q}$$

*Dimostrazione:* applicare Young a $a=|f(x)|/\|f\|_{L^p}$ e $b=|g(x)|/\|g\|_{L^q}$ e integrare.

**Disuguaglianza di Minkowski** (triangolare in $L^p$):
$$\|f+g\|_{L^p} \leq \|f\|_{L^p}+\|g\|_{L^p}$$

*Dimostrazione:* $\int|f+g|^p\leq\int|f+g|^{p-1}|f|+\int|f+g|^{p-1}|g|$, poi Hölder con esponenti $(p,q)$ su ciascun termine.

## $L^\infty$ e caso limite

$$L^\infty(E) = \{f\ \text{misurabile}\ |\ \exists K>0:\ |f(x)|\leq K\ \text{q.o.}\}$$
$$\|f\|_{L^\infty} = \inf\{K>0: |f|\leq K\ \text{q.o.}\}$$

Hölder si estende: se $f\in L^1$ e $g\in L^\infty$, allora $\int|fg|\leq\|f\|_{L^1}\|g\|_{L^\infty}$ (con la convenzione $1/\infty=0$).

## Completezza

**Teorema di Fischer-Riesz.** Per ogni $p\in[1,+\infty]$, $(L^p(E),\|\cdot\|_{L^p})$ è uno **spazio di Banach** (spazio normato completo).

**Convergenza in $L^p$.** $f_n\to f$ in $L^p$ significa $\|f_n-f\|_{L^p}\to 0$, che è più forte della convergenza puntuale ma non implica né è implicata da essa.

*Esempio.* $f_n=\sqrt{n}\,\chi_{[0,1/n]}$: $f_n\to 0$ puntualmente, ma $\|f_n\|_{L^2}=1\not\to 0$, quindi $f_n\not\to 0$ in $L^2$.

## Inclusioni tra spazi $L^p$

Su un dominio $E$ di misura finita ($m(E)<+\infty$): $L^q(E)\subseteq L^p(E)$ per $p\leq q$ (via Hölder).

Su un dominio di misura infinita non vale in generale: $f(x)=1/x\in L^p((1,+\infty))$ per $p>1$ ma $\notin L^1$.

## Connessioni

- Costruito su: [[Integrale di Lebesgue]] (misura, funzioni misurabili)
- Spazio metrico: [[Spazio metrico]] (Banach è spazio normato completo)
- Applicazioni in ML: $L^2$ è lo spazio naturale delle funzioni di perdita quadratica, $L^1$ per MAE
- Collegamento a probabilità: $L^2(\Omega)$ contiene le v.a. a varianza finita ([[Varianza e covarianza]])

## Fonti

- [[Dispense AnalisiII — Galletti]] (§5, pp. 113-117)
