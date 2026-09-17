---
tipo: corso
titolo: Ottimizzazione
docente: Marco Sciandrone
anno-accademico: 2024/2025
codice-breve: ottimizzazione
ultima-modifica: 2026-05-04
tag: [ottimizzazione, matematica-applicata, smia]
---

# Ottimizzazione

Corso di **Ottimizzazione** tenuto dal prof. **Marco Sciandrone** nell'A.A. 2024/2025, SMIA, Sapienza.

## Programma

1. **Introduzione**
   - 1.1 [[Problema di ottimizzazione]] (formulazione, esempi, classificazione)
   - 1.2 [[Convessità]] di insiemi e funzioni
   - 1.3 Esistenza di soluzione (Weierstrass, coercività)
   - 1.4 [[Minimi quadrati]] (caso rank pieno e rank deficiente)
   - 1.5 [[Condizioni di ottimalità]] (1° e 2° ordine, caso convesso)
2. **Algoritmi di ottimizzazione**
   - 2.1 Schema generale $x_{k+1} = x_k + s_k$, convergenza (finita, asintotica, locale/globale)
3. **Ottimizzazione non vincolata**
   - 3.1 Classificazione (line search, trust region, ricerca diretta)
   - 3.2 Condizioni di convergenza globale (funzione di forzamento, condizione d'angolo)
   - 3.3 Ricerca unidimensionale esatta (caso quadratico)
   - 3.4 [[Metodo di Armijo]] (line search inesatta)
   - 3.5 [[Discesa del gradiente|Steepest descent]] (direzione antigradiente normalizzata)
4. **Problema dell'addestramento di reti neurali**
   - 4.1 [[Discesa del gradiente|Gradiente con passo costante]] (lemma di discesa, μ < 2/L)
   - 4.2 [[Gradiente coniugato]] (Fletcher-Reeves, convergenza in n iterazioni)
   - 4.3 [[Metodo di Newton (ottimizzazione)]] (convergenza locale superlineare/quadratica)
5. **Metodi incrementali**
   - 5.1 Minimi quadrati ricorsivi (Sherman-Morrison per $H^{-1}$)
   - 5.2 [[Regressione logistica]] (convessità della cross-entropy loss)
   - [[Algoritmo del percettrone]]
6. **Problemi a larga scala**
   - 6.1 [[Metodi Quasi-Newton]] (BFGS, L-BFGS)
   - 6.2 [[Condizioni di ottimalità|Ottimizzazione vincolata]] (direzioni ammissibili, S convesso)
   - 6.3 [[Proiezione su insiemi convessi]]
   - 6.4 [[Frank-Wolfe e gradiente proiettato|Metodo di Frank-Wolfe]]
   - 6.5 [[Frank-Wolfe e gradiente proiettato|Gradiente proiettato]]
   - [[Condizioni KKT]] (Fritz-John, KKT, condizioni di regolarità)

## Concetti centrali

**Fondamenti teorici:**
- [[Problema di ottimizzazione]] — classificazione, min locale/globale, coercività
- [[Convessità]] — la proprietà chiave per garantire min locale = globale
- [[Condizioni di ottimalità]] — ∇f = 0, Hessiana SDP/DP, caso vincolato

**Algoritmi non vincolati:**
- [[Discesa del gradiente]] — steepest descent, passo costante, convergenza con L-Lipschitz
- [[Metodo di Armijo]] — line search inesatta, decremento sufficiente
- [[Gradiente coniugato]] — Fletcher-Reeves, convergenza in ≤n iterazioni
- [[Metodo di Newton (ottimizzazione)]] — convergenza quadratica locale, Newton troncato

**Metodi incrementali e larga scala:**
- [[Algoritmo del percettrone]] — classificazione lineare, regola di aggiornamento
- [[Stochastic Gradient Descent]] — SGD/mini-batch come metodo incrementale
- [[Metodi Quasi-Newton]] — L-BFGS per n ≥ 10⁴

**Ottimizzazione vincolata:**
- [[Proiezione su insiemi convessi]] — operatore p(x), non espansività
- [[Frank-Wolfe e gradiente proiettato]] — due metodi per S convesso
- [[Condizioni KKT]] — Fritz-John, condizioni necessarie/sufficienti, complementarità

## Persone citate

- [[Sciandrone, Marco]] — docente
- [[Galletti, Marco]] — autore dispense
- [[Karush, William]], [[Kuhn, Harold]], [[Tucker, Albert]] — condizioni KKT
- [[Fletcher, Roger]] — formula Fletcher-Reeves per gradiente coniugato
- [[Newton, Isaac]] — metodo di Newton

## Fonti del corso

- [[Dispense Ottimizzazione — Galletti]] — 56 pp., ingest profondo 2026-05-04 ✅

## Stato

🟢 Ingest completo
