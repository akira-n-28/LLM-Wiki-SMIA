---
tipo: concetto
titolo: Metodo probabilistico
tag: [probabilità, combinatoria, dimostrazioni]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-06
---

# Metodo probabilistico

Tecnica di dimostrazione di esistenza dovuta a **Paul Erdős**: invece di costruire esplicitamente una struttura combinatoria con la proprietà desiderata, si **prova che esiste con probabilità positiva** in un modello probabilistico ben scelto. Esistenza = $P(\text{proprietà}) > 0$.

## Il principio fondamentale

Sia $X$ una [[Variabile aleatoria]] su uno spazio campionario $S$ di esiti possibili. Allora:

> Se $E[X] > c$, esiste almeno un esito $\omega \in S$ tale che $X(\omega) > c$.

**Dimostrazione:** se $X(\omega) \leq c$ per ogni $\omega$, allora $E[X] = \sum X(\omega) P(\omega) \leq c$, contraddizione. $\square$

Variante per minimo: se $E[X] < c$, esiste $\omega$ con $X(\omega) < c$.

## Esempio canonico: cammino hamiltoniano in tornei

**Teorema (Szele 1943):** ogni torneo (grafo orientato completo) con $n$ vertici ha almeno $n!/2^{n-1}$ cammini hamiltoniani.

**Dimostrazione:** considera un torneo casuale (orientazione di $K_n$ scelta uniformemente). Per ogni permutazione $\pi$ dei vertici, sia $X_\pi$ l'indicatore che $\pi$ sia un cammino hamiltoniano. Allora:
$$
P(X_\pi = 1) = (1/2)^{n-1}
$$
(serve che ogni arco $\pi(i) \to \pi(i+1)$ sia orientato correttamente). Il numero atteso di cammini è:
$$
E[X] = \sum_\pi E[X_\pi] = n!/2^{n-1}
$$
Esiste quindi un torneo con almeno $E[X]$ cammini hamiltoniani. $\square$

## Esempio: 2-colorazione senza monocromatici

**Teorema (Erdős):** se $\binom{n}{k} 2^{1-\binom{k}{2}} < 1$, esiste una 2-colorazione di $K_n$ senza $K_k$ monocromatico.

**Dimostrazione:** colora ogni arco con probabilità $1/2$. Per un fissato $K_k$, $P(\text{monocromatico}) = 2 \cdot 2^{-\binom{k}{2}}$. Per union bound: $P(\exists K_k \text{ monocromatico}) \leq \binom{n}{k} 2^{1-\binom{k}{2}} < 1$. Esiste quindi una colorazione senza $K_k$ monocromatico. $\square$

Da qui: $R(k, k) > 2^{k/2}$ per il numero di Ramsey diagonale.

## Tre tecniche del metodo probabilistico

### 1. Linearità dell'attesa
Anche per v.a. dipendenti, $E[\sum X_i] = \sum E[X_i]$. Permette di stimare proprietà aggregate senza calcolare la distribuzione congiunta.

### 2. Union bound
$P(A_1 \cup \cdots \cup A_n) \leq \sum P(A_i)$. Se $\sum P(A_i) < 1$ allora esiste un esito in cui nessun $A_i$ si verifica.

### 3. Local lemma (Lovász)
Più sofisticato: anche se $\sum P(A_i) \geq 1$, sotto vincoli di dipendenza limitata, si può ancora concludere $P(\bigcap A_i^c) > 0$.

## Limiti

- Dimostra **esistenza**, non costruisce. Algoritmi randomizzati possono "derandomizzare" (metodo dei pesi condizionati).
- Le bound spesso non sono tight: il numero atteso può essere molto più grande del minimo realizzato.
- Richiede una scelta intelligente del modello probabilistico.

## Connessioni con altri argomenti

- **[[Combinatoria]]**: complementare — combinatoria conta, metodo probabilistico stima medie.
- **[[Algoritmi e Complessità]]**: la randomizzazione è la base degli algoritmi randomizzati (Quick Sort, [[Locality Sensitive Hashing]], primality testing).
- **[[Lemma di Schwarz-Zippel]]**: caso applicativo per test di identità polinomiale.
- **[[Valore atteso]]**: è lo strumento operativo (la pagina contiene un esempio della linearità).

## Persone

- **Paul Erdős** (1947): "Some remarks on the theory of graphs" — primo uso esplicito.
- **László Lovász**: Lovász Local Lemma (1975).
- Il libro di riferimento è *The Probabilistic Method* di Alon e Spencer.

## Fonti

- [[Dispense ProbStat — Galletti]] (§2, esempi di cammino hamiltoniano)
