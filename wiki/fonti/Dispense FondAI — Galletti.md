---
tipo: fonte
titolo: Dispense FondAI — Galletti
autori: [Galletti, Marco]
corso: Fondamenti di Intelligenza Artificiale
docente: Baccini, Federica
anno-accademico: 2024/2025
pagine: 37
data-ingest: 2026-05-04
file-raw: raw/appunti/fond_ai.pdf
ultima-modifica: 2026-05-04
tag: [fond-ai, logica, agenti, smia]
---

# Dispense FondAI — Galletti

**Riferimento file raw:** `raw/appunti/fond_ai.pdf`
**Docente:** prof.ssa Federica Baccini — SMIA, Sapienza, A.A. 2024/2025
**Redatte da:** Marco Galletti

## Riassunto in 5 punti

1. L'IA classica si divide in approccio **simbolico** (regole formali, logica) e **sub-simbolico** (machine learning). Questo corso copre il simbolico.
2. Un **agente** è definito da una funzione $f: H \to A$ (sequenze percettive → azioni); la razionalità si articola attraverso lo schema PEAS.
3. La **ricerca A*** combina costo percorso $g(n)$ ed euristica ammissibile $h(n) \leq h^*(n)$, garantendo ottimalità; la consistenza $h(n) \leq c(n,a,n') + h(n')$ è condizione più forte.
4. La **logica proposizionale** fornisce il linguaggio per rappresentare conoscenza dichiarativa; conseguenza logica, alberi di Beth e sistema Hilbertiano (HAL) sono i tre metodi di inferenza presentati.
5. La **logica del primo ordine** estende la proposizionale con quantificatori, termini e predicati; l'unificazione (algoritmo di Robinson, mgu) abilita la risoluzione con clausole del primo ordine.

## Struttura (indice)

| § | Titolo | Pagine |
|---|---|---|
| 1 | Introduzione: agenti, PEAS | 1–6 |
| 2 | Ricerca informata: A* | 7–8 |
| 3 | Logica proposizionale | 9–12 |
| 4 | Conseguenza logica e inferenza | 13–14 |
| 5 | Alberi di Beth | 15 |
| 6 | Sistema Hilbertiano (HAL, CNF, RES, Horn) | 16–26 |
| 7 | Logica del primo ordine | 27–37 |

## Argomenti trattati

- [[Agente intelligente]] — PEAS, tipi di agenti e ambienti
- [[Ricerca A*]] — euristica ammissibile, ottimalità, consistenza
- [[Logica proposizionale]] — sintassi, semantica, modelli, tautologie
- [[Conseguenza logica]] — $F_1 \models F_2$, model checking
- [[Alberi di Beth]] — refutazione automatica
- [[Sistema Hilbertiano]] — HAL, derivabilità $\Phi \vdash A$
- [[Risoluzione (RES)]] — CNF, clausola vuota $\bot$, completezza per refutazione
- [[Clausole di Horn]] — definite, fatti, regole, goal
- [[Concatenazione in avanti e all'indietro]] — algoritmi PL-CA
- [[Logica del primo ordine]] — sintassi, semantica, decidibilità, unificazione, Skolem

## Citazioni chiave

> "L'intelligenza artificiale si occupa di comportamento intelligente negli artefatti. Il comportamento intelligente, a sua volta, coinvolge la percezione, il ragionamento, l'apprendimento, il comunicare e l'agire in ambienti complessi." — Nilsson (1998)

> "Un agente si definisce razionale se, per ogni possibile sequenza percettiva, sulla base delle informazioni derivate dalla sequenza percettiva e dalla eventuale conoscenza a priori sull'ambiente, l'agente sceglie l'azione che massimizza il valore atteso della misura della performance."

## Note di lettura

- Il corso copre l'approccio **simbolico** all'IA, complementare al sub-simbolico di [[Machine Learning]].
- La progressione logica: agenti → ricerca nello spazio degli stati → logica come linguaggio di conoscenza → sistemi di inferenza.
- La parte di logica (§3–7) è la più densa: conviene partire da [[Logica proposizionale]] e procedere verso [[Logica del primo ordine]].
- §6 (Sistema Hilbertiano) copre tre sistemi distinti: HAL, alberi di Beth (§5), e RES — tutti metodi per dimostrare conseguenza logica.

## Pagine wiki create/aggiornate

**Create:**
- [[Agente intelligente]], [[Ricerca A*]], [[Logica proposizionale]], [[Conseguenza logica]], [[Alberi di Beth]], [[Sistema Hilbertiano]], [[Risoluzione (RES)]], [[Clausole di Horn]], [[Concatenazione in avanti e all'indietro]], [[Logica del primo ordine]]
- [[Baccini, Federica]]

**Aggiornate:**
- [[Fondamenti di Intelligenza Artificiale]] — 🟡 → 🟢
