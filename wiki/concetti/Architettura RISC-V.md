---
tipo: concetto
titolo: Architettura RISC-V
tag: [architettura, hardware, cs, isa, risc-v]
cluster: sistemi
fonti: 1
ultima-modifica: 2026-05-06
---

# Architettura RISC-V

## Instruction Set Architecture (ISA)

La **ISA** (Instruction Set Architecture) è l'interfaccia tra hardware e software: definisce lo stato del processore (registri, memoria), le operazioni computazionali, le operazioni di memoria e il control flow.

**Stack software:**
```
Applicazioni → Linguaggio di programmazione → Assembly/Machine → Hardware
```

RISC-V è l'ISA di riferimento delle dispense: architettura RISC a 64 bit con 32 registri generali (x0–x31) da 64 bit ciascuno. `x0` vale sempre 0.

## Metriche di performance

**Response time** (o elapsed time): durata totale di un'operazione. **Throughput**: lavoro per unità di tempo.

$$\text{CPU time} = \frac{\text{Instruction Count} \times \text{CPI}}{\text{Clock rate}}$$

Il **CPI** (Cycles per Instruction) è la media pesata per classe di istruzione:
$$\text{CPI} = \sum_{i=1}^n \text{CPI}_i \times \frac{\text{IC}_i}{\text{IC}}$$

Le prestazioni dipendono da: algoritmo, linguaggio, compilatore, ISA — tutti influenzano IC e CPI.

**Power wall:** $\text{Power} = C \cdot V^2 \cdot f$ — non si può ridurre ulteriormente $V$ né aumentare $f$ senza problemi termici. Motivo del passaggio al multi-core.

## Formati di istruzione RISC-V

Ogni istruzione è a **32 bit** a formato fisso. I campi `rs1`, `rs2`, `rd` sono **sempre nelle stesse posizioni** — semplifica la decodifica e il bypass nella pipeline.

| Formato | Uso | Struttura |
|---|---|---|
| **R** | Aritm. registro | `funct7 rs2 rs1 funct3 rd opcode` |
| **I** | Aritm. immediata, load | `imm[11:0] rs1 funct3 rd opcode` |
| **S** | Store | `imm[11:5] rs2 rs1 funct3 imm[4:0] opcode` |
| **B** | Branch | `imm[12,10:5] rs2 rs1 funct3 imm[4:1,11] opcode` |

Immediati nei formati S e B sono spezzati per tenere fissi i campi registro. I branch usano LSB implicito a 0 (salti sempre allineati a 2 byte → compatibilità con istruzioni compresse a 16 bit).

**Opcodes comuni:**
- R-type ALU: `0110011`; I-type ALU: `0010011`; Load: `0000011`; Store: `0100011`
- Branch: `1100011`; `jal`: `1101111`; `jalr`: `1100111`

## Load/Store e indirizzi

Accesso memoria tramite `ld/sd` (8 byte), `lw/sw` (4), `lb/sb` (1). Indirizzo = `rs1 + offset`.

```
ld  x5, 16(x10)     # x5 ← Mem[16 + x10]
sd  x5, 24(x10)     # Mem[24 + x10] ← x5
lb  x6, 4(x10)      # 1 byte con sign extension
lbu x7, 4(x10)      # 1 byte con zero extension
```

## Control flow

- `j target` — salto incondizionato
- `beq x1, x2, target` — salta se `x1 == x2`; altrimenti `PC+4`
- `bne`, `blt`, `bge` — varianti analoghe

## Procedure call e ABI

**`jal x1, target`** — salta e scrive `PC+4` in `x1` (return address).
**`jalr x0, 0(ra)`** — ritorna al chiamante (`ret`).

Registri ABI RISC-V:
- `ra` (x1) = return address; `sp` (x2) = stack pointer; `a0-a7` (x10-x17) = argomenti/return
- `t0-t6` = caller-saved; `s0-s11` = callee-saved (la funzione chiamata li preserva)
- Lo stack cresce verso indirizzi **decrescenti**; ogni procedura alloca il proprio stack frame con `addi sp, sp, -N`.

**Procedura chiamata:**
1. Caller: prepara argomenti in `a0-a7`, esegue `jal ra, f`.
2. Callee: alloca stack frame (`addi sp, sp, -16`), salva `ra` e registri callee-saved.
3. Callee: esegue il corpo, scrive il valore di ritorno in `a0`.
4. Callee: ripristina registri, libera frame (`addi sp, sp, 16`), esegue `ret`.

## Connessioni

- Aritmetica e rappresentazioni: [[Aritmetica dei computer]]
- Esecuzione e pipeline: [[Pipeline e processore]]
- Corso: [[Architetture degli Elaboratori]]

## Fonti

- [[Dispense Architetture — Galletti]] (§1-§2, pp. 2-12)
