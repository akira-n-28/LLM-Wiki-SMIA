---
tipo: concetto
titolo: Pipeline e processore
tag: [architettura, hardware, cs, pipeline, processore]
cluster: sistemi
fonti: 1
ultima-modifica: 2026-05-06
---

# Pipeline e processore

## Progettazione del datapath

**Metodologia di clock:** ogni operazione è completata in un ciclo. Il percorso critico (longest path) determina il clock period.

**Stadi della pipeline RISC-V a 5 stadi:**

| Stadio | Sigla | Operazione |
|---|---|---|
| Instruction Fetch | IF | Legge l'istruzione dalla memoria |
| Instruction Decode | ID | Decodifica e legge i registri |
| Execute | EX | Calcola in ALU |
| Memory Access | MEM | Legge/scrive in memoria dati |
| Write Back | WB | Scrive il risultato in un registro |

La pipeline rende ogni stadio un ciclo di clock. Richiede **pipeline registers** tra stadi per memorizzare i valori intermedi. Con pipeline ideale: CPI → 1 (vs CPI > 1 del ciclo singolo).

## Hazard

Situazioni che impediscono l'esecuzione dell'istruzione successiva nel ciclo atteso.

### Hazard strutturali

Conflitto su una risorsa hardware (es. un'unica memoria per istruzioni e dati). Soluzione: memorie separate (instruction cache + data cache).

### Hazard sui dati

Un'istruzione dipende dal risultato di una precedente ancora in pipeline.

**Data forwarding (bypassing):** il risultato viene passato direttamente dall'output di EX/MEM all'input di EX senza attendere WB. Risolve la maggior parte dei RAW (Read After Write).

**Load-use hazard:** un `ld` seguito immediatamente da un'istruzione che usa il dato caricato non è risolvibile con il forwarding (il dato è disponibile solo dopo MEM). Il compilatore o l'hardware inserisce uno **stall** (bolla) di 1 ciclo.

### Hazard di controllo (branch hazard)

Bisogna attendere che la condizione del branch sia calcolata per sapere quale istruzione prelevare.

**Soluzioni:**
1. **Stall:** attesa. Semplice ma spreca 1-3 cicli per branch.
2. **Anticipare in ID:** hardware aggiuntivo in ID per calcolare target (sommatore PC+offset) e confrontare i registri → penalità ridotta a **1 ciclo**.
3. **Branch prediction:**
   - *Static:* predict-not-taken, predict-taken, backward-taken/forward-not-taken. Semplice.
   - *Dynamic:* Branch History Table (BHT) con predittore a **1 bit** (ricorda ultimo esito) o **2 bit** (automa a 4 stati: Strongly Not Taken → Weakly NT → Weakly Taken → Strongly Taken). Riduce drasticamente le penalità su loop.

## Instruction Level Parallelism (ILP)

Due tecniche per aumentare l'ILP:

1. **Pipeline più profonda:** più stadi → frequenza di clock più alta, ma più penalità da hazard.
2. **Multiple issue (pipeline più larga):** più istruzioni per ciclo.

### Multiple Issue statico (VLIW)

Il **compilatore** raggruppa istruzioni in pacchetti (es. dual-issue: 1 ALU + 1 load/store per ciclo). Richiede scheduling statico aggressivo, loop unrolling e register renaming. Limite: stalli da latenze imprevedibili (cache miss).

Esempio dual-issue: IPC teorico = 2, pratico ≈ 1.25-1.75 con loop unrolling×4.

### Multiple Issue dinamico (Superscalare)

La **CPU** decide dinamicamente quante istruzioni emettere in ogni ciclo in base a risorse e dipendenze. Il compilatore può ottimizzare ma la correttezza è garantita dall'hardware → compatibilità binaria.

## Esecuzione fuori ordine (Out-of-Order)

Per nascondere stalli (es. cache miss), la CPU esegue istruzioni **fuori ordine** ma le **committe in ordine**:

1. **In-order Issue:** prelievo e decodifica in ordine.
2. **Out-of-order Execute:** le istruzioni sono eseguite appena gli operandi sono pronti e un'unità funzionale è libera.
3. **In-order Commit:** i risultati sono scritti nei registri architetturali in ordine di programma (garantisce correttezza su eccezioni e misprediction).

**Componenti:**
- **Reservation Stations:** buffer che attendono gli operandi per ogni unità funzionale.
- **Reorder Buffer (ROB):** riordina i risultati per il commit in-order.
- **Functional Units:** ALU, FP, Load/Store — operano in parallelo.

## Register Renaming

Elimina le **dipendenze fittizie** (WAR: Write After Read, WAW: Write After Write) causate dal riutilizzo degli stessi nomi di registro da parte del compilatore. La CPU mappa dinamicamente i registri architetturali (32 visibili) a un insieme più ampio di **registri fisici**. Ogni nuova scrittura su `x1` usa una nuova locazione fisica; le letture precedenti continuano a vedere il "vecchio" valore.

## Limiti del Multiple Issue

- **Dipendenze reali** dell'algoritmo (non eliminabili).
- **Finestra di issue limitata:** la CPU può analizzare solo N istruzioni alla volta.
- **Memory bottleneck:** cache miss riduce la banda di istruzioni disponibili.
- **Costo della speculazione:** branch prediction sbagliata spende energia per istruzioni scartate.

## Connessioni

- ISA: [[Architettura RISC-V]]
- Memoria e cache: [[Gerarchia di memoria e cache]]
- Parallelismo e multi-core: [[Gerarchia di memoria e cache]] (§7)
- GPU e scheduling: [[GPU e CUDA]]
- Corso: [[Architetture degli Elaboratori]]

## Fonti

- [[Dispense Architetture — Galletti]] (§4, pp. 24-36)
