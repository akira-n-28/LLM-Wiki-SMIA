---
tipo: fonte
titolo: Dispense MMFII — Galletti
autori: [Marco Galletti]
docente-corso: [Francesco Zamponi]
anno-accademico: 2024/2025
data-ingest: 2026-05-06
file-raw: raw/appunti/mmfII.pdf
pagine: 59
ultima-modifica: 2026-05-06
tag: [mmf, fisica-statistica, probabilità, cs]
---

# Dispense di Modelli Matematici per la Fisica II — Galletti

**Riferimento file raw:** `raw/appunti/mmfII.pdf`  
**Corso:** [[Modelli Matematici per la Fisica II]] (prof. Francesco Zamponi, A.A. 2024/2025, SMIA Sapienza)  
**Autore appunti:** [[Galletti, Marco]]

## Riassunto in 5 punti

1. **Probabilità avanzata**: TLC dimostrato via MGF/cumulanti ($\kappa_l(\hat{S}_n)\to 0$ per $l\geq 3$); teoria delle grandi deviazioni — bound $P(u_n\geq u)\leq e^{-n\Omega(u)}$, distribuzione di Gumbel (code leggere), Fréchet (Pareto).
2. **Entropia di Shannon**: $H(X)=-\sum p_i\log_2 p_i\in[0,\log_2 L]$; informazione mutua $I(X;Y)=H(X)+H(Y)-H(X,Y)\geq 0$; divergenza KL $D_{KL}(p\|q)\geq 0$.
3. **Principio di massima entropia (MaxEnt)**: distribuzione che massimizza $S=-\sum p_x\log p_x$ con vincoli $\mathbb{E}[g_\alpha]=\bar{g}_\alpha$ è $p_x\propto e^{\sum\lambda_\alpha g_\alpha(x)}$ (distribuzione di Boltzmann-Gibbs).
4. **Modello di Ising 1D**: $H=-h\sum\sigma_i - J\sum\sigma_i\sigma_{i+1}$; matrice di trasferimento $Z=\text{Tr}(T^N)$; rappresentazione spettrale $\lambda_\pm$; magnetizzazione; correlazioni $C_{ij}=e^{-r/\xi}$ (decadimento esponenziale, no transizione di fase in 1D).
5. **Campo medio e Hopfield**: Curie-Weiss (fully connected) — equazione $m=\tanh(\beta(Jm+h))$, transizione di fase $T_c=J$, biforcazione; Hopfield — regola di Hebb, memoria associativa, attrattori.

## Argomenti trattati

### §1 Richiami di probabilità (pp. 1-18)
- [[Funzione generatrice dei momenti]] — cumulanti, arricchita con dimostrazione TLC e grandi deviazioni
- [[Teoria delle grandi deviazioni]] — bound di Cramér, funzione di tasso $\Omega_X$, Gumbel, Fréchet

### §2 Entropia (pp. 19-26)
- [[Entropia di Shannon]] — $H(X)$, proprietà, info mutua, DKL

### §3 Principio di massima entropia (pp. 27-32)
- [[Principio di massima entropia]] — MaxEnt, distribuzione di Boltzmann-Gibbs

### §4 Sistemi di più variabili aleatorie (pp. 33-44)
- [[Modello di Ising]] — Hamiltoniana, matrice di trasferimento, autovalori, magnetizzazione, correlazioni

### §5 Sistemi multidimensionali (pp. 45-59)
- [[Modello di Curie-Weiss e Hopfield]] — campo medio, transizione di fase, Hopfield, regola di Hebb

## Note di lettura

- Il §1 è un ripasso di probabilità con materiale avanzato (grandi deviazioni, Gumbel, Fréchet) non trattato in ProbStat.
- §2-3 trattano entropia in senso fisico-informazionale: utile ponte tra [[Entropia di Shannon]] e [[Divergenza di Kullback-Leibler]] (già vista in ML).
- §4-5 è il nucleo del corso: fisica statistica tramite modelli a spin. Il Modello di Hopfield collega direttamente a [[Recurrent Neural Network]] e memoria associativa.

## Pagine wiki aggiornate da questa ingest

**Ingest profondo (2026-05-06):**

*Create — concetti (5):*
- [[Teoria delle grandi deviazioni]] (nuova)
- [[Entropia di Shannon]] (nuova)
- [[Principio di massima entropia]] (nuova)
- [[Modello di Ising]] (nuova)
- [[Modello di Curie-Weiss e Hopfield]] (nuova)

*Aggiornata — concetto esistente (1):*
- [[Funzione generatrice dei momenti]] — aggiunta sezione cumulanti, dimostrazione TLC, link grandi deviazioni

*Infrastruttura:*
- [[Modelli Matematici per la Fisica II]] (corso) — 🟡→🟢

## Fonti
- `raw/appunti/mmfII.pdf`
