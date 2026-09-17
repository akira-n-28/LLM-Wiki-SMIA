---
tipo: moc
titolo: MOC — Probabilistica
cluster: probabilistica
ultima-modifica: 2026-05-06
---

# MOC — Probabilistica

**Map of Content** del cluster `probabilistica` (54 concetti). Pagina di **navigazione tematica** per studio.

> **Corsi coinvolti:** [[Probabilità e Statistica]] (Isopi, 24/25), [[Processi Stocastici]] (Isopi, 25/26), [[Matematica per il Machine Learning]] (Agliari, 25/26 — §1-§3), [[Modelli Matematici per la Fisica II]] (Zamponi, 24/25 — fisica statistica).

---

## 🎯 Da dove iniziare

Se è la prima volta, l'ordine canonico:

1. [[Spazio di probabilità]] — assiomi di Kolmogorov
2. [[Probabilità condizionata]] → [[Formula di Bayes]]
3. [[Combinatoria]] — modello classico
4. [[Variabile aleatoria]] (discreta + continua)
5. [[Funzione di ripartizione]] — CDF
6. [[Valore atteso]] → [[Varianza e covarianza]] → [[Attesa condizionata]]

## 🎲 Fondamenti

- [[Spazio di probabilità]] — assiomi
- [[Probabilità condizionata]] — indipendenza
- [[Formula di Bayes]] — prior/likelihood/posterior
- [[Combinatoria]] — permutazioni, disposizioni, combinazioni
- [[Metodo probabilistico]] — esistenza via E[X] > 0
- [[Lemma di Schwarz-Zippel]] — algoritmi randomizzati

## 📊 Variabili aleatorie

- [[Variabile aleatoria]] — discreta e continua
- [[Funzione di ripartizione]] — CDF, quantili, Glivenko-Cantelli
- [[Valore atteso]] — linearità, leggi
- [[Varianza e covarianza]] — momenti del secondo ordine
- [[Attesa condizionata]] — tower property, varianza totale
- [[Funzione generatrice dei momenti]] — MGF, cumulanti
- [[Funzione generatrice delle probabilità]] — PGF (caso discreto)

## 📐 Distribuzioni notevoli

**Discrete:**
- [[Distribuzione geometrica]] — primi successi
- [[Distribuzione di Poisson]] — eventi rari

**Continue:**
- [[Distribuzione esponenziale]] — memoryless
- [[Distribuzione Normale Multivariata]] — base ML
- [[Distribuzione Gamma]] — somma di esponenziali
- [[Distribuzione Inverse-Gamma]]
- [[Distribuzione Beta]] — coniugata della Bernoulli
- [[Distribuzione t-Student]] — test t
- [[Distribuzione chi-quadro]] — varianza campionaria
- [[Distribuzione F di Fisher-Snedecor]] — rapporto di varianze

## 📉 Statistica inferenziale

- [[Statistica descrittiva]] vs [[Statistica inferenziale]]
- [[Media campionaria]] e [[Varianza campionaria]]
- [[Outlier]]
- [[Stimatore]] — bias, varianza, MSE, consistenza, sufficienza
- [[Stima di Massima Verosimiglianza]] (MLE)
- [[Stima MAP]] (Bayesiana puntuale)
- [[Intervallo di confidenza]] (frequentista)
- [[Intervalli di credibilità]] (Bayesiano)
- [[Test di ipotesi]]

## 🌊 Convergenza & disuguaglianze

- [[Disuguaglianza di Markov]] — bound elementare
- [[Disuguaglianza di Chebyshev]] — concentrazione
- [[Disuguaglianza di Jensen]] — convessità
- [[Legge dei Grandi Numeri]] (debole) — $\bar X_n \to \mu$
- [[Teorema ergodico]] — generalizza LGN a catene markoviane

## ⛓️ Catene di Markov & processi stocastici

**Discreto:**
- [[Catena di Markov]] — proprietà di base, classi comunicanti
- [[Passeggiata aleatoria]] (Random Walk, rovina del giocatore)
- [[Bilancio dettagliato]] — condizione sufficiente
- [[Teorema ergodico]]

**Continuo:**
- [[Distribuzione esponenziale]] — base teoria continua
- [[Generatore infinitesimale]] — $Q$, $P(t) = e^{Qt}$
- [[Catena immersa]] — decomposizione struttura/tempi
- [[Processo di nascita e morte]] — esempio principale
- [[Processo di Poisson (continuo)]] — incrementi stazionari
- [[Equazione logistica]] — limite deterministico

## 🎰 Monte Carlo & MCMC

**Generazione:**
- [[Generatore MRG]] — pseudo-casuale
- [[Algoritmo di Box-Muller]] — gaussiane
- [[Metodo della funzione inversa]] — distribuzioni con CDF nota
- [[Metodo accept-reject]] — campionamento per rifiuto

**Stima:**
- [[Metodi Monte Carlo]] — framework
- [[Bootstrap]] — non parametrico
- [[Importance Sampling]] — varianza ridotta
- [[Riduzione della varianza]]

**MCMC:**
- [[Metropolis-Hastings]] — algoritmo generale
- [[Campionamento di Gibbs]] — multivariato

## 📐 Bayes & framework probabilistico

- [[Apprendimento Bayesiano]] — paradigma
- [[Stima MAP]] vs MLE
- [[Distribuzioni coniugate]]
- [[BIC]] — approssimazione di Laplace
- [[Divergenza di Kullback-Leibler]] — rischio
- [[Disuguaglianza di Jensen]] — non-negatività KL

## 🔗 Argomenti trasversali

- [[Catene di Markov e MCMC]] — sintesi 4 corsi
- [[Probabilità bayesiana e inferenza]] — sintesi 5 corsi
- [[Entropia e information theory]] — Shannon, KL, MaxEnt

## 📚 Per esame

**ProbStat (Isopi, 24/25):** §1-§8 → [[Probabilità e Statistica]]
**Processi Stocastici (Isopi, 25/26):** catene + tempi continui → [[Processi Stocastici]]
**MatML (Agliari, 25/26):** §1-§3 (statistica + Bayes + MC) → [[Matematica per il Machine Learning]]
