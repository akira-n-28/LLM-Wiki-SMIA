---
tipo: concetto
titolo: Lemma di Schwarz-Zippel
tag: [probabilità, algoritmi-randomizzati, algebra]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-06
---

# Lemma di Schwarz-Zippel

Risultato che lega il **grado** di un polinomio alla probabilità che esso si annulli su un punto casuale. È la base teorica dei **test probabilistici di identità polinomiale**.

## Enunciato

Sia $p(x_1, \ldots, x_n)$ un polinomio non nullo a coefficienti in un campo $\mathbb{F}$, di grado totale $d$. Sia $S \subseteq \mathbb{F}$ un sottoinsieme finito. Se $r_1, \ldots, r_n$ sono scelti uniformemente e indipendentemente da $S$:

$$
P\bigl(p(r_1, \ldots, r_n) = 0\bigr) \leq \frac{d}{|S|}
$$

## Dimostrazione (induzione su $n$)

**Base $n = 1$:** un polinomio non nullo di grado $d$ in una variabile ha al più $d$ radici. Quindi $P(p(r) = 0) \leq d/|S|$. ✓

**Passo induttivo:** scrivi $p(x_1, \ldots, x_n) = \sum_{i=0}^k x_n^i\, q_i(x_1, \ldots, x_{n-1})$ dove $k$ è il grado massimo di $x_n$ e $q_k \neq 0$. Allora $\deg(q_k) \leq d - k$.

Decomponi l'evento $\{p = 0\}$:
- $A = \{q_k(r_1, \ldots, r_{n-1}) = 0\}$: per ipotesi induttiva, $P(A) \leq (d-k)/|S|$.
- $A^c \cap \{p = 0\}$: condizionatamente a $A^c$, il polinomio $p(r_1, \ldots, r_{n-1}, x_n)$ è un polinomio in $x_n$ di grado esattamente $k$, non nullo, quindi $P(p = 0 \mid A^c) \leq k/|S|$.

Per total probability:
$$
P(p = 0) \leq P(A) + P(A^c) \cdot P(p=0 \mid A^c) \leq \frac{d-k}{|S|} + \frac{k}{|S|} = \frac{d}{|S|}. \quad \square
$$

## Applicazione: test di identità polinomiale

Date due rappresentazioni $p_1, p_2$ di polinomi (es. forma simbolica vs determinante di una matrice di polinomi), vogliamo decidere se $p_1 \equiv p_2$.

**Algoritmo (PIT):**
1. Scegli $S$ con $|S| \geq 2d$.
2. Estrai $r_1, \ldots, r_n \in S$ uniformemente.
3. Valuta $p_1(\mathbf{r})$ e $p_2(\mathbf{r})$.
4. Se differiscono, $p_1 \not\equiv p_2$ con certezza. Se coincidono, $p_1 \equiv p_2$ **con probabilità $\geq 1/2$**.

Ripetendo $k$ volte e accettando solo se tutte le valutazioni coincidono, l'errore scende a $2^{-k}$.

## Esempi notevoli di uso

- **Verifica di moltiplicazione di matrici:** controllare $AB = C$ in tempo $O(n^2)$ (Freivalds): scegli $\mathbf{r}$ casuale, verifica $A(B\mathbf{r}) = C\mathbf{r}$. Se $AB \neq C$, $P(\text{collide}) \leq 1/2$ per Schwarz-Zippel applicato al polinomio $(AB - C)\mathbf{r}$.
- **Matching perfetto in grafi bipartiti:** Tutte's matrix theorem riduce l'esistenza di un matching perfetto al non-annullamento di un determinante simbolico — verificabile via Schwarz-Zippel.
- **Primality testing:** il test di Solovay-Strassen e Miller-Rabin condividono lo spirito (anche se non sono Schwarz-Zippel diretto).

## Confronto con union bound

Per $n$ variabili e grado $d$, una bound naïve via union bound darebbe $\leq nd/|S|$. Schwarz-Zippel è **strettamente migliore** ($d$ invece di $nd$), perché sfrutta la struttura algebrica del polinomio.

## Connessioni

- Strumento per: algoritmi randomizzati (cfr. [[Algoritmi e Complessità]] — randomized algorithms).
- Generalizza: il fatto elementare che un polinomio in 1 variabile di grado $d$ ha $\leq d$ radici.
- Applicazione: [[Metodo probabilistico]] (Schwarz-Zippel produce esistenza di valutazioni "buone").

## Persone

- **Jacob T. Schwartz** (1980), **Richard Zippel** (1979), **Øystein Ore** (1922): scoperte indipendenti.
- Il lemma è anche chiamato **DeMillo-Lipton-Schwartz-Zippel** in alcune fonti.

## Fonti

- [[Dispense ProbStat — Galletti]] (§2.1.2, problema delle parti)
