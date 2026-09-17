---
tipo: corso
titolo: Processi Stocastici
docente: Marco Isopi
anno-accademico: 2025/2026
codice-breve: processi
ultima-modifica: 2026-05-04
tag: [probabilità, processi-stocastici, smia]
stato: 🟢
---

# Processi Stocastici

Corso di **Processi Stocastici** tenuto dal prof. **Marco Isopi** nell'A.A. 2025/2026, SMIA, Sapienza.

> Continuazione naturale di [[Probabilità e Statistica]]: da lì i fondamenti, qui la teoria delle catene di Markov e dei processi a tempo continuo.

## Programma

1. **Introduzione** — assiomi di Kolmogorov, probabilità condizionata, [[Variabile aleatoria]], CDF/densità
2. **Distribuzioni**
   - Distribuzione uniforme, [[Distribuzione geometrica]], Binomiale, [[Distribuzione di Poisson]]
3. **Catene di Markov**
   - Matrice di transizione, accessibilità, classi comunicanti, irriducibilità
   - Stati transienti/ricorrenti/ricorrenti-positivi, periodicità
   - [[Passeggiata aleatoria]] (Random Walk, Rovina del giocatore)
   - Distribuzione stazionaria, teorema ergodico
4. **Serie di potenze**
   - [[Funzione generatrice delle probabilità]] `G(s) = E[s^T]`, calcolo di momenti
5. **Comportamento asintotico**
   - Teorema ergodico: `lim P(Xn=j|X0=i) = πⱼ = 1/µⱼ`
   5.1 [[Processo di nascita e morte]] — bilancio dettagliato ricorsivo
   5.2 [[Distribuzione esponenziale]], [[Generatore infinitesimale]], [[Processo di Poisson (continuo)]]
   - Incrementi stazionari e indipendenti, [[Catena immersa]]
   - [[Equazione logistica]] (limite continuo di processi di nascita e morte)

## Concetti centrali

**Catene di Markov (tempo discreto)**
- [[Catena di Markov]] — teoria completa, matrice di transizione
- [[Passeggiata aleatoria]] — random walk, rovina del giocatore
- [[Bilancio dettagliato]] — stazionarietà per processi di nascita e morte
- [[Funzione generatrice delle probabilità]] — calcolo momenti

**Processi continui**
- [[Distribuzione esponenziale]] — memoryless, base della teoria continua
- [[Processo di nascita e morte]] — classi di catene con transizioni adiacenti
- [[Generatore infinitesimale]] — `Q`, `P(t) = e^{Qt}`, equazioni di Kolmogorov
- [[Processo di Poisson (continuo)]] — incrementi stazionari/indipendenti, $N_t \sim \mathrm{Poi}(\lambda t)$
- [[Catena immersa]] — decomposizione struttura + tempi di permanenza
- [[Equazione logistica]] — limite deterministico di processi di nascita e morte
- [[Distribuzione di Poisson]] — caso discreto del processo

**Fondamenti (vedi [[Probabilità e Statistica]])**
- [[Spazio di probabilità]], [[Probabilità condizionata]], [[Variabile aleatoria]]
- [[Valore atteso]], [[Varianza e covarianza]]

## Persone citate

- [[Isopi, Marco]] — docente del corso
- [[Markov, Andrey]] — catene di Markov
- [[Kolmogorov, Andrey]] — equazioni di Kolmogorov, assiomatizzazione

## Fonti del corso

- [[Dispense Processi Stocastici — Galletti]] (24 pp., 2025/2026) — ✅ ingerita in profondità

## Stato

🟢 **Completo** — concetti centrali estratti (8 pagine), fonte ingerita, gap chiusi (2026-05-06: +Processo di Poisson continuo, +Catena immersa, +Equazione logistica).
