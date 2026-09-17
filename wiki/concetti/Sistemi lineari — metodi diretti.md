---
tipo: concetto
titolo: Sistemi lineari — metodi diretti
tag: [calcolo-numerico, algebra-lineare, metodi-numerici]
cluster: numerico
fonti: 1
ultima-modifica: 2026-05-05
---

# Sistemi lineari — metodi diretti

Un **metodo diretto** risolve $Ax = b$ in un numero finito e determinato di operazioni aritmetiche, producendo (in aritmetica esatta) la soluzione esatta.

## Eliminazione di Gauss

Trasforma $A$ in forma triangolare superiore $U$ tramite operazioni elementari di riga (moltiplicatori $m_{ij} = a_{ij}/a_{ii}$). Poi risolve $Ux = y$ con backward substitution.

**Costo:** $O(n^3/3)$ moltiplicazioni per l'eliminazione + $O(n^2)$ per la sostituzione.

## Fattorizzazione LU

L'eliminazione di Gauss equivale a decomporre $A = LU$ dove:
- $L$ — triangolare inferiore con 1 sulla diagonale (i moltiplicatori $m_{ij}$)
- $U$ — triangolare superiore (la matrice ridotta)

Una volta disponibile $LU$, più rhs $b_1, b_2, \ldots$ si risolvono con costo $O(n^2)$ ciascuno.

**Pivoting parziale:** si sceglie come pivot l'elemento di modulo massimo nella colonna corrente, riordinando le righe con una matrice di permutazione $P$. La fattorizzazione diventa $PA = LU$.

Senza pivoting, $|m_{ij}|$ può essere molto grande e l'algoritmo è numericamente instabile. Con pivoting parziale, $|m_{ij}| \leq 1$ e l'algoritmo è stabile in pratica.

## Costo computazionale

| Operazione                          | Costo         |
|-------------------------------------|---------------|
| Fattorizzazione $PA = LU$           | $O(n^3/3)$    |
| Forward substitution $Ly = Pb$      | $O(n^2)$      |
| Backward substitution $Ux = y$      | $O(n^2)$      |
| Soluzione per nuovo rhs (dopo LU)   | $O(n^2)$      |

## Fattorizzazione di Cholesky (cfr. [[Cholesky, André-Louis]])

Per matrici **simmetriche definite positive** (SPD): $A = LL^T$, con $L$ triangolare inferiore a diagonale positiva.

**Vantaggi rispetto a LU:** costo $O(n^3/6)$ (metà), nessun pivoting necessario (stabilità garantita dalla SPD), meno memoria.

**Verifica SPD:** tutti i minori principali devono essere positivi (equivalente: la fattorizzazione non fallisce mai, cioè $l_{ii} > 0$ per tutto $i$).

## Matrici sparse

Per sistemi sparsi (es. dalla discretizzazione di PDE), eliminazione di Gauss introduce **fill-in**: elementi nulli diventano non nulli in $L$ e $U$. Il riordinamento delle righe/colonne (Cuthill-McKee, nested dissection) minimizza il fill-in.

**Esempio — matrice di Poisson:** sistema tridiagonale a blocchi dalla discretizzazione $-\Delta u = f$ su griglia $n\times n$; dimensione $N=n^2$, ma con struttura banda di ampiezza $n$. Costo LU diretto $O(N^{3/2})$ vs $O(N^2)$ dense.

## Connessioni

- Prerequisito di: [[Metodi iterativi per sistemi lineari]], [[Fattorizzazione QR]]
- Richiede: [[Numeri di macchina e aritmetica floating-point]], [[Autovalori e autovettori]]
- Strettamente legato a: [[Numero di condizionamento]]
- Discusso in: [[Metodi Numerici]]

## Fonti

- [[Dispense Metodi Numerici — Galletti]]
