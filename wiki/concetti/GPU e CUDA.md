---
tipo: concetto
titolo: GPU e CUDA
tag: [architettura, hardware, cs, gpu, cuda, dsa, parallelismo]
cluster: sistemi
fonti: 1
ultima-modifica: 2026-05-06
---

# GPU e CUDA

## Domain Specific Architectures (DSA)

Con la fine della **Legge di Moore** e del **Dennard Scaling**, le CPU general-purpose non offrono più guadagni di efficienza sufficienti. Le **DSA** (Domain Specific Architectures) sono hardware progettato su misura per un dominio specifico, bilanciando efficienza e programmabilità.

**DSA vs ASIC:**
- **ASIC:** hardware fisso per una singola applicazione, massima efficienza, zero flessibilità.
- **DSA:** accelera un intero dominio (es. ML, grafica, compressione) mantenendo programmabilità.

**Perché i DSA sono più efficienti delle CPU:**
1. **Parallelismo SIMD/VLIW** invece di costoso MIMD.
2. **Memorie locali (scratchpad)** gestite dal software invece di cache automatiche.
3. **Precisione ridotta:** INT8, Float16, Bfloat16 invece di FP32.
4. **Meno overhead:** nessun fetch/decode complesso; più transistor al calcolo.

### Systolic Arrays

Rete regolare di Processing Elements (PE) connessi a griglia. Ogni PE riceve dati dai vicini, esegue un MAC (Multiply-Accumulate) e passa il risultato al ciclo successivo. I dati "scorrono" ritmicamente senza dover accedere alla memoria globale → **massimo riuso** dei dati.

### Double Buffering

Mentre l'unità di calcolo lavora sul buffer A, si caricano i dati successivi nel buffer B. Elimina gli stalli di attesa memoria → unità sempre attive.

## Google TPU (caso di studio)

La **TPU v1** di Google (2015) è progettata per inferenza su Deep Neural Networks. Speedup 15-30× rispetto a CPU/GPU comparabili; efficienza 30-80× migliore.

**Architettura TPU v1:**
- **Matrix Multiply Unit (MXU):** array sistolico 256×256 = 65.536 unità MAC a 8 bit. Fino a 65.536 operazioni per ciclo.
- **Accumulatori (4 MiB):** 4096 vettori da 256 elementi a 32 bit.
- **Unified Buffer (24 MiB):** SRAM on-chip per attivazioni, gestita esplicitamente (scratchpad, non cache).
- **Weight Memory (8 GiB DRAM esterna):** pesi della rete; alimentati tramite Weight FIFO.

**ISA TPU:** CISC compatto (~12 istruzioni), nessun Program Counter interno, CPI alto (10-20 cicli) ma ogni istruzione lancia enorme quantità di lavoro. Istruzioni: `Read_Host_Memory`, `Read_Weights`, `MatrixMultiply/Convolve`, `Activate`, `Write_Host_Memory`.

**Floorplan:** 35% memoria, 35% calcolo (MXU), 12% I/O, 2% controllo (vs CPU/GPU dove il controllo occupa molto più spazio).

### Roofline Model

Strumento per analizzare il collo di bottiglia di un algoritmo:

$$\text{Intensità Aritmetica} = \frac{\text{Operazioni (FLOP)}}{\text{Byte letti dalla memoria}}$$

$$\text{Prestazioni raggiungibili} = \min(\text{Peak BW} \times \text{Intensità},\; \text{Peak FLOP/s})$$

- **Memory-bound** (bassa intensità): prestazioni ∝ banda memoria.
- **Compute-bound** (alta intensità): prestazioni = plateau computazionale.
- **Ridge point:** intensità minima per sfruttare appieno l'unità di calcolo.

La maggior parte delle reti neurali sulla TPU è **memory-bound**: il bottleneck è la banda verso la DRAM dei pesi.

## Architettura GPU

La **GPU** nasce per grafica 3D ad alta definizione, poi adottata per GPGPU (General Purpose GPU): ML, simulazioni, analisi dati.

**CPU vs GPU:**
| | CPU | GPU |
|---|---|---|
| Obiettivo | Latenza minima (singolo thread) | Throughput massimo (tanti thread) |
| Cache | Grande | Piccola |
| Controllo | Branch prediction, forwarding | Semplice |
| ALU | Poche, potenti | Moltissime, efficienti energeticamente |
| Frequenza | Alta | Moderata |

**Struttura interna GPU:**
- **Global Memory:** memoria esterna ad alta banda (GDDR/HBM).
- **Streaming Multiprocessor (SM):** unità base di elaborazione; raggruppa CUDA cores + Shared Memory.
- **CUDA Core:** unità elementare con più ALU; esecuzione SIMD a 16 linee (un'istruzione controlla 16 unità).

## Modello di programmazione CUDA

**CUDA** (NVIDIA): estensioni C/C++ per programmazione GPU general purpose.

### Gerarchia di thread

```
Grid → Blocks → Threads
```

- **Grid:** tutti i thread lanciati per un kernel.
- **Block (Thread Block):** sottogruppo di thread che possono cooperare e sincronizzarsi. Eseguiti su un singolo SM.
- **Thread:** unità di esecuzione atomica.

**Identificatori:** ogni thread conosce `threadIdx`, `blockIdx`, `blockDim`, `gridDim`.

ID globale lineare: `threadID = threadIdx.x + blockIdx.x * blockDim.x`.

**Scalabilità:** i blocchi sono indipendenti e possono essere schedulati in qualsiasi ordine su qualsiasi SM → il codice scala automaticamente su GPU con più SM.

### Memorie CUDA

| Scope | Memoria | Velocità |
|---|---|---|
| Per-Thread | Registri | Velocissima |
| Per-Block | Shared Memory (SRAM on-chip) | Veloce |
| Per-Grid | Global Memory (GDDR/HBM) | Lenta |

**API:** `cudaMalloc`, `cudaMemcpy` (sincrono), `cudaFree` per gestire la Global Memory.

Lancio kernel: `kernel<<<gridDim, blockDim>>>(args)`.

## Warp e SIMD execution

L'hardware raggruppa i thread in **warp** da 32. Tutti i 32 thread di un warp eseguono **la stessa istruzione** simultaneamente (SIMD).

**Control Divergence:** se branch in un warp ha condizione diversa per thread diversi, l'hardware **serializza** i due percorsi → metà delle unità inutilizzata. Minimizzare la divergenza è cruciale.

**Ottimizzazione sum reduction:** usare thread contigui (0..511 attivi) invece di interleaved (0,2,4.. attivi) → warp completamente pieni o completamente vuoti, nessuna serializzazione.

## Tiling e Shared Memory

**Problema:** la moltiplicazione matriciale naïve accede alla Global Memory per ogni elemento — $O(N^3)$ accessi.

**Soluzione (Tiling):**
1. Divide la Global Memory in **tile**.
2. Ogni blocco carica cooperativamente un tile in Shared Memory.
3. I thread eseguono il calcolo dalla Shared Memory (riutilizzano il tile più volte).
4. `__syncthreads()` sincronizza i thread all'interno del blocco: barrier dopo il caricamento (evita letture di dati non ancora scritti) e dopo il calcolo (evita sovrascrittura prematura del tile).

Riduzione accessi Global Memory: da $2 \times \text{Width}$ a $2 \times \text{Width} / \text{TILE\_WIDTH}$ per thread.

**Occupancy vs Shared Memory:** la Shared Memory è limitata (es. 16KB–48KB per SM). Un tile grande riduce la banda verso la Global Memory ma limita il numero di blocchi attivi per SM → bilanciare.

## Bank Conflicts

La Shared Memory è suddivisa in **32 banchi**. Accessi a banchi diversi → paralleli (efficiente). Accessi a banchi **uguali** con indirizzi diversi → **serializzati** (bank conflict). Accesso allo **stesso indirizzo** da più thread → broadcast (efficiente).

Evitare stride che causano conflitti (es. stride 2 con array di float → conflitti; stride 1 → accessi sequenziali a banchi diversi, efficiente).

## Memory Coalescing

L'hardware raggruppa in un'unica transazione gli accessi di un warp alla Global Memory se:
1. Gli indirizzi sono **contigui** (o vicini) nello stesso blocco allineato.
2. L'indirizzo base è un **multiplo** della dimensione del blocco.

Thread che accedono a dati sparsi o disallineati costringono a transazioni multiple → spreco di bandwidth.

Granularità: 128 byte (hit in L1) o 32 byte (hit in L2 / Global).

## Trasferimento Host-Device e Streams

Il bus **PCIe** è il collo di bottiglia nei sistemi eterogenei (CPU+GPU): PCIe Gen3 = 16 GB/s vs DDR4 ≈ 50 GB/s.

`cudaMemcpy` è **sincrono** (bloccante). Per nascondere la latenza PCIe si usano:
- `cudaMemcpyAsync`: asincrono.
- **CUDA Streams:** flussi di esecuzione indipendenti. Dividendo i dati in chunk, si sovrappone (*overlap*) il trasferimento del chunk $i+1$ con il calcolo del chunk $i$ → **pipeline software** che nasconde quasi tutta la latenza PCIe.

## Connessioni

- DSA e roofline: collegamento a [[Multi-Layer Perceptron]], [[Backpropagation]] (ML) — GPU accelera training
- Cache e memoria: [[Gerarchia di memoria e cache]] (shared memory, DRAM, gerarchie)
- SIMD: [[Aritmetica dei computer]] (AVX-512, FMA)
- Calcolo parallelo: [[Gerarchia di memoria e cache]] (Amdahl, Flynn, multithreading)
- Corso: [[Architetture degli Elaboratori]]

## Fonti

- [[Dispense Architetture — Galletti]] (§8-§10, pp. 53-77)
