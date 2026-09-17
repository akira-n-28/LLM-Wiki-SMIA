---
tipo: concetto
titolo: Combinatoria
tag: [probabilità, fondamenti, matematica-discreta]
cluster: probabilistica
fonti: 2
ultima-modifica: 2026-05-06
---

# Combinatoria

Disciplina del **conteggio**: contare configurazioni di un insieme finito sotto vincoli. È il fondamento del **modello classico** di probabilità $P(A) = |A|/|S|$.

## Le quattro famiglie fondamentali

Estraendo $k$ elementi da un insieme di $n$:

| Modello | Ordinato? | Ripetizioni? | Conteggio |
|---|---|---|---|
| **Permutazioni** | sì | no | $n! = n(n-1)\cdots 1$ |
| **Disposizioni** $D_{n,k}$ | sì | no | $\dfrac{n!}{(n-k)!}$ |
| **Combinazioni** $\binom{n}{k}$ | no | no | $\dfrac{n!}{k!(n-k)!}$ |
| **Disposizioni con ripetizione** | sì | sì | $n^k$ |
| **Combinazioni con ripetizione** | no | sì | $\binom{n+k-1}{k}$ |

## Identità chiave

- **Simmetria binomiale:** $\binom{n}{k} = \binom{n}{n-k}$.
- **Formula di Pascal:** $\binom{n}{k} = \binom{n-1}{k-1} + \binom{n-1}{k}$.
- **Teorema binomiale:** $(a+b)^n = \sum_{k=0}^n \binom{n}{k} a^k b^{n-k}$ (cfr. [[Teorema Binomiale]]).
- **Vandermonde:** $\binom{m+n}{k} = \sum_{j=0}^k \binom{m}{j}\binom{n}{k-j}$.

## Principio di inclusione-esclusione

Per eventi $A_1, \ldots, A_n$:

$$
P\!\left(\bigcup_{i=1}^n A_i\right) = \sum_i P(A_i) - \sum_{i<j} P(A_i \cap A_j) + \sum_{i<j<k} P(A_i \cap A_j \cap A_k) - \cdots
$$

Forma compatta:
$$
P\!\left(\bigcup_i A_i\right) = \sum_{\emptyset \neq S \subseteq \{1,\ldots,n\}} (-1)^{|S|+1} P\!\left(\bigcap_{i \in S} A_i\right)
$$

**Esempio (problema dei sorteggi):** la probabilità che almeno una persona riceva il proprio nome (su $n$) tende a $1 - 1/e \approx 0.632$ per $n \to \infty$.

## Modelli di estrazione da urna

Urna con $N$ palline, $K$ bianche, $N-K$ nere. Si estrae $n$ palline.

| Modello | Reinserimento? | Ordinato? | Distribuzione di $X$ = bianche |
|---|---|---|---|
| **Bernoulli/Binomiale** | sì | irrilevante | $X \sim B(n, p=K/N)$ |
| **Ipergeometrico** | no | irrilevante | $P(X=k) = \dfrac{\binom{K}{k}\binom{N-K}{n-k}}{\binom{N}{n}}$ |
| **Multinomiale** ($r$ colori) | sì | irrilevante | $P(\mathbf{k}) = \dfrac{n!}{k_1! \cdots k_r!} p_1^{k_1} \cdots p_r^{k_r}$ |

**Convergenza:** ipergeometrico $\to$ binomiale per $N \to \infty$ con $K/N \to p$ fisso (urna grande $\Rightarrow$ "come se" si reinserisse).

## Modello classico

Spazio campionario finito $S$ con $|S| < \infty$ e tutti gli esiti equiprobabili: $P(\{s\}) = 1/|S|$. Allora $P(A) = |A|/|S|$ — il calcolo della probabilità si riduce a un **conteggio combinatorio**.

**Validità:** richiede simmetria reale tra esiti (lancio di dado equo, estrazione casuale). Fallisce quando gli esiti non sono equiprobabili.

## Problema dei compleanni

Con $n$ persone, la probabilità che almeno due abbiano lo stesso compleanno (su 365) è:
$$
P_n = 1 - \frac{365 \cdot 364 \cdots (365 - n + 1)}{365^n} = 1 - \frac{D_{365, n}}{365^n}
$$

Per $n = 23$: $P \approx 0.507$ — controintuitivamente alta.

## Connessione con il [[Metodo probabilistico]]

Combinatoria + valore atteso = strumento di esistenza: se $E[X] > 0$ allora esiste un esito con $X > 0$. Usato per dimostrare l'esistenza di colorazioni, cammini, codici senza costruirli esplicitamente.

## Connessioni

- Strumento di base per: [[Spazio di probabilità]], [[Variabile aleatoria]] (Binomiale, Ipergeometrico, Multinomiale)
- Identità: [[Teorema Binomiale]], [[Permutazione]] (gruppo simmetrico in [[Strutture Algebriche]])
- Estensione: [[Funzione generatrice delle probabilità]] (combinatoria via serie di potenze)
- Applicazione: [[Metodo probabilistico]], [[Lemma di Schwarz-Zippel]]

## Fonti

- [[Dispense ProbStat — Galletti]] (§1, pp. 3-7)
- [[Dispense StrAlg — Galletti]] (rinforza con [[Permutazione]] e [[Teorema Binomiale]])
