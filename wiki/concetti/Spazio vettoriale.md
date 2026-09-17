---
tipo: concetto
titolo: Spazio vettoriale
tag: [algebra-lineare, matematica]
cluster: algebra
fonti: 2
ultima-modifica: 2026-05-05
---

# Spazio vettoriale

Un **spazio vettoriale** $V$ su un **campo** $K$ (tipicamente $\mathbb{R}$ o $\mathbb{C}$) è un insieme di elementi detti *vettori*, dotato di addizione $+$ e moltiplicazione per scalare $K \times V \to V$, che soddisfa:

| Proprietà | Formula |
|---|---|
| Commutatività | $u + v = v + u$ |
| Associatività somma | $u + (v + w) = (u + v) + w$ |
| Associatività scalare | $(ab)v = a(bv)$ |
| Elemento neutro | $\exists\, 0 \in V : v + 0 = v$ |
| Inverso additivo | $\forall v\, \exists\, w : v + w = 0$ |
| Neutro moltiplicativo | $1 \cdot v = v$ |
| Distributività | $a(u+v) = au + av$, $(a+b)v = av + bv$ |

## Esempi

| Spazio | Campo | Elementi |
|---|---|---|
| $K^n$ | $K$ | $n$-uple $(x_1,\ldots,x_n)$ |
| $M_{m,n}(K)$ | $K$ | matrici $m \times n$ a coefficienti in $K$ |
| $K_t[x] = \{p : \deg p \leq t\}$ | $K$ | polinomi di grado $\leq t$ |
| $C([a,b],\mathbb{R})$ | $\mathbb{R}$ | funzioni continue su $[a,b]$ |

In $M_{m,n}(K)$ la base canonica ha $mn$ elementi $E_{ij}$ (1 in posizione $(i,j)$, 0 altrove); $\dim M_{m,n} = mn$.
In $K_t[x]$ la base canonica è $\{1, x, x^2, \ldots, x^t\}$; $\dim K_t[x] = t+1$.

## Base e dimensione

Una **base** è un insieme di vettori *linearmente indipendenti* che generano $V$:

$$
\lambda_1 v_1 + \cdots + \lambda_n v_n = 0 \;\Longrightarrow\; \lambda_1 = \cdots = \lambda_n = 0
$$

La **dimensione** di $V$ è il numero di vettori in una base. La base canonica di $\mathbb{R}^n$ è l'insieme degli $n$ vettori standard (one-hot).

## Prodotto scalare

Il prodotto scalare tra $x, y \in \mathbb{R}^n$:

$$
x^\top y = \sum_{i=1}^n x_i y_i
$$

## Rilevanza per il ML

In ML ogni dataset è un sottoinsieme di $\mathbb{R}^d$ (spazio delle feature); i parametri di un modello lineare sono elementi dello stesso spazio. Le [[Mappe lineari]] tra spazi vettoriali corrispondono alle matrici.

## Connessioni

- Struttura fondamentale di: [[Mappe lineari]], [[Applicazione lineare]]
- Sottostruttura: [[Sottospazio vettoriale]]
- Generatori e basi: [[Sottospazio generato]], [[Base di uno spazio vettoriale]], [[Dipendenza lineare]]
- In ML: [[Regressione lineare]], [[Multi-Layer Perceptron]]
- Versione con norma: [[Spazio metrico]]
- Versione con prodotto interno: [[Sistema Hilbertiano]]
- Discusso in: [[Algebra Lineare]], [[Machine Learning]] (§2)

## Fonti

- [[Dispense Machine Learning — Galletti]] (§2, pp. 3-4)
- [[Dispense AlgLin — Galletti]]
