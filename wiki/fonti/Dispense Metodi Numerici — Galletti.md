---
tipo: fonte
titolo: Dispense Metodi Numerici — Galletti
autori: [Galletti, Marco]
docente: Puppo, Gabriella
corso: Metodi Numerici
anno-accademico: 2024/2025
data-ingest: 2026-05-05
file-raw: raw/appunti/metodi.pdf
pagine: 108
ultima-modifica: 2026-05-05
---

# Dispense Metodi Numerici — Galletti

**Riferimento file raw:** `raw/appunti/metodi.pdf`
**Docente:** prof.ssa [[Puppo, Gabriella]], A.A. 2024/2025, SMIA, Sapienza.
**Estensione:** 108 pagine — il corso più matematicamente denso dell'ingest.

## Riassunto in 5 punti

1. **Arimetica floating-point:** i numeri di macchina formano un insieme discreto; l'arrotondamento introduce errori relativi ≤ eps_M/2, e la cancellazione catastrofica amplifica l'errore relativo quando si sottraggono quantità quasi uguali.
2. **Sistemi lineari:** la fattorizzazione LU con pivoting parziale (PA=LU) risolve Ax=b in O(n³/3) flop; la stabilità della soluzione dipende dal numero di condizionamento K(A)=‖A‖·‖A⁻¹‖.
3. **Metodi iterativi:** Jacobi, Gauss-Seidel e Richardson producono successioni x_k→x* a costo O(n²) per iterazione; il gradiente coniugato converge in ≤n+1 iterazioni con tasso ρ=√(K-1)/√(K+1).
4. **Autovalori e interpolazione:** i cerchi di Gershgorin localizzano lo spettro; il metodo delle potenze e l'algoritmo QR calcolano autovalori; l'interpolazione di Lagrange con nodi di Gauss-Lobatto evita il fenomeno di Runge.
5. **ODE numeriche:** i metodi di Eulero (esplicito e implicito) e Runge-Kutta integrano y'=f(t,y) con ordini 1 e 4; la stabilità assoluta (regione nel piano h·λ) governa la scelta del passo.

## Argomenti trattati (struttura del corso)

### Cap. 1-2 — Aritmetica e numeri di macchina
- [[Numeri di macchina e aritmetica floating-point]] — IEEE 754, eps_M, cancellazione catastrofica

### Cap. 3 — Sistemi lineari diretti
- [[Sistemi lineari — metodi diretti]] — LU, Cholesky, pivoting, costo O(n³/3)
- [[Numero di condizionamento]] — K(A), bound errore relativo

### Cap. 4 — Metodi iterativi
- [[Metodi iterativi per sistemi lineari]] — Jacobi, Gauss-Seidel, Richardson
- [[Gradiente coniugato]] — metodo del gradiente, GC, convergenza in n+1 iterazioni

### Cap. 5-6 — Equazioni non lineari e interpolazione
- [[Metodi per equazioni non lineari]] — bisezione, Newton, secanti, punto fisso
- [[Teorema delle Contrazioni]] — Banach-Caccioppoli, esistenza/unicità
- [[Interpolazione di Lagrange]] — basi di Lagrange, errore, Runge, nodi Gauss-Lobatto

### Cap. 7 — Autovalori e SVD
- [[Cerchi di Gershgorin]] — localizzazione spettro
- [[Metodo delle potenze]] — autovalore dominante, potenza inversa
- [[Algoritmo QR per autovalori]] — iterazione QR, fattorizzazione di Schur
- [[Singular Value Decomposition]] — σ₁=‖A‖₂, rank, SVD ridotta
- [[Fattorizzazione QR]] — Householder, minimi quadrati sovradeterminati

### Cap. 8 — Integrazione numerica
- [[Integrazione numerica]] — rettangoli, trapezi, Cavalieri-Simpson, Gauss
- [[Interpolazione di Lagrange]] *(nodi, errore composito)*

### Cap. 9-10 — ODE numeriche
- [[Metodi numerici per ODE]] — Eulero esplicito/implicito, Runge-Kutta, stabilità assoluta

## Citazioni chiave

> "La precisione di macchina eps_M è il numero più piccolo tale che fl(1+eps_M) > 1."

> "Il metodo del gradiente coniugato è esatto in aritmetica esatta dopo al più n+1 iterazioni, e converge molto prima per spettri ben separati."

## Note di lettura

Le dispense sono matematicamente rigorose, con dimostrazioni e teoremi. Il capitolo più importante per le applicazioni è il 4 (iterativi + GC). Il capitolo sugli autovalori (7) è corposo ma tratta argomenti centrali anche in ML (SVD, PCA).

## Pagine wiki create da questa ingest

**Create (13):**
- [[Numeri di macchina e aritmetica floating-point]] (nuova)
- [[Sistemi lineari — metodi diretti]] (nuova)
- [[Numero di condizionamento]] (nuova)
- [[Metodi iterativi per sistemi lineari]] (nuova)
- [[Interpolazione di Lagrange]] (nuova)
- [[Metodi per equazioni non lineari]] (nuova)
- [[Teorema delle Contrazioni]] (nuova)
- [[Fattorizzazione QR]] (nuova)
- [[Cerchi di Gershgorin]] (nuova)
- [[Metodo delle potenze]] (nuova)
- [[Algoritmo QR per autovalori]] (nuova)
- [[Integrazione numerica]] (nuova)
- [[Metodi numerici per ODE]] (nuova)

**Aggiornate (3):**
- [[Autovalori e autovettori]] (aggiunta: Gershgorin, power method, Schur, trattazione numerica)
- [[Singular Value Decomposition]] (aggiunta: σ₁=‖A‖₂, rank, SVD ridotta, calcolo via AᵀA)
- [[Gradiente coniugato]] (aggiunta: formule numeriche αk/βk, convergenza in n+1, confronto Richardson)
