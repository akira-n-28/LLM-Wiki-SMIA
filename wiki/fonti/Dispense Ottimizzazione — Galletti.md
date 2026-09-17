---
tipo: fonte
titolo: Dispense Ottimizzazione — Galletti
autori: [Galletti, Marco]
docente: Sciandrone, Marco
corso: Ottimizzazione
anno-accademico: 2024/2025
pagine: 56
file-raw: raw/appunti/ottimizzazione.pdf
data-ingest: 2026-05-04
ultima-modifica: 2026-05-04
---

# Dispense Ottimizzazione — Galletti

**Riferimento file raw:** `raw/appunti/ottimizzazione.pdf`

Dispense di **56 pagine** redatte da Marco Galletti per il corso di Ottimizzazione del prof. Marco Sciandrone, A.A. 2024/2025, corso di laurea SMIA, Sapienza di Roma.

## Riassunto in 5 punti

1. **Fondamenti** (§1): classificazione dei problemi (LP, NLP, convesso/non convesso), condizioni di esistenza (Weierstrass, coercività), condizioni di ottimalità del 1° e 2° ordine (∇f = 0, Hessiana SDP/DP).
2. **Algoritmi line search** (§3): schema generale $x_{k+1} = x_k + \alpha_k d_k$, convergenza globale con funzione di forzamento e condizione d'angolo, metodo di Armijo per la scelta di $\alpha_k$.
3. **Reti neurali come problema di ottimizzazione** (§4): SGD/mini-batch/batch, gradiente coniugato (Fletcher-Reeves), metodo di Newton, Newton troncato per larga scala.
4. **Metodi incrementali** (§5): percettrone, minimi quadrati ricorsivi con aggiornamento Sherman-Morrison per $H^{-1}$, regressione logistica (loss convessa).
5. **Larga scala e vincolato** (§6): L-BFGS, direzioni ammissibili, condizioni KKT (Fritz-John → KKT), proiezione su convessi, Frank-Wolfe, gradiente proiettato.

## Struttura (indice)

1. Introduzione — problemi di ottimizzazione, convessità, esistenza, minimi quadrati, condizioni ottimalità (pp. 2-23)
2. Algoritmi di ottimizzazione — schema generale, convergenza (pp. 24)
3. Ottimizzazione non vincolata — classificazione algoritmi, convergenza globale, Armijo, steepest descent (pp. 25-30)
4. Addestramento reti neurali — batch/SGD, gradiente con passo costante, gradiente coniugato, Newton (pp. 30-38)
5. Metodi incrementali — percettrone, minimi quadrati ricorsivi, regressione logistica (pp. 38-42)
6. Problemi a larga scala — quasi-Newton, vincolato, proiezione, Frank-Wolfe, gradiente proiettato, KKT (pp. 43-56)

## Citazioni chiave

> "Gli algoritmi sono figli delle condizioni di ottimalità." — §1.5

> "Il metodo di Newton troncato: non risolviamo il sistema lineare con soluzioni esatte, dato che sarebbe troppo costoso." — §6

> "L-BFGS è il miglior metodo quasi-Newton per problemi a larga scala." — §6.1

## Pagine wiki create/aggiornate da questa ingest

**Create:**
- [[Problema di ottimizzazione]]
- [[Convessità]]
- [[Condizioni di ottimalità]]
- [[Metodo di Armijo]]
- [[Gradiente coniugato]]
- [[Metodo di Newton (ottimizzazione)]]
- [[Condizioni KKT]]
- [[Proiezione su insiemi convessi]]
- [[Frank-Wolfe e gradiente proiettato]]
- [[Algoritmo del percettrone]]
- [[Metodi Quasi-Newton]]

**Aggiornate:**
- [[Discesa del gradiente]] (aggiunto: steepest descent, convergenza Lipschitz, lemma di discesa, Armijo)

## Note di lettura

Le dispense sono dense e ricche di esempi applicativi (XOR, reti neurali, clustering, MRI). Il filo conduttore è la convessità come condizione di tractabilità: dove $f$ è convessa ogni minimo locale è globale e ∇f = 0 è condizione sufficiente. La sezione sulle reti neurali mette in scena direttamente i metodi (CG, Newton) sull'ottimizzazione dei pesi.
