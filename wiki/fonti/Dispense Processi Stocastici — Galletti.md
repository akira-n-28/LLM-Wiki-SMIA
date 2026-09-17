---
tipo: fonte
titolo: Dispense Processi Stocastici — Galletti
autori: [Marco Galletti]
corso: Processi Stocastici
docente: Marco Isopi
anno-accademico: 2025/2026
data-pubblicazione: 2026
data-ingest: 2026-05-04
file-raw: raw/appunti/processi.pdf
pagine: 24
ultima-modifica: 2026-05-04
tag: [processi-stocastici, markov, dispense, galletti]
---

# Dispense di Processi Stocastici — Galletti

Riassunto del corso di **Processi Stocastici** del prof. **Marco Isopi** (A.A. 2025/2026, SMIA Sapienza), redatto da **Marco Galletti** in 24 pagine. Copre le catene di Markov a tempo discreto, la teoria asintotica, le catene a tempo continuo e i processi di Poisson.

**Riferimento file raw:** `raw/appunti/processi.pdf`

## Riassunto in 5 punti

1. **Fondamenti probabilistici (recap).** Assiomi di Kolmogorov, probabilità condizionata, variabile aleatoria, CDF, distribuzioni (Bernoulli, Geometrica, Binomiale, Poisson). Collegamento diretto con [[Probabilità e Statistica]] — questo corso è la continuazione teorica.

2. **Catene di Markov a tempo discreto.** Matrice di transizione stocastica, rappresentazione tramite grafo orientato pesato. Distribuzione stazionaria come autovettore sinistro (`π = πP`). [[Passeggiata aleatoria]] e rovina del giocatore come caso studio: sistema di equazioni alle differenze, soluzione generale `fₙ(m) = ((q/p)^m - (q/p)^N) / (1 - (q/p)^N)`.

3. **Teoria asintotica delle catene.** Accessibilità (`i→j`), comunicazione (`i↔j`), classi comunicanti, irriducibilità. Stati ricorrenti/transienti/ricorrenti-positivi/ricorrenti-nulli, periodicità. **Teorema ergodico**: se una catena è irriducibile, aperiodica e positivamente ricorrente allora `lim_{n→∞} P(Xn=j|X0=i) = πⱼ = 1/µⱼ(j)`.

4. **Funzione generatrice delle probabilità.** `G(s) = E[s^T] = Σ pₙsⁿ`. Estrae `E[T] = lim G'(s)` e `Var[T]` tramite derivate. Usata per analizzare il tempo di ritorno nell'origine della passeggiata.

5. **Catene a tempo continuo e processi di Poisson.** Distribuzione esponenziale `T∼Exp(λ)`, assenza di memoria. Processo di Poisson `Nₜ∼Poi(λt)` con incrementi stazionari e indipendenti. Generatore infinitesimale `Q`, `P(t) = e^{Qt}`, equazioni di Kolmogorov. Processi di nascita e morte con distribuzione stazionaria via [[Bilancio dettagliato]]. Equazione logistica come limite continuo.

## Citazioni / passaggi notevoli

> "Una distribuzione stazionaria è un autovettore sinistro della matrice di transizione con autovalore 1: `π = πP`." (§3)

> "Processi di nascita e morte soddisfano le equazioni del bilancio dettagliato: `πᵢPᵢⱼ = πⱼPⱼᵢ`. Questo permette di trovare π in modo ricorsivo." (§5.1)

> "Le tre proprietà che individuano univocamente un processo di Poisson: (1) `P(Nₜ₊Δₜ - Nₜ = 0) ≈ 1 - λΔt`, (2) `P(...=1) ≈ λΔt`, (3) `P(...≥2) = o(Δt)`." (§5.2)

## Pagine wiki aggiornate da questa ingest

**Primo ingest (2026-05-04):**
- [[Distribuzione esponenziale]] (nuova)
- [[Passeggiata aleatoria]] (nuova) — include rovina del giocatore
- [[Funzione generatrice delle probabilità]] (nuova)
- [[Processo di nascita e morte]] (nuova)
- [[Generatore infinitesimale]] (nuova)
- [[Catena di Markov]] — aggiornata con teoria formale: classi comunicanti, ricorrenza, teorema ergodico, catene continue
- [[Distribuzione di Poisson]] — aggiornata con collegamento al processo di Poisson a tempo continuo

**Secondo ingest (2026-05-06, chiusura gap):**
- [[Processo di Poisson (continuo)]] (nuova) — assiomi, $N_t \sim \mathrm{Poi}(\lambda t)$, interarrivi $\mathrm{Exp}(\lambda)$, sovrapposizione/thinning
- [[Catena immersa]] (nuova) — decomposizione struttura + tempi di permanenza, matrice $\Pi_{ij} = Q_{ij}/|Q_{ii}|$
- [[Equazione logistica]] (nuova) — $\dot N = rN(1-N/K)$, limite deterministico di processi nascita-morte
- [[Passeggiata aleatoria]] — aggiunto alias "Rovina del giocatore"

## Fonti

- `raw/appunti/processi.pdf` (24 pp., A.A. 2025/2026)
