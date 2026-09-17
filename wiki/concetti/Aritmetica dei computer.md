---
tipo: concetto
titolo: Aritmetica dei computer
tag: [architettura, hardware, cs, aritmetica, floating-point]
cluster: sistemi
fonti: 1
ultima-modifica: 2026-05-06
---

# Aritmetica dei computer

## Rappresentazioni intere

**Complemento a 2 (Two's Complement Signed):**
$$x = -2^{n-1} \cdot b_{n-1} + \sum_{i=0}^{n-2} b_i \cdot 2^i$$

**Negazione:** $-x = \bar{x} + 1$ (complemento bit a bit + 1).

**Unsigned:** $x = \sum_{i=0}^{n-1} b_i \cdot 2^i$.

**Overflow:** somma di due $n$-bit può richiedere $n+1$ bit. Il processore imposta un bit di overflow. In complemento a 2 su 4 bit, $7 + 6 = 13$ non è rappresentabile → il risultato è $-3$ (wraparound).

## Moltiplicazione

Prodotto di $n$ bit × $n$ bit richiede fino a $2n$ bit. RISC-V ha 4 istruzioni: `mul` (32 bit bassi), `mulh` (32 bit alti, signed×signed), `mulhu` (unsigned), `mulhsu` (signed×unsigned).

**Rilevamento overflow 64 bit:** per unsigned, overflow se `mulhu ≠ 0`; per signed, overflow se `mulh ≠ arithmetic_shift_right(mul, 63)`.

**Algoritmo hardware (shift-and-add):** 32 cicli — per ogni bit del moltiplicatore, se è 1 somma il moltiplicando al registro prodotto; poi shift left del moltiplicando e shift right del moltiplicatore.

## Divisione

$D = V \cdot Q + R$ con $0 \leq R < |V|$. RISC-V: `div/rem` (signed), `divu/remu` (unsigned). La divisione per zero non genera eccezione in RISC-V (comportamento definito).

**Algoritmo restoring:** ad ogni iterazione si tenta $R \leftarrow R - V$; se $R < 0$ si "restaura" ($R \leftarrow R + V$) e si pone $Q_i = 0$, altrimenti $Q_i = 1$.

## Standard IEEE 754 (Floating Point)

| Precisione | Bit totali | Segno | Esponente | Mantissa |
|---|---|---|---|---|
| Single | 32 | 1 | 8 (bias 127) | 23 |
| Double | 64 | 1 | 11 (bias 1023) | 52 |

$$x = (-1)^S \times (1 + \text{Fraction}) \times 2^{\text{Exponent} - \text{Bias}}$$

Valori speciali: esponente `11...1` con mantissa=0 → $\pm\infty$; mantissa≠0 → NaN.
Esponente `00...0` → denormalizzato (perdita di precisione ma permette numeri molto piccoli).

### Addizione FP

1. Allinea gli esponenti (sposta il numero con esponente minore).
2. Somma le significande.
3. Normalizza il risultato.
4. Arrotonda e rinormalizza se necessario.

Modale di arrotondamento (IEEE 754): round-to-nearest-even (default), round toward zero, round up, round down.

### Moltiplicazione FP

1. Somma gli esponenti (poi sottrae il bias).
2. Moltiplica le significande.
3. Normalizza e controlla over/underflow.
4. Arrotonda e determina il segno dal prodotto dei segni degli operandi.

### Fused Multiply-Add (FMA)

$a \leftarrow a + (b \times c)$ in un unico arrotondamento finale — più preciso di multiply + add separati. Istruzione `fmadd` disponibile in RISC-V e in estensioni SIMD.

### Istruzioni FP in RISC-V

Registri dedicati `f0–f31`. Load/store: `flw/fld`, `fsw/fsd`. Aritmetica: `fadd.s/d`, `fsub.s/d`, `fmul.s/d`, `fdiv.s/d`, `fsqrt.s/d`. Confronto: `feq.s/d`, `flt.s/d`, `fgt.s/d`.

## SIMD e istruzioni vettoriali (§5)

**SIMD (Single Instruction Multiple Data):** stessa operazione su più dati in parallelo.

| Estensione | Registri | Capacità |
|---|---|---|
| SSE (128-bit) | `xmm0-15` | 2 double / 4 float |
| AVX (256-bit) | `ymm0-15` | 4 double / 8 float |
| AVX-512 (512-bit) | `zmm0-31` | 8 double / 16 float |

**AVX-512** introduce anche 8 registri di maschera `k0-k7` per operazioni condizionali selettive su sottoinsiemi di elementi. Intrinsics C: `__m512d`, `_mm512_fmadd_pd`, `_mm512_load_pd`, ecc.

**Vectorization:** tecnica di riscrittura/compilazione automatica che sfrutta le istruzioni SIMD. Utile per DGEMM: loop unrolling + AVX-512 → 32 double elaborati per iterazione.

## Attenzione: non associatività

Le operazioni FP non sono associative: $(x + y) + z \neq x + (y + z)$ in generale. Calcoli paralleli che suddividono somme richiedono validazione.

## Connessioni

- ISA di riferimento: [[Architettura RISC-V]]
- Pipeline e hardware: [[Pipeline e processore]]
- Calcolo numerico: [[Numeri di macchina e aritmetica floating-point]] (Metodi Numerici — IEEE 754, eps_M)
- GPU/CUDA: [[GPU e CUDA]] (istruzioni HMMA, tensor cores)
- Corso: [[Architetture degli Elaboratori]]

## Fonti

- [[Dispense Architetture — Galletti]] (§3-§5, pp. 13-38)
