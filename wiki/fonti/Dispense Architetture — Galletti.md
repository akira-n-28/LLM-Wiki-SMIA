---
tipo: fonte
titolo: Dispense Architetture — Galletti
autori: [Marco Galletti]
docente-corso: Salvatore Pontarelli
anno-accademico: 2025/2026
data-ingest: 2026-05-06
file-raw: raw/appunti/architetture.pdf
pagine: 77
ultima-modifica: 2026-05-06
tag: [architettura, hardware, cs]
---

# Dispense di Architetture degli Elaboratori — Galletti

**Riferimento file raw:** `raw/appunti/architetture.pdf`
**Corso:** [[Architetture degli Elaboratori]] (prof. Salvatore Pontarelli, A.A. 2025/2026, SMIA Sapienza)
**Autore appunti:** [[Galletti, Marco]]

## Riassunto in 5 punti

1. **ISA e RISC-V:** L'ISA è l'interfaccia hardware-software. RISC-V usa 32 registri a 64 bit, istruzioni a 32 bit con formati R/I/S/B a posizione fissa dei campi registro. Performance = IC × CPI / clock rate. Il power wall ha spinto verso il multicore.
2. **Aritmetica:** Complemento a 2 per gli interi; IEEE 754 (bias, normalizzazione, NaN/Inf) per floating point; addizione FP (allinea, somma, normalizza, arrotonda); moltiplicazione FP (somma esponenti, moltiplica significande). SIMD (SSE/AVX/AVX-512) esegue operazioni in parallelo su vettori larghi fino a 512 bit.
3. **Pipeline e ILP:** Pipeline a 5 stadi (IF/ID/EX/MEM/WB) raggiunge CPI≈1; hazard strutturali, dati (risolti con forwarding) e di controllo (risolti con branch prediction a 1/2 bit). Multiple issue (statico VLIW, dinamico superscalare), out-of-order execution con ROB e reservation stations, register renaming.
4. **Memoria e cache:** Gerarchia disco→DRAM→cache (SRAM). Direct-mapped cache con Tag/Index/Offset; AMAT = HitTime + MissRate × MissPenalty; N-way set associative; LRU; write-through vs write-back; 3C (compulsory/capacity/conflict). Multi-core: cache coherence con snooping (write invalidate), false sharing, Legge di Amdahl, tassonomia di Flynn, SMT.
5. **DSA, TPU e GPU:** DSA vs ASIC; systolic arrays; roofline model (memory-bound vs compute-bound); TPU v1 (MXU 256×256, unified buffer, ISA CISC, 35% area calcolo, 35% memoria); GPU GPGPU (SM, CUDA core, warp 32 thread, SIMD, control divergence); CUDA (grid/block/thread, shared memory, tiling, bank conflicts, coalescing, streams asincrone).

## Argomenti trattati

### §1 Introduzione (pp. 2-5)
- ISA: stati, operazioni, control flow, procedure; stack software applicazioni→assembly→hardware
- Response time e throughput; CPU time; CPU clock (clock period, clock rate)
- CPU time = IC × CPI / clock rate; CPI pesato; dipendenza da algoritmo/linguaggio/compilatore/ISA
- Power = $C \cdot V^2 \cdot f$; power wall; passaggio a multi-core

### §2 Rappresentazione delle istruzioni (pp. 6-12)
- 32 bit a formato fisso; formati R, I, S, B (immediatici spezzati, LSB implicito nei branch)
- Opcodes principali (R-type ALU, I-type, load, store, branch, jal, jalr)
- Registri RISC-V; operazioni memoria (ld/sd/lw/lb/lbu); control flow (j, beq, bne, blt)
- Strutture dati: array, struct, layout memoria
- Procedure: jal/jr, ABI (ra, sp, a0-a7, t0-t6 caller-saved, s0-s11 callee-saved), stack frame, chiamate annidate

### §3 Aritmetica dei computer (pp. 13-23)
- Complemento a 2: rappresentazione signed/unsigned; negazione $-x = \bar{x} + 1$; overflow
- Moltiplicazione binaria in colonna; circuito shift-and-add (32 cicli); istruzioni mul/mulh/mulhu/mulhsu; rilevamento overflow
- Divisione binaria; algoritmo restoring; istruzioni div/rem/divu/remu; gestione zero
- IEEE 754: single/double precision, bias, normalizzazione, NaN, ±∞, denormalizzati
- Addizione FP (allinea esponenti, somma, normalizza, arrotonda); Floating point adder hardware
- Moltiplicazione FP (somma esponenti, moltiplica significande, corregge segno); FMA; non associatività
- Istruzioni FP RISC-V (f0-f31, flw/fld, fsw/fsd, fadd/fsub/fmul/fdiv/fsqrt, feq/flt/fgt)

### §4 Progettazione di un processore (pp. 24-36)
- Metodologia di clock; percorso critico
- Datapath a ciclo singolo; pipeline a 5 stadi (IF/ID/EX/MEM/WB) con pipeline registers
- Hazard strutturali (memorie separate)
- Hazard dati: forwarding (EX-EX, MEM-EX); load-use hazard → stall 1 ciclo
- Hazard di controllo: stall; anticipare la decisione in ID (penalità 1 ciclo); branch prediction statica (predict-not-taken, predict-taken, backward-taken); branch prediction dinamica (BHT, 1-bit, 2-bit state machine)
- ILP: pipeline più profonda; multiple issue (VLIW statico, dual-issue scheduling, loop unrolling; superscalare dinamico)
- Out-of-order execution: reservation stations, reorder buffer (ROB), commit in-order
- Register renaming: elimina WAR/WAW; mapping architetturale→fisico

### §5 Istruzioni vettoriali SIMD (pp. 37-38)
- SIMD overview; SSE 128-bit (xmm, 4 float / 2 double), AVX 256-bit (ymm), AVX-512 512-bit (zmm, maschere k0-k7)
- Vectorization; auto-vectorization; intrinsics C; loop unrolling ×4 + AVX-512 → 32 double/iterazione

### §6 Le memorie (pp. 39-46)
- Principio di località (temporale e spaziale); gerarchia (cache SRAM → DRAM → disco); blocchi/linee
- Hit/miss/hit ratio/miss rate; DRAM: condensatore, burst mode, SDRAM, DDR
- Cache direct-mapped: Tag/Index/Offset; valid bit; conflict miss
- Dimensione blocchi: trade-off miss rate vs miss penalty; Early Restart; Critical Word First
- Write-through (write buffer) vs write-back (dirty bit); write allocate vs no-write allocate
- AMAT = HitTime + MissRate × MissPenalty; L1+L2: CPI con due livelli
- N-way set associative; fully associative; LRU vs Random; 3C (cold/capacity/conflict)
- Design trade-offs: ↑cache size → ↓capacity miss ↑hit time; ↑assoc → ↓conflict miss ↑hit time; ↑block size → ↓compulsory miss ↑miss penalty

### §7 Processori multi-core e cache coherence (pp. 47-52)
- Cache coherence in sistemi multi-core; snooping protocols; Write Invalidate Protocol; falso sharing
- Parallelismo: task-level; parallel processing program
- Legge di Amdahl: $\text{Speedup} = 1/[(1-F_p) + F_p/N]$; limite sequenziale
- Tassonomia di Flynn: SISD/SIMD/MISD/MIMD; SPMD
- Multithreading hardware: fine-grain, coarse-grain, SMT (Simultaneous Multithreading)
- SMP (UMA/NUMA); lock e istruzioni atomiche; sum reduction parallela (riduzione ad albero, log₂N passi)
- Message passing e cluster; reti di interconnessione (bus, ring, 2D mesh, N-cube); latenza, bandwidth, bisection BW

### §8 Architetture specifiche per dominio (pp. 53-55)
- Motivazioni (fine Moore/Dennard); DSA vs ASIC
- Perché i DSA sono efficienti: parallelismo SIMD, memorie locali, precisione ridotta, meno overhead
- Systolic arrays; double buffering
- Programmazione DSA: framework (TensorFlow, PyTorch, Halide), compilatori specializzati
- Memory wall negli acceleratori; compressione dati (sparse, quantizzazione)
- Istruzioni specializzate (HMMA su GPU) vs acceleratori dedicati (TPU)

### §9 Google TPU: caso di studio (pp. 56-59)
- DNN: neuroni, MLP (GEMM), CNN (stencil/convoluzione); batching, quantizzazione
- TPUv1: coprocessore PCIe; MXU 256×256 MAC INT8; accumulatori 4MiB; unified buffer 24MiB; weight memory 8GiB DRAM; weight FIFO
- ISA CISC (~12 istruzioni); nessun PC; CPI alto; floorplan (35% memoria, 35% calcolo, 2% controllo)
- Roofline model: intensità aritmetica; memory-bound vs compute-bound; ridge point; TPU workload memory-bound
- Linee guida DSA: dati ridotti, meno overhead, memorie dedicate, parallelismo semplice, DSL

### §10 GPU (pp. 60-77)
- CPU vs GPU: latenza vs throughput; struttura GPU (global memory, SM, CUDA core, shared memory)
- CUDA: gerarchia grid→block→thread; threadIdx/blockIdx/blockDim; ID globale; scalabilità
- Memorie: registri (thread), shared memory (block), global memory (grid)
- Warp (32 thread); SIMD a 16 linee; control divergence e serializzazione; sum reduction ottimizzata
- Matrix multiply in CUDA; tiling (shared memory, __syncthreads(), Sync 1 + Sync 2)
- Occupancy vs shared memory: tile grande → meno accessi global, ma meno blocchi per SM
- Shared memory banks: 32 banchi; bank conflict; broadcast/multicast
- Memory coalescing: accessi contigui allineati → 1 transazione; sparsi/disallineati → transazioni multiple
- Host-device transfer: PCIe bottleneck; cudaMemcpy sincrono vs async; CUDA Streams; overlap calcolo+trasferimento

## Note di lettura

- Il §4 (pipeline) e il §10 (GPU/CUDA) sono i capitoli più densi e pratici — contengono molto codice assembly e CUDA.
- Il §3 (floating point) è il collegamento diretto a [[Numeri di macchina e aritmetica floating-point]] (Metodi Numerici).
- Il §9 (TPU) e il §10 (GPU) sono estremamente rilevanti per chiunque lavori con ML/AI: spiegano *perché* le GPU accelerano il training e come ottimizzare il codice CUDA.
- La Legge di Amdahl (§7) è uno strumento concettuale fondamentale per ragionare su qualsiasi ottimizzazione parallela.

## Pagine wiki create/aggiornate da questa ingest

**Create (5):**
- [[Architettura RISC-V]] — §1-§2
- [[Aritmetica dei computer]] — §3-§5
- [[Pipeline e processore]] — §4
- [[Gerarchia di memoria e cache]] — §6-§7
- [[GPU e CUDA]] — §8-§10

**Corso:**
- [[Architetture degli Elaboratori]] — 🟡→🟢

## Fonti
- `raw/appunti/architetture.pdf`
