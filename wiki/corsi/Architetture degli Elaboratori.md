---
tipo: corso
titolo: Architetture degli Elaboratori
docente: Salvatore Pontarelli
anno-accademico: 2025/2026
codice-breve: architetture
ultima-modifica: 2026-05-06
tag: [architettura, hardware, cs, smia]
---

# Architetture degli Elaboratori

Corso di **Architetture degli Elaboratori** tenuto dal prof. **Salvatore Pontarelli** nell'A.A. 2025/2026, SMIA, Sapienza. Dispense redatte da [[Galletti, Marco]] (77 pp.).

## Programma

### §1 Introduzione (pp. 2-5)
- [[Architettura RISC-V]] — ISA: stati, operazioni, control flow, procedure
- Metriche di performance: CPU time, CPI, throughput; power wall → multicore

### §2 Rappresentazione delle istruzioni (pp. 6-12)
- [[Architettura RISC-V]] — formati R/I/S/B, 32 bit a larghezza fissa
- Registri, load/store, control flow, strutture dati, procedure call (ABI, stack)

### §3 Aritmetica dei computer (pp. 13-23)
- [[Aritmetica dei computer]] — complemento a 2, overflow, moltiplicazione/divisione binaria
- IEEE 754: single/double precision, NaN, ±∞, operazioni FP, FMA

### §4 Progettazione di un processore (pp. 24-36)
- [[Pipeline e processore]] — datapath, pipeline 5 stadi (IF/ID/EX/MEM/WB)
- Hazard strutturali, dati (forwarding), controllo (branch prediction 1/2 bit)
- ILP: multiple issue (statico/dinamico), out-of-order execution, ROB, register renaming

### §5 Istruzioni vettoriali SIMD (pp. 37-38)
- [[Aritmetica dei computer]] — SSE/AVX/AVX-512; vectorization; intrinsics

### §6 Le memorie (pp. 39-46)
- [[Gerarchia di memoria e cache]] — principio di località, DRAM, direct-mapped cache
- AMAT, N-way set associative, LRU, write-through/back, 3C (cold/capacity/conflict)

### §7 Processori multi-core e cache coherence (pp. 47-52)
- [[Gerarchia di memoria e cache]] — snooping, false sharing, Legge di Amdahl
- Tassonomia di Flynn (SISD/SIMD/MIMD), SMT, SMP (UMA/NUMA), reti di interconnessione

### §8 Architetture specifiche per dominio (pp. 53-55)
- [[GPU e CUDA]] — DSA vs ASIC, systolic arrays, double buffering, memory wall, quantizzazione

### §9 Google TPU: caso di studio (pp. 56-59)
- [[GPU e CUDA]] — MXU (256×256 MAC INT8), unified buffer, ISA CISC, roofline model

### §10 GPU e CUDA (pp. 60-77)
- [[GPU e CUDA]] — CPU vs GPU, CUDA (grid/block/thread/warp), shared memory
- Tiling, bank conflicts, memory coalescing, CUDA Streams

## Concetti centrali

| Concetto | Sezione | Importanza |
|---|---|---|
| [[Architettura RISC-V]] | §1-§2 | ISA, metriche di performance, ABI |
| [[Aritmetica dei computer]] | §3-§5 | IEEE 754, overflow, SIMD |
| [[Pipeline e processore]] | §4 | hazard, ILP, out-of-order |
| [[Gerarchia di memoria e cache]] | §6-§7 | cache, coerenza, Amdahl |
| [[GPU e CUDA]] | §8-§10 | DSA, TPU, CUDA, tiling, coalescing |

## Fonti del corso

- [[Dispense Architetture — Galletti]] — dispense principali, 77 pp. (ingest profondo 2026-05-06)

## Stato della wiki per questo corso

🟢 **Completo** — ingest profondo effettuato (2026-05-06). 5 concetti creati.

## Connessioni trasversali con altri corsi

| Concetto Architetture | Corso collegato |
|---|---|
| IEEE 754, aritmetica FP | [[Metodi Numerici]] (numeri di macchina, cancellazione catastrofica) |
| Cache e gerarchia memoria | [[Algoritmi e Complessità]] (località, cache-oblivious algorithms) |
| GPU e parallelismo SIMD | [[Machine Learning]], [[Informatica per il Machine Learning]] (training su GPU) |
| Roofline model, intensità aritmetica | [[Ottimizzazione]] (compute-bound vs memory-bound) |
| Systolic arrays, TPU | [[Informatica per il Machine Learning]] (acceleratori hardware per DNN) |
