---
tipo: fonte
titolo: Dispense ProbStat — Galletti
autori: [Marco Galletti]
docente-corso: Marco Isopi
anno-accademico: 2024/2025
data-ingest: 2026-05-04
file-raw: raw/appunti/probabilita-statistica.pdf
pagine: 46
ultima-modifica: 2026-05-04
tag: [matematica, probabilità, statistica]
---

# Dispense di Probabilità e Statistica — Galletti

**Riferimento file raw:** `raw/appunti/probabilita-statistica.pdf`
**Corso:** [[Probabilità e Statistica]] (prof. Marco Isopi, A.A. 2024/2025, SMIA Sapienza)
**Autore appunti:** [[Galletti, Marco]]

## Riassunto in 5 punti

1. **Combinatoria e insiemistica**: permutazioni, disposizioni, combinazioni, principio di inclusione-esclusione, modello classico e ipergeometrico.
2. **Assiomi di Kolmogorov**: spazio di probabilità (S, P(S), P), probabilità condizionata, indipendenza, formula di Bayes, teorema della probabilità totale.
3. **Variabili aleatorie discrete**: Bernoulli, Binomiale, Geometrica, Poisson; funzione di ripartizione F(x); densità discreta congiunta e marginale.
4. **Valore atteso e varianza**: E[X]=Σx·P(X=x), linearità, E[XY]=E[X]E[Y] per indip.; Var(X)=E[X²]-E[X]², covarianza, indice di correlazione.
5. **Concentrazione**: disuguaglianza di Markov (P(X≥t)≤E[X]/t), disuguaglianza di Chebyshev (P(|X-µ|≥ε)≤Var/ε²), Legge dei Grandi Numeri debole.

## Argomenti trattati

### §1 Teoria degli insiemi (pp. 3-7)
- Operazioni insiemistiche, De Morgan
- [[Combinatoria]] — principio di inclusione-esclusione, modello classico
- [[Combinatoria]] — permutazioni/disposizioni/combinazioni
- Estrazioni da urna (con/senza reinserimento): modello binomiale, ipergeometrico, multinomiale

### §2 Sistema di assiomi (pp. 8-26)
- [[Spazio di probabilità]] — assiomi di Kolmogorov
- Problema dei compleanni
- [[Probabilità condizionata]] — indipendenza — [[Formula di Bayes]]
- Problema delle parti, [[Lemma di Schwarz-Zippel]]
- [[Variabile aleatoria]] — Bernoulli, Binomiale, funzione di ripartizione
- [[Valore atteso]] — E[B(n,p)] = np (dimostrazione identità binomiale)
- [[Metodo probabilistico]] — cammino Hamiltoniano in un torneo

### §3 Varianza (pp. 27-30)
- [[Varianza e covarianza]] — proprietà, Var(Ber)=p(1-p), Var(Bin)=np(1-p)
- [[Attesa condizionata]] — E[X|Y], tower property, varianza totale

### §4 Statistica (pp. 31-33)
- [[Statistica descrittiva]] — mediana, moda
- [[Stimatore]] — distorsione (bias), MSE, consistenza

### §5 Funzioni continue (pp. 34-37)
- [[Variabile aleatoria]] §"continua" — CDF continua, densità di probabilità (PDF)

### §6 Distribuzione Geometrica (pp. 38-40)
- [[Distribuzione geometrica]] — P(X=k)=(1-p)^(k-1)p, E[X]=1/p, Var[X]=(1-p)/p²

### §7 Distribuzione di Poisson (pp. 41-43)
- [[Distribuzione di Poisson]] — limite di Binomiale per n→∞, p→0, np=λ; E[X]=Var[X]=λ

### §8 Legge dei Grandi Numeri (pp. 44-46)
- [[Disuguaglianza di Markov]] — P(X≥t)≤E[X]/t per X≥0
- [[Disuguaglianza di Chebyshev]] — P(|X-µ|≥ε)≤Var(X)/ε²
- [[Legge dei Grandi Numeri]] (debole): X̄_n →^P µ

## Citazioni chiave

> "Il lemma di Schwarz-Zippel dà P(P(r₁,...,rₙ)=0) ≤ d/|S| per un polinomio di grado d scelto a caso su S. È la base dei test probabilistici di identità polinomiale." — §2.1.2

## Note di lettura

- Questo corso è il **prerequisito diretto** di [[Matematica per il Machine Learning]]: la variabile aleatoria, il valore atteso, la varianza, e la LGN sono usate estensivamente in MatML.
- Il prof. Isopi insegna anche [[Processi Stocastici]]: i concetti di variabile aleatoria e convergenza qui introdotti vengono ripresi e generalizzati in quel corso.
- Presenza del **metodo probabilistico** (esistenza di strutture combinatorie via valori attesi) — insolito per un corso di base, segnale che il corso è orientato alla matematica discreta.

## Pagine wiki aggiornate da questa ingest

**Primo ingest (2026-05-04, profondo):**
- [[Probabilità e Statistica]] — corso creato con programma completo (🟢).
- Create: [[Spazio di probabilità]], [[Probabilità condizionata]], [[Formula di Bayes]], [[Variabile aleatoria]], [[Valore atteso]], [[Varianza e covarianza]], [[Distribuzione geometrica]], [[Distribuzione di Poisson]], [[Disuguaglianza di Markov]], [[Disuguaglianza di Chebyshev]]
- Aggiornata: [[Legge dei Grandi Numeri]] (già presente come [[Media campionaria]] in MatML)

**Secondo ingest (2026-05-06, approfondimento dei fondamenti):**
- Create: [[Combinatoria]] (§1), [[Lemma di Schwarz-Zippel]] (§2.1.2), [[Metodo probabilistico]] (§2.6), [[Attesa condizionata]] (§3.2), [[Stimatore]] (§4)
- Estesa: [[Variabile aleatoria]] — aggiunta sezione "continua" con CDF, PDF, distribuzioni notevoli (Uniforme, Esponenziale, Normale)

## Fonti
- `raw/appunti/probabilita-statistica.pdf`
