---
tipo: corso
titolo: Fondamenti di Intelligenza Artificiale
docente: Federica Baccini
anno-accademico: 2024/2025
codice-breve: fond_ai
ultima-modifica: 2026-05-04
tag: [ai, logica, agenti, smia]
---

# Fondamenti di Intelligenza Artificiale

Corso di **Fondamenti di Intelligenza Artificiale** tenuto dalla prof.ssa **Federica Baccini** nell'A.A. 2024/2025, SMIA, Sapienza. Approccio classico/simbolico (logica + ricerca), come complemento al sub-simbolico di [[Machine Learning]].

## Programma

1. **Introduzione**
   - 1.1 [[Agente intelligente]] — architettura, funzione agente $f: H \to A$, razionalità
   - 1.2 Schema PEAS, tipi di ambienti, tipi di agenti (reattivi, modello, obiettivi, utilità)
   - 1.3 Rappresentazioni atomica/fattorizzata/strutturata; agenti PS vs KB
2. **Ricerca informata: A***
   - 2.1 Best-first greedy: $f(n) = h(n)$
   - 2.2 [[Ricerca A*]]: $f(n) = g(n) + h(n)$, euristica ammissibile $h(n) \leq h^*(n)$, consistenza, ottimalità
3. **Logica come linguaggio per rappresentare conoscenza**
   - 3.1 [[Logica proposizionale]] — sintassi, semantica, modelli, tautologie, CNF
4. **Conseguenza logica e inferenza**
   - 4.1 [[Conseguenza logica]] — $F_1 \models F_2$, model checking $O(2^n)$, sistema di inferenza
5. **Alberi di Beth**
   - 5.1 [[Alberi di Beth]] — refutazione automatica, correttezza e completezza
6. **Sistema Hilbertiano**
   - 6.1 [[Sistema Hilbertiano]] (HAL) — 3 assiomi, modus ponens, $\Phi \vdash A$, teorema di deduzione
   - 6.2 [[Risoluzione (RES)]] — CNF, clausola vuota $\bot$, completezza per refutazione
   - 6.3 Completezza della risoluzione
   - 6.4 Algoritmo PL-RISOLUZIONE
   - 6.5 [[Clausole di Horn]] — definite, fatti, regole, goal
   - 6.6 [[Concatenazione in avanti e all'indietro]] — PL-CA, grafo AND-OR
7. **Logica del primo ordine**
   - 7.1 [[Logica del primo ordine]] — sintassi (termini, predicati, quantificatori), variabili libere/vincolate
   - 7.2 Semantica: struttura $\mathcal{M}$, assegnazione, soddisfacibilità quantificatori
   - 7.3 Decidibilità: LP decidibile, LPO indecidibile (semidecidibile)
   - 7.4 Unificazione: mgu, algoritmo di Robinson, disagreement set
   - 7.5 Forma prenessa, skolemizzazione, risoluzione con mgu

## Concetti centrali

**Agenti e ricerca:**
- [[Agente intelligente]] — PEAS, tipi di agenti, PS vs KB
- [[Ricerca A*]] — euristica ammissibile, ottimalità, consistenza

**Logica proposizionale:**
- [[Logica proposizionale]] — sintassi, semantica, modelli, tautologie
- [[Conseguenza logica]] — $\models$, model checking, sistema di inferenza
- [[Alberi di Beth]] — refutazione automatica
- [[Sistema Hilbertiano]] — HAL, $\vdash$, teorema di deduzione, correttezza/completezza

**Inferenza efficiente:**
- [[Risoluzione (RES)]] — CNF, clausola vuota, completezza per refutazione
- [[Clausole di Horn]] — fatti, regole, goal
- [[Concatenazione in avanti e all'indietro]] — algoritmi lineari

**Logica del primo ordine:**
- [[Logica del primo ordine]] — predicati, quantificatori, decidibilità, unificazione, Skolem

## Persone citate

- [[Baccini, Federica]] — docente
- [[Galletti, Marco]] — autore dispense

## Fonti del corso

- [[Dispense FondAI — Galletti]] — 37 pp., ingest profondo 2026-05-04 ✅

## Stato

🟢 Ingest completo
