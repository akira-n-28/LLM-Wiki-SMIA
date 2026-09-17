---
tipo: fonte
titolo: Dispense MatML — Galletti
autori: [Marco Galletti]
docente-corso: Elena Agliari
anno-accademico: 2025/2026
data-ingest: 2026-04-30
file-raw: raw/appunti/MatML.pdf
pagine: 68
ultima-modifica: 2026-05-04
tag: [matematica, ml, statistica, bayesiano, monte-carlo]
---

# Dispense di Matematica per il Machine Learning — Galletti

**Riferimento file raw:** `raw/appunti/MatML.pdf`
**Corso:** [[Matematica per il Machine Learning]] (prof.ssa Elena Agliari, A.A. 2025/2026, SMIA Sapienza)
**Autore appunti:** [[Galletti, Marco]]

## Riassunto in 5 punti

1. **Statistica inferenziale** come fondamento: media/varianza campionaria, intervalli di confidenza, test di ipotesi (H₀, p-value), distribuzioni t-Student, χ², F.
2. **Apprendimento statistico** formalizzato come minimizzazione del [[Rischio teorico]] (ignoto) tramite il [[Rischio empirico]] (ERM); per la loss MSE il predittore ottimo è `E[Y|X]`.
3. **Decomposizione del rischio** in tre termini (rischio di Bayes + errore di approssimazione + errore di stima) e dualmente in [[Bias-Variance trade-off]] puntuale, illustrato esplicitamente sul caso lineare via [[Matrice di Vandermonde]] e [[Matrice di Hilbert]].
4. **Apprendimento Bayesiano**: prior/likelihood/posterior, [[Distribuzioni coniugate]] (Beta-Bernoulli, Gamma-Poisson, Normale-Inv-Gamma), [[Stima MAP]], [[Intervalli di credibilità]], convergenza dell'evidenza a `g(τ|θ̂_ML)` e [[BIC]] come approssimazione di Laplace.
5. **Metodi Monte Carlo**: generazione pseudo-casuale (MRG), trasformate ([[Algoritmo di Box-Muller]], [[Metodo della funzione inversa]], [[Metodo accept-reject]]), MCMC ([[Metropolis-Hastings]], [[Campionamento di Gibbs]]) con [[Bilancio dettagliato]] ed [[Ergodicità]] come condizioni di convergenza, e [[Bootstrap]] per la stima di errori standard.

## Argomenti trattati

### Parte 1 — Introduzione (pp. 2-9)
- [[Statistica descrittiva]] e [[Statistica inferenziale]]
- [[Media campionaria]], [[Varianza campionaria]], [[Outlier]]
- Tipi di grafici: bar chart, istogramma, pie chart, box-plot, Q-Q plot
- [[Intervallo di confidenza]]
- [[Distribuzione t-Student]], [[Distribuzione chi-quadro]]
- [[Test di ipotesi]] (H₀, p-value, test a due code)

### Parte 2 — Apprendimento Statistico (pp. 9-43)
- [[Apprendimento statistico]] (supervisionato vs non supervisionato)
- [[Funzione di perdita]] (MSE, MAE, BCE, 0-1)
- [[Rischio teorico]] e [[Rischio empirico]] → [[ERM]]
- Predittore ottimo MSE: `g*(x) = E[Y|X=x]`
- Classificatore ottimo di Bayes (loss 0-1): `g*(x) = arg max_y f(y|x)`
- [[Regressione polinomiale]], [[Matrice di Vandermonde]], [[Minimi quadrati]] (OLS)
- [[Bias-Variance trade-off]] e [[Errore di approssimazione e di stima]]
- [[Matrice di Hilbert]] (caso lineare con `U ∼ U(0,1)`)
- [[Rischio in-sample]] e [[Ottimismo]] (= `2σ²p/n` nel caso lineare)
- [[Cross-validation]] (K-fold, leave-one-out)
- [[Apprendimento non supervisionato]], [[Divergenza di Kullback-Leibler]]
- [[Stima di Massima Verosimiglianza]] (ML), Score
- [[Funzione generatrice dei momenti]]
- [[Distribuzione Gamma]], [[Distribuzione Inverse-Gamma]], [[Distribuzione Beta]], [[Distribuzione F di Fisher-Snedecor]]
- [[Distribuzione Normale Multivariata]] (decomposizione di Cholesky)
- [[Modello lineare normale]] (ML = OLS)
- [[Apprendimento Bayesiano]]: prior/likelihood/posterior
- [[Distribuzioni coniugate]]
- [[Stima MAP]], [[Intervalli di credibilità]]
- [[Disuguaglianza di Jensen]] (usata per la convergenza dell'evidenza)
- [[BIC]] (approssimazione di Laplace)

### Parte 3 — Metodi Monte Carlo (pp. 43-68)
- [[Metodi Monte Carlo]] (panoramica: campionamento, integrazione, ottimizzazione)
- [[Generatore MRG]] (MRG)
- [[Algoritmo di Box-Muller]]
- [[Metodo della funzione inversa]]
- [[Metodo accept-reject]]
- [[Catena di Markov]] (omogenea, distribuzione stazionaria, distribuzione limite)
- [[Bilancio dettagliato]] e [[Ergodicità]]
- [[Metropolis-Hastings]]
- [[Campionamento di Gibbs]]
- [[Bootstrap]] (§3.11.1: stime Var/Bias/MSE, CI normale e percentile)
- [[Riduzione della varianza]] (§3.12: variabili di controllo, α* = Cov/Var, riduzione (1-ρ²))
- [[Importance Sampling]] (§3.13: pesi f/g, g* ottimale, varianza finita)
- [[Simulated Annealing]] (§3.14: distribuzione di Gibbs, T→0, M-H per ogni T)
- [[Approssimazione stocastica]] (§3.15.1: Robbins-Monro, Kiefer-Wolfowitz, condizioni βₜ)
- [[Metodo del corrispondente stocastico]] (§3.15.2: SAA, campione fisso, ottimizzazione deterministica)
- [[Metodo Cross-Entropy]] (§3.16: élite, MLE su élite = min KL, smoothing α)

## Citazioni chiave

> "Il rischio empirico valutato sui dati di addestramento `ℓ_T(g_T)` è uno stimatore fortemente distorto e ottimistico del vero rischio `ℓ(g_T)`. Avendo l'algoritmo minimizzato l'errore proprio su T, la training loss sottostimerà sistematicamente l'errore di generalizzazione su dati futuri." — Oss. 2.2, p. 12

> "È sufficiente conoscere la densità target a meno di una costante di normalizzazione. Infatti, ponendo `f(x) = C f̄(x)`, la costante incognita C si elide nel calcolo del rapporto `f(y)/f(x)`." — sull'algoritmo di Metropolis-Hastings, p. 50

> "Un aspetto fondamentale del metodo Monte Carlo è che il tasso di convergenza dell'errore, proporzionale a `O(N^{-1/2})`, non scala con la dimensione del dominio di integrazione." — Oss. 3.7, p. 55

## Note di lettura

- Le dispense sono molto **dimostrative**: non si limita a enunciare risultati, deriva quasi tutto (p.es. predittore ottimo MSE, ottimismo per OLS, convergenza dell'evidenza Bayesiana, Box-Muller, M-H da bilancio dettagliato).
- Forte intreccio tra **statistica inferenziale classica** (Parte 1) e **apprendimento statistico** (Parte 2): le distribuzioni introdotte all'inizio (t, χ²) ricompaiono come posterior nel framework Bayesiano (esempio modello normale con prior improprio → marginal posterior `t_{n-1}`).
- La trattazione Bayesiana è il fulcro: 12 pagine (30-41) di esempi (Bernoulli, Poisson, Normale) e tre livelli di prior (proper, improprio per μ, doppiamente improprio).
- I metodi Monte Carlo sono presentati con linguaggio della **fisica statistica** (Boltzmann-Gibbs, magnetizzazione, spin) — collegamento esplicito con [[Modelli Matematici per la Fisica II]].

## Pagine wiki aggiornate da questa ingest

**Primo ingest (2026-05-04, 58 pp.):**
- [[Matematica per il Machine Learning]] — corso aggiornato con concetti centrali e link.
- Create ~45 pagine in `wiki/concetti/` e 16 in `wiki/persone/` (vedi `index.md`).

**Secondo ingest (2026-05-04, 68 pp. — sezioni §3.12–3.16 aggiunte):**
- [[Bootstrap]] — arricchito: stime formali Var/Bias/MSE, CI normale e percentile, esempio cammino aleatorio.
- Create: [[Riduzione della varianza]], [[Importance Sampling]], [[Simulated Annealing]], [[Approssimazione stocastica]], [[Metodo del corrispondente stocastico]], [[Metodo Cross-Entropy]].

## Prossimi passi suggeriti

- Quando arriverà l'ingest profondo di [[Processi Stocastici]] (Isopi), unificare la pagina [[Catena di Markov]] integrando le due prospettive.
- Quando arriverà l'ingest di [[Machine Learning]] (Rodolà), confrontare la decomposizione bias-varianza e l'uso di cross-validation con la trattazione di Agliari.
- Quando arriverà l'ingest di [[Modelli Matematici per la Fisica II]] (Zamponi), unificare [[Bilancio dettagliato]] e la distribuzione di Boltzmann-Gibbs.
