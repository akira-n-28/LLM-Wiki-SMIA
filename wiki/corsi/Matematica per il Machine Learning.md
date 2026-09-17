---
tipo: corso
titolo: Matematica per il Machine Learning
docente: Elena Agliari
anno-accademico: 2025/2026
codice-breve: MatML
ultima-modifica: 2026-05-04
tag: [matematica, ml, statistica, smia]
---

# Matematica per il Machine Learning

Corso di **Matematica per il Machine Learning** tenuto dalla prof.ssa **[[Agliari, Elena]]** nell'A.A. 2025/2026, corso di laurea SMIA, Sapienza. Dispense redatte da [[Galletti, Marco]].

## Programma

### 1. Statistica di base
1.1 Tipologie di output e analisi dei dati — [[Statistica descrittiva]], [[Statistica inferenziale]]
1.2 Grafici (boxplot, istogrammi, Q-Q plot)
1.3 Statistiche campionarie: [[Media campionaria]], [[Varianza campionaria]], [[Outlier]]
1.4 Stima puntuale e [[Intervallo di confidenza]]
1.5 [[Test di ipotesi]] (Z-test, T-test, Chi-quadro, F-test)
1.6 Distribuzioni: [[Distribuzione t-Student]], [[Distribuzione chi-quadro]], [[Distribuzione F di Fisher-Snedecor]], [[Distribuzione Gamma]], [[Distribuzione Inverse-Gamma]], [[Distribuzione Beta]]

### 2. Apprendimento Statistico
2.1 [[Apprendimento statistico]] — [[Funzione di perdita]], [[Rischio teorico]], [[Rischio empirico]], [[ERM]]
2.2 [[Regressione polinomiale]] — [[Matrice di Vandermonde]], [[Minimi quadrati]], [[Matrice di Hilbert]]
2.3 [[Errore di approssimazione e di stima]] — [[Bias-Variance trade-off]]
2.4 [[Rischio in-sample]], [[Ottimismo]], [[Cross-validation]], [[BIC]]
2.5 [[Stima di Massima Verosimiglianza]] — [[Divergenza di Kullback-Leibler]]
2.6 [[Funzione generatrice dei momenti]], [[Distribuzione Normale Multivariata]], [[Modello lineare normale]]
2.7 [[Apprendimento Bayesiano]] — [[Distribuzioni coniugate]], [[Stima MAP]], [[Intervalli di credibilità]]
2.8 [[Disuguaglianza di Jensen]], [[BIC]] (approssimazione di Laplace)

### 3. Metodi Monte Carlo
3.1 [[Metodi Monte Carlo]] — applicazioni, integrazione numerica
3.2 [[Generatore MRG]] — numeri pseudo-casuali
3.3 [[Algoritmo di Box-Muller]], [[Metodo della funzione inversa]], [[Metodo accept-reject]]
3.4 [[Catena di Markov]] — distribuzione stazionaria, [[Bilancio dettagliato]], burn-in
3.5 [[Metropolis-Hastings]], [[Campionamento di Gibbs]]
3.6 [[Bootstrap]] (ricampionamento; CI normale e percentile)
3.7 [[Riduzione della varianza]] — variabili di controllo, α*, correlazione IS
3.8 [[Importance Sampling]] — pesi f/g, pdf ottimale g*, IS self-normalized
3.9 [[Simulated Annealing]] — distribuzione di Gibbs, T→0, M-H per ogni temperatura
3.10 [[Approssimazione stocastica]] (Robbins-Monro, KW) — [[Metodo del corrispondente stocastico]] (SAA)
3.11 [[Metodo Cross-Entropy]] — élite, MLE su élite, minimizzazione KL, smoothing

## Concetti centrali

### Statistica
- [[Statistica descrittiva]] — [[Statistica inferenziale]]
- [[Media campionaria]] — [[Varianza campionaria]]
- [[Intervallo di confidenza]] — [[Test di ipotesi]]
- Distribuzioni: [[Distribuzione t-Student]], [[Distribuzione chi-quadro]], [[Distribuzione F di Fisher-Snedecor]], [[Distribuzione Gamma]], [[Distribuzione Inverse-Gamma]], [[Distribuzione Beta]]

### Apprendimento statistico
- [[Apprendimento statistico]] — [[ERM]] — [[Rischio teorico]] — [[Rischio empirico]]
- [[Bias-Variance trade-off]] — [[Errore di approssimazione e di stima]]
- [[Minimi quadrati]] — [[Regressione polinomiale]] — [[Matrice di Vandermonde]] — [[Matrice di Hilbert]]
- [[Rischio in-sample]] — [[Ottimismo]] — [[Cross-validation]] — [[BIC]]
- [[Stima di Massima Verosimiglianza]] — [[Divergenza di Kullback-Leibler]]
- [[Distribuzione Normale Multivariata]] — [[Modello lineare normale]]
- [[Apprendimento Bayesiano]] — [[Distribuzioni coniugate]] — [[Stima MAP]] — [[Intervalli di credibilità]]
- [[Disuguaglianza di Jensen]]

### Monte Carlo
- [[Metodi Monte Carlo]] — [[Generatore MRG]]
- [[Algoritmo di Box-Muller]] — [[Metodo della funzione inversa]] — [[Metodo accept-reject]]
- [[Catena di Markov]] — [[Bilancio dettagliato]]
- [[Metropolis-Hastings]] — [[Campionamento di Gibbs]] — [[Bootstrap]]
- [[Riduzione della varianza]] — [[Importance Sampling]]
- [[Simulated Annealing]] — [[Approssimazione stocastica]] — [[Metodo del corrispondente stocastico]]
- [[Metodo Cross-Entropy]]

## Fonti del corso

- [[Dispense MatML — Galletti]] — dispense complete, 68 pp., ingerite in profondità (2026-05-04, aggiornamento §3.12-3.16 stesso giorno)

## Stato della wiki per questo corso

🟢 **Completo** — ingest profondo completato (2026-05-04). 51 pagine concettuali + 16 pagine persone + 1 fonte creata.

## Connessioni trasversali con altri corsi

| Concetto MatML | Corso collegato |
|---|---|
| Catene di Markov (MCMC) | [[Processi Stocastici]] |
| Distribuzione di Boltzmann-Gibbs | [[Modelli Matematici per la Fisica II]] |
| Bias-Variance trade-off | [[Machine Learning]] |
| ERM, OLS, regolarizzazione | [[Ottimizzazione]] |
| Integrazione Monte Carlo | [[Metodi Numerici]] |
