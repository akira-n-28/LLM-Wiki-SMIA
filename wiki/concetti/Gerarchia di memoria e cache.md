---
tipo: concetto
titolo: Gerarchia di memoria e cache
tag: [architettura, hardware, cs, memoria, cache, multicore]
cluster: sistemi
fonti: 1
ultima-modifica: 2026-05-06
---

# Gerarchia di memoria e cache

## Principio di località

- **Temporale:** dati acceduti recentemente è probabile vengano riacceduti a breve.
- **Spaziale:** dati vicini a quelli acceduti recentemente è probabile vengano acceduti a breve.

Da qui nasce la gerarchia:

```
CPU → SRAM (Cache) → DRAM (Main Memory) → Disco (Storage)
        piccola, veloce    più grande, più lenta    enorme, lentissima
```

## Terminologia

- **Blocco (linea):** unità di trasferimento tra livelli. Può contenere più word.
- **Hit:** il dato è presente nel livello superiore — accesso rapido.
- **Miss:** il dato non c'è — bisogna caricarlo dal livello inferiore (*miss penalty*).
- **Hit ratio** = $\text{hit}/\text{accessi totali}$; **Miss rate** = $1 - \text{Hit ratio}$.

## Tecnologia DRAM

Ogni cella = condensatore + transistor. Deve essere periodicamente **rinfrescata** (dati persi se il condensatore si scarica). La lettura scarica il condensatore → richiede riscrittura.

Accesso a un'intera riga (burst mode) è efficiente; accesso a righe diverse è costoso. Varianti: **SDRAM** (sincrona con clock), **DDR** (Double Data Rate — trasferisce su entrambi i fronti del clock).

## Cache direct-mapped

Ogni blocco di memoria può mappare **in una sola posizione** della cache.

**Suddivisione dell'indirizzo:**
- **Offset** (bit meno significativi): byte nel blocco.
- **Index:** riga della cache; `Index = (Block Address) mod (#Blocks)`.
- **Tag:** bit rimanenti, memorizzati nella cache per identificare quale blocco è presente.

Ogni riga ha anche un **Valid bit** (0 = vuota).

**Accesso:** legge la riga con l'Index, confronta Tag e Valid bit → hit se entrambi corrispondono.

**Limite:** *conflict miss* — due blocchi con stesso Index si contendono la posizione anche se la cache non è piena.

## Average Memory Access Time (AMAT)

$$\text{AMAT} = \text{Hit Time} + \text{Miss Rate} \times \text{Miss Penalty}$$

Con cache L1 e L2:
$$\text{CPI} = \text{CPI base} + (\text{Miss Rate}_{L1} \times \text{Penalty}_{L1}) + (\text{Global Miss Rate} \times \text{Penalty}_{L2})$$

Esempio: base CPI=1, miss rate L1=2%, penalty L1=20 cicli, global miss rate=0.5%, penalty L2=400 cicli → CPI=3.4 (vs 9 senza L2). L1 abbassa l'hit time; L2 abbassa il miss rate.

## Cache associativa

**N-way Set Associative:** la cache è divisa in **set**, ognuno con $N$ linee (vie). Il blocco mappa a un set specifico (`Block Address mod #Sets`) ma può occupare qualsiasi delle $N$ vie.

**Fully Associative:** un blocco va in qualsiasi posizione — massima flessibilità, richiede $N$ comparatori.

**Trade-off:** più associatività → meno conflict miss ma hit time maggiore (più logica di selezione).

### Politiche di rimpiazzo

- **LRU (Least Recently Used):** rimpiazza il blocco usato meno recentemente. Sfrutta la località temporale.
- **Random:** semplice in hardware; performance vicina a LRU per associatività alta.

## Gestione delle scritture

### Write Hit

| Politica | Comportamento | Pro/Contro |
|---|---|---|
| **Write-Through** | Scrive in cache **e** in memoria simultaneamente | Semplice; penalizza CPI (lento come DRAM) → usa **Write Buffer** |
| **Write-Back** | Scrive **solo in cache**; dirty bit; write in memoria solo all'eviction | Veloce, meno traffico; inconsistenza temporanea |

### Write Miss

- **Write Allocate** (tipico con Write-Back): carica il blocco in cache, poi modifica.
- **No-Write Allocate** (tipico con Write-Through): scrive direttamente in memoria senza caricare in cache.

## Le 3C (Three Sources of Misses)

| Tipo | Causa | Riduzione |
|---|---|---|
| **Compulsory** (Cold Start) | Primo accesso a un blocco | Aumentare dimensione blocco (prefetching) |
| **Capacity** | Cache troppo piccola per il working set | Aumentare dimensione cache |
| **Conflict** | Troppi blocchi sullo stesso set | Aumentare associatività |

Ogni mitigazione ha un costo: blocchi più grandi → miss penalty maggiore; cache più grande → hit time maggiore; più associatività → hit time maggiore + complessità hardware.

## Gerarchia multi-livello e memorie moderne

I processori moderni hanno 3 livelli: **L1** (privata, ~KB, ~cicli), **L2** (privata, ~MB), **L3** (condivisa tra core, ~decine MB).

CPU out-of-order: un cache miss non blocca tutto — le istruzioni indipendenti proseguono mascherando parte della latenza.

**Cache e software:** l'algoritmo influisce sull'efficienza. Quicksort (accesso contiguo) spesso batte Radix Sort (accesso sparso) in pratica nonostante $O(N)$ vs $O(N\log N)$. DGEMM con **blocking/tiling**: si divide la matrice in tile che entrano interamente in cache, massimizzando il riuso temporale.

## Multicore e cache coherence (§7)

In sistemi multi-core, ogni core ha la propria cache L1/L2 ma condivide L3 e memoria. Problema: due core possono avere **copie diverse dello stesso dato**.

### Snooping protocols

Ogni cache monitora il bus condiviso.

**Write Invalidate Protocol (più comune):**
1. Lettura → carica il blocco (stato Shared).
2. Scrittura → invia **Invalidate** sul bus → tutte le altre copie diventano Invalid.
3. Chi invalida dovrà rileggere dalla cache che ha il dato aggiornato.

**False Sharing:** due variabili *diverse* nella stessa cache line → la scrittura di una invalida la line dell'altro core, che subisce un miss anche se la sua variabile non è cambiata. Soluzione: allineare le strutture dati ai confini della cache line.

## Parallelismo e Legge di Amdahl

$$\text{Speedup} = \frac{1}{(1 - F_p) + \frac{F_p}{N}}$$

dove $F_p$ = frazione parallelizzabile, $N$ = numero processori. L'overhead sequenziale $(1-F_p)$ è il **limite invalicabile** dello speedup, indipendentemente da quanti processori si aggiungono.

## Tassonomia di Flynn

| | Single Data | Multiple Data |
|---|---|---|
| **Single Instruction** | SISD (sequenziale classico) | SIMD (GPU, AVX) |
| **Multiple Instruction** | MISD (raro) | MIMD (multiprocessore) |

**SPMD** (Single Program Multiple Data): modello di programmazione più comune su MIMD — stesso programma su tutti i core, ognuno elabora una porzione diversa di dati.

## Multithreading hardware

Permette più flussi di controllo (thread) sullo stesso core fisico, mascherando latenze di memoria.

| Tipo | Cambio thread | Quando |
|---|---|---|
| **Fine-grain** | Ad ogni ciclo di clock | Thread sempre pronto → massima latenza hidden |
| **Coarse-grain** | Solo su stall lunghi (es. cache miss L2) | Meno overhead di cambio |
| **SMT** (Simultaneous Multithreading) | Emette istruzioni da più thread nello stesso ciclo | Massima occupazione unità funzionali |

Intel Hyper-Threading è un'implementazione SMT: replica PC e registri per 2 thread; unità funzionali condivise.

## Reti di interconnessione

Topologie: Bus (semplice, banda limitata), Ring, 2D Mesh, N-cube (ipercubo), Fully Connected.

Metriche: **Latenza** (singolo messaggio), **Bandwidth** (totale), **Bisection Bandwidth** (collo di bottiglia tagliando la rete in due).

## Connessioni

- Pipeline: [[Pipeline e processore]]
- GPU e parallelismo SIMD: [[GPU e CUDA]]
- Aritmetica: [[Aritmetica dei computer]] (IEEE 754, FP)
- Metodi Numerici: [[Numeri di macchina e aritmetica floating-point]]
- Corso: [[Architetture degli Elaboratori]]

## Fonti

- [[Dispense Architetture — Galletti]] (§6-§7, pp. 39-52)
