---
tipo: concetto
titolo: Algoritmo di Gauss-Jordan
tag: [algebra-lineare, matematica, calcolo-numerico]
cluster: algebra
fonti: 1
ultima-modifica: 2026-05-05
---

# Algoritmo di Gauss-Jordan

L'**algoritmo di Gauss-Jordan** riduce una matrice $A$ alla sua **forma ridotta a scala** (RREF) tramite operazioni elementari di riga, preservando l'insieme delle soluzioni del sistema $AX = K$.

## Operazioni elementari di riga

1. **$L_i(b)$:** moltiplicare la riga $i$ per uno scalare $b \neq 0$.
2. **$L_{ij}$:** scambiare le righe $i$ e $j$.
3. **$L_{ij}(b)$:** sostituire la riga $i$ con la somma della riga $i$ e della riga $j$ moltiplicata per $b$.

Ogni operazione corrisponde a moltiplicare a sinistra per una matrice elementare $E = L(I_m)$: se $B = E \cdot A$, allora $A \sim B$ (riga-equivalenti).

## Matrice ridotta a scala (RREF)

Una matrice $R$ è **ridotta a scala** se:
1. Le righe nulle stanno in fondo.
2. Il primo elemento non nullo di ogni riga non nulla è 1 (**pivot**).
3. Nella colonna pivot, tutti gli elementi sopra e sotto il pivot sono 0.
4. Gli indici di colonna dei pivot sono in ordine strettamente crescente.

**Teorema di unicità:** Per ogni $A$ esiste un'unica $R$ ridotta a scala tale che $A \sim R$.

## Teorema del calcolo

L'algoritmo di Gauss-Jordan risolve tutti i problemi di algebra lineare:

### (a) Risolvere $AX = K$

Si riduce la matrice aumentata $[A|K] \sim [R|H]$. Tre casi:
1. $\mathrm{rg}([A|K]) > \mathrm{rg}(A)$: sistema **incompatibile** (0 soluzioni).
2. $\mathrm{rg}(A) = n$ (= numero di incognite): **soluzione unica**.
3. $\mathrm{rg}(A) = r < n$: **infinite soluzioni** con $n - r$ parametri liberi ($\infty^{n-r}$ soluzioni).

**Teorema di Rouché-Capelli:** $AX = K$ compatibile $\Leftrightarrow \mathrm{rg}(A) = \mathrm{rg}([A|K])$.

### (b) Calcolare il rango e una base di $\mathrm{Im}(L_A)$

$$\mathrm{rg}(A) = \text{numero di pivot di } R$$

Le colonne di $A$ nelle posizioni $j_1 < j_2 < \cdots < j_r$ dei pivot di $R$ formano una base di $\mathrm{Im}(A) = \mathrm{span}(\text{colonne di } A)$.

### (c) Calcolare nucleo e nullità

$$n(A) = \dim \ker A = n - \mathrm{rg}(A)$$

Si risolve il sistema omogeneo $RX = 0$ per trovare una base di $\ker A$.

### (d) Estrarre base dallo span di vettori

Si forma $A = [v_1 | \cdots | v_k]$ e si applica (b): le colonne di $A$ in posizione pivot sono una base di $\mathrm{span}(v_1, \ldots, v_k)$.

### (e) Calcolare $U + W$

Si affiancano le basi: $A = [\text{base di } U \;|\; \text{base di } W]$, poi si applica (b).

### (f) Calcolare il cambio di base / inversa

$[A | I_n] \sim [I_n | A^{-1}]$: se $A$ è invertibile, la parte destra diventa $A^{-1}$.

## Rango e proprietà

- $\mathrm{rg}(A) = \mathrm{rg}(A^T)$
- $A \sim B \Rightarrow \mathrm{rg}(A) = \mathrm{rg}(B)$
- $\mathrm{rg}(A) \leq \min\{m, n\}$ per $A \in M_{m,n}$
- $A$ ha rango pieno (full column rank) se $\mathrm{rg}(A) = n$

## Connessioni con i sistemi diretti

Gauss-Jordan su $[A|K]$ equivale (in aritmetica esatta) alla fattorizzazione LU di [[Sistemi lineari — metodi diretti]] del corso di [[Metodi Numerici]]. La versione numerica usa pivoting parziale per la stabilità.

## Connessioni

- Prerequisiti: [[Dipendenza lineare]], [[Sottospazio vettoriale]]
- Usato per: [[Base di uno spazio vettoriale]], [[Sottospazio generato]], [[Applicazione lineare]], [[Formula di Grassmann]]
- Versione numerica: [[Sistemi lineari — metodi diretti]]
- Discusso in: [[Algebra Lineare]]

## Fonti

- [[Dispense AlgLin — Galletti]]
