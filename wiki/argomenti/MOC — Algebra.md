---
tipo: moc
titolo: MOC — Algebra
cluster: algebra
ultima-modifica: 2026-05-06
---

# MOC — Algebra

**Map of Content** del cluster `algebra` (38 concetti). Pagina di **navigazione tematica** per studio.

> **Corsi coinvolti:** [[Algebra Lineare]] (Malvenuto, 24/25), [[Strutture Algebriche]] (Malvenuto, 24/25), [[Metodi Numerici]] (Puppo, 24/25 — capitoli spettrali). Il cluster contiene sia algebra astratta sia algebra lineare.

---

## 🎯 Da dove iniziare

**Per AlgLin:**
1. [[Spazio vettoriale]] — definizione su un campo K
2. [[Sottospazio vettoriale]] → [[Sottospazio generato]] → [[Dipendenza lineare]] → [[Base di uno spazio vettoriale]]
3. [[Mappe lineari]] → [[Applicazione lineare]] → [[Teorema della dimensione (algebra lineare)]]
4. [[Autovalori e autovettori]] → [[Diagonalizzazione]]

**Per StrAlg:**
1. [[Relazione di equivalenza]] e [[Relazione d'ordine]]
2. [[Principio di induzione]]
3. [[Massimo comun divisore]] → [[Algoritmo di Euclide]]
4. [[Aritmetica modulare]] — ℤ_n
5. [[Gruppo (struttura algebrica)]] → [[Sottogruppo]] → [[Teorema di Lagrange]]

---

## 🏗️ Strutture algebriche (StrAlg)

**Fondamenti combinatori:**
- [[Relazione di equivalenza]] — partizioni, classi
- [[Relazione d'ordine]] — totale, parziale
- [[Principio di induzione]]
- [[Teorema Binomiale]] — $(a+b)^n$
- [[Permutazione]] — gruppi simmetrici

**Aritmetica:**
- [[Massimo comun divisore]] — definizione, proprietà
- [[Algoritmo di Euclide]] — calcolo MCD, identità di Bézout
- [[Aritmetica modulare]] — ℤ_n, U(ℤ_n), φ(n), Eulero-Fermat

**Gruppi:**
- [[Gruppo (struttura algebrica)]] — assiomi, esempi
- [[Sottogruppo]] — generato, normale
- [[Teorema di Lagrange]] — $|G| = [G:H]\cdot|H|$
- [[Gruppo simmetrico]] — $S_n$, struttura ciclica
- [[Classi di coniugio]] — invariante struttura ciclica
- [[Omomorfismo di gruppi]] — nucleo, 1° teorema isomorfismo

**Anelli e campi:**
- [[Anello e campo]] — ℤ_p campo per p primo

## 📐 Spazi vettoriali (AlgLin §1-2)

- [[Spazio vettoriale]] — su campo K, esempi (M_{m,n}, R_t[x])
- [[Sottospazio vettoriale]] — somma, intersezione
- [[Sottospazio generato]] — span
- [[Dipendenza lineare]] — definizione, criteri
- [[Base di uno spazio vettoriale]] — esistenza, dimensione
- [[Formula di Grassmann]] — dim(U+W)+dim(U∩W)=dim U + dim W

## 🔄 Applicazioni lineari (AlgLin §3-4)

- [[Mappe lineari]] — nucleo, immagine
- [[Applicazione lineare]] — matrice associata, cambio base
- [[Teorema della dimensione (algebra lineare)]] — rank-nullity
- [[Algoritmo di Gauss-Jordan]] — RREF, Rouché-Capelli, 6 applicazioni

## 🌈 Spettro & diagonalizzazione (AlgLin §5 + MetNum)

**Teoria:**
- [[Polinomio caratteristico]] — $p_T(\lambda) = \det(A - \lambda I)$
- [[Autovalori e autovettori]] — autospazio, m_a, m_g
- [[Diagonalizzazione]] — m_g = m_a, algoritmo 5-step

**Calcolo numerico:**
- [[Cerchi di Gershgorin]] — localizzazione spettro
- [[Metodo delle potenze]] — autovalore dominante
- [[Power iteration]] — versione ML
- [[Quoziente di Rayleigh]] — massimizzazione spettrale
- [[Algoritmo QR per autovalori]] — Hessenberg, shift

## 🎯 Norme & decomposizioni (AlgLin + MetNum)

**Norme matriciali:**
- [[Norma di Frobenius]] — $\sqrt{\sum a_{ij}^2}$

**Matrici notevoli:**
- [[Matrice di Vandermonde]] — interpolazione
- [[Matrice di Hilbert]] — esempio mal condizionato

**Fattorizzazioni:**
- [[Fattorizzazione QR]] — Householder, minimi quadrati
- [[Singular Value Decomposition]] — $A = U \Sigma V^\top$, esiste sempre

## 🔗 Argomenti trasversali

- [[SVD e decomposizione spettrale]] — sintesi 5 corsi (AlgLin/MetNum/ML/MatML/InfML)
- [[Regolarizzazione]] — shift autovalori (Tikhonov)
- [[Reti neurali]] — Hessiana e curvature spettrali

## 📚 Per esame

**AlgLin (Malvenuto, 24/25):** spazi → mappe → diagonalizzazione → [[Algebra Lineare]]
**StrAlg (Malvenuto, 24/25):** insiemi → aritmetica → gruppi → [[Strutture Algebriche]]
**MetNum (Puppo, 24/25):** sezione spettrale → [[Metodi Numerici]] (cap. 7)

## 🔁 Relazione tra i due corsi di Malvenuto

[[Algebra Lineare]] e [[Strutture Algebriche]] sono **complementari**:
- StrAlg fornisce il linguaggio (gruppi, anelli, campi) che AlgLin usa implicitamente.
- AlgLin specializza la teoria sui campi $\mathbb{R}$ e $\mathbb{C}$ con applicazioni geometriche e di calcolo.
- Il [[Gruppo simmetrico]] (StrAlg) è la base del determinante (AlgLin).
- Il concetto di [[Anello e campo]] (StrAlg) giustifica perché lo [[Spazio vettoriale]] è "su un campo K".
