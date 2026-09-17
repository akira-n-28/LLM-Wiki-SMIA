---
tipo: corso
titolo: Metodi Numerici
docente: Gabriella Puppo
anno-accademico: 2024/2025
codice-breve: metodi
ultima-modifica: 2026-05-05
tag: [matematica, calcolo-numerico, smia]
---

# Metodi Numerici

Corso di **Metodi Numerici** tenuto dalla prof.ssa **[[Puppo, Gabriella]]** nell'A.A. 2024/2025, SMIA, Sapienza. 108 pagine — materiale matematicamente rigoroso con dimostrazioni e teoremi.

## Programma

1. **Ripasso di algebra lineare**
   - Norme di vettori e matrici, autovalori/autovettori

2. **Numeri di macchina e aritmetica floating-point**
   - IEEE 754, precisione di macchina $\varepsilon_M$, overflow/underflow
   - Arrotondamento: $\mathrm{fl}(x) = x(1+\delta)$, $|\delta| \leq \varepsilon_M/2$
   - Cancellazione catastrofica

3. **Sistemi lineari — metodi diretti**
   - Eliminazione di Gauss, fattorizzazione $PA = LU$ con pivoting
   - Costo $O(n^3/3)$; Cholesky $O(n^3/6)$ per SPD
   - Matrici sparse, matrice di Poisson, fill-in

4. **Numero di condizionamento e stabilità**
   - $K_p(A) = \|A\|_p \|A^{-1}\|_p$; bound errore relativo
   - $K_2(\text{SPD}) = \lambda_{\max}/\lambda_{\min}$; $K_2(\text{ortog.}) = 1$

5. **Metodi iterativi per sistemi lineari**
   - Jacobi (dominanza diagonale), Gauss-Seidel
   - Richardson: $\alpha_{\mathrm{opt}} = 2/(\lambda_1+\lambda_n)$, $\rho = (K-1)/(K+1)$
   - Precondizionatori

6. **Metodo del gradiente e gradiente coniugato**
   - Gradiente: $\alpha_k = r_k^Tr_k / (d_k^TAd_k)$
   - GC: converge in $\leq n+1$ iterazioni; $\rho_{GC} = (\sqrt{K}-1)/(\sqrt{K}+1)$
   - GC precondizionato (PCG)

7. **Equazioni non lineari**
   - Bisezione: $|e_k| \leq (b-a)/2^{k+1}$, converge sempre
   - Newton: convergenza quadratica $|e_{k+1}| \leq M|e_k|^2$
   - Secanti (ordine $\phi \approx 1.618$), punto fisso
   - [[Teorema delle Contrazioni]] (Banach-Caccioppoli)

8. **Interpolazione**
   - Basi di Lagrange, formula dell'errore $e_n(x) = f^{(n+1)}(\xi)\omega_{n+1}(x)/(n+1)!$
   - Fenomeno di Runge con nodi equidistanti
   - Costante di Lebesgue $\Lambda_n$, nodi di Gauss-Lobatto
   - Interpolazione composita (piecewise)

9. **Integrazione numerica**
   - Rettangoli, trapezi ($O(h^2)$), Cavalieri-Simpson ($O(h^4)$)
   - Quadratura di Gauss: grado di esattezza $2n+1$ con $n+1$ nodi

10. **Fattorizzazione QR e minimi quadrati**
    - $A = QR$ via Householder; QR ridotta
    - Minimi quadrati sovradeterminati: $\tilde{R}x = \tilde{Q}^Tb$
    - Stabilità vs equazione normale ($K(A^TA) = K(A)^2$)

11. **Autovalori — localizzazione e calcolo**
    - Cerchi di Gershgorin: $\mathrm{spec}(A) \subseteq \bigcup_i C_i$
    - Metodo delle potenze, potenza inversa, shift
    - Algoritmo QR: iterazione $A_{k+1}=R_kQ_k$ → fattorizzazione di Schur
    - Forma di Hessenberg come pre-processing

12. **Singular Value Decomposition**
    - $A = U\Sigma V^T$; $\sigma_1 = \|A\|_2$; $\mathrm{rank}=\#\{\sigma_i>0\}$
    - SVD ridotta; algoritmo di Golub-Reinsch

13. **Metodi numerici per ODE**
    - Eulero esplicito: $y_{k+1}=y_k+hf(t_k,y_k)$, ordine 1, regione stabilità $|1+h\lambda|<1$
    - Eulero implicito: A-stabile, adatto a sistemi stiff
    - Runge-Kutta 4: $y_{k+1}=y_k+(h/6)(k_1+2k_2+2k_3+k_4)$, ordine 4

## Concetti centrali

### Aritmetica e stabilità
- [[Numeri di macchina e aritmetica floating-point]]
- [[Numero di condizionamento]]

### Sistemi lineari
- [[Sistemi lineari — metodi diretti]]
- [[Metodi iterativi per sistemi lineari]]
- [[Gradiente coniugato]] *(sezione sistemi lineari SPD)*

### Equazioni non lineari
- [[Metodi per equazioni non lineari]]
- [[Teorema delle Contrazioni]]

### Interpolazione e integrazione
- [[Interpolazione di Lagrange]]
- [[Integrazione numerica]]

### Algebra lineare numerica
- [[Fattorizzazione QR]]
- [[Cerchi di Gershgorin]]
- [[Metodo delle potenze]]
- [[Algoritmo QR per autovalori]]
- [[Autovalori e autovettori]] *(arricchita con prospettiva numerica)*
- [[Singular Value Decomposition]] *(arricchita con norme, rango, calcolo)*

### ODE
- [[Metodi numerici per ODE]]

## Fonti del corso

- [[Dispense Metodi Numerici — Galletti]] — dispense della prof.ssa Puppo, 108 pp.

## Stato

🟢 Ingest profondo completato (2026-05-05)
