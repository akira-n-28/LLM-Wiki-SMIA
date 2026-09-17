---
tipo: argomento
titolo: SVD e decomposizione spettrale
tag: [trasversale, algebra-lineare, ml, calcolo-numerico]
cluster: trasversale
corsi: [Algebra Lineare, Metodi Numerici, Machine Learning, Matematica per il Machine Learning, Informatica per il Machine Learning]
ultima-modifica: 2026-05-06
---

# SVD e decomposizione spettrale

Argomento trasversale che attraversa **5 corsi**. Lo stesso oggetto matematico — la decomposizione spettrale di una matrice — viene insegnato in cinque modi diversi a seconda dell'angolazione: algebrica, numerica, statistica, geometrica, applicativa.

## Il nucleo unificante

Per una matrice $A \in \mathbb{R}^{m \times n}$ esistono due decomposizioni canoniche, legate tra loro:

**Eigendecomposizione** — solo per $A$ quadrata e diagonalizzabile:
$$A = P D P^{-1}, \qquad D = \mathrm{diag}(\lambda_1, \ldots, \lambda_n)$$

Per $A$ simmetrica reale, $P$ è ortogonale ($A = P D P^\top$) e gli autovalori sono reali.

**SVD** — esiste sempre, anche per matrici rettangolari o singolari:
$$A = U \Sigma V^\top, \qquad \sigma_i^2 = \lambda_i(A^\top A)$$

L'identità $\sigma_i^2 = \lambda_i(A^\top A)$ è il ponte: la SVD è l'eigendecomposizione di $A^\top A$ (per i destri) o $A A^\top$ (per i sinistri), trasferita su $A$ stessa.

> 📐 **Slogan unificante:** ogni matrice agisce come una rotazione, seguita da uno scaling lungo gli assi principali, seguita da un'altra rotazione. La SVD identifica gli assi.

## Il tour dei corsi

### [[Algebra Lineare]] — la teoria
Introduce gli autovalori come radici del [[Polinomio caratteristico]] $p_T(\lambda) = \det(A - \lambda I)$. Sviluppa la [[Diagonalizzazione]] con criterio molteplicità geometrica = molteplicità algebrica e arriva alla **forma di Jordan** per il caso non diagonalizzabile. Non tratta SVD, ma fornisce gli ingredienti (ortogonalità, sottospazi invarianti, [[Teorema della dimensione (algebra lineare)]]).

### [[Metodi Numerici]] — il calcolo
Il punto di vista più ricco computazionalmente. Tre layer:

- **Localizzazione:** [[Cerchi di Gershgorin]] dà bound a priori sullo spettro senza calcolare nulla.
- **Iterazione di un autovalore:** [[Metodo delle potenze]] e potenza inversa estraggono $\lambda_{\max}$ o $\lambda_{\min}$ in $O(\log(1/\epsilon))$ iterazioni con costo $O(n^2)$ ciascuna.
- **Spettro completo:** [[Algoritmo QR per autovalori]] con shift e Hessenberg, costo $O(n^3)$. Per la SVD: bidiagonalizzazione + QR su $B^\top B$ implicito (Golub-Reinsch), evita $K_2(A^\top A) = K_2(A)^2$.

Lega lo spettro al [[Numero di condizionamento]]: $K_2(A) = \sigma_1/\sigma_n$, $K_2(\text{SPD}) = \lambda_{\max}/\lambda_{\min}$. Da qui passa al condizionamento dei sistemi lineari e alla velocità del [[Gradiente coniugato]].

### [[Machine Learning]] — l'interpretazione statistica
La SVD compare come **strumento centrale** in tre contesti:

- **[[Principal Component Analysis]]:** $X = U\Sigma V^\top$ implica $X^\top X / n = V (\Sigma^2/n) V^\top$. Le PC sono i vettori singolari, le varianze sono $\sigma_i^2/n$. Il [[Quoziente di Rayleigh]] giustifica la massimizzazione della varianza.
- **[[Power iteration]]:** algoritmo iterativo per estrarre la prima PC senza diagonalizzare $C = X^\top X$ (costoso per $n \gg d$ o viceversa).
- **Pseudoinversa:** $A^\dagger = V\Sigma^\dagger U^\top$ chiude la formula della [[Regressione lineare]] anche per casi sotto/sovradeterminati.

### [[Matematica per il Machine Learning]] — l'inferenza
La decomposizione spettrale di $X^\top X$ entra nel **modello lineare normale**: la matrice di varianza-covarianza dello stimatore $\hat\beta = (X^\top X)^{-1} X^\top y$ è $\sigma^2 (X^\top X)^{-1}$, e gli autovalori di $X^\top X$ controllano l'incertezza nelle direzioni delle PC. La [[Stima MAP]] con prior gaussiano regolarizza precisamente gli autovalori piccoli (ridge $\Leftrightarrow \sigma_i \to \sigma_i + \lambda$).

### [[Informatica per il Machine Learning]] — la compressione applicata
SVD usata come **strumento operativo**:
- **[[Sistemi di raccomandazione]]:** matrix factorization $R \approx Q P^\top$ è una SVD troncata su matrice sparsa (utenti × oggetti), risolta con SGD invece che algebricamente.
- **Word2Vec:** la matrice di co-occorrenza viene fattorizzata implicitamente, con i vettori singolari come embedding.
- Compressione di pesi (LoRA, low-rank fine-tuning) usa Eckart-Young in modo additivo.

## Equivalenze e varianti

| Forma | Quando | Costo | Cuor del calcolo |
|---|---|---|---|
| Eigendecomposition simmetrica | $A=A^\top$ piccola | $O(n^3)$ | QR con shift |
| [[Power iteration]] | serve solo $\lambda_1$ | $O(n^2)$/iter | moltiplicazioni $A v$ |
| SVD piena | studio completo | $O(\min(mn^2, m^2 n))$ | Golub-Reinsch |
| SVD ridotta (economica) | $m \gg n$ | $O(mn^2)$ | salta $U$ inutile |
| SVD troncata (top-$k$) | $k \ll \min(m,n)$ | $O(mnk)$ | Lanczos / Arnoldi |
| PCA via $X^\top X$ | $d \ll n$ | $O(nd^2 + d^3)$ | mai con dati mal cond. |
| PCA via SVD diretta | dati mal cond. | $O(\min(mn^2, m^2 n))$ | Golub-Reinsch su $X$ |
| Pseudoinversa | $A$ rettangolare | $O(\min(mn^2, m^2 n))$ | $V\Sigma^\dagger U^\top$ |

## Albero di decisione operativo

- **Devo solo l'autovalore massimo o minimo?** → [[Metodo delle potenze]] / potenza inversa.
- **Devo lo spettro intero, $A$ piccola, simmetrica?** → [[Algoritmo QR per autovalori]].
- **Devo le componenti principali di dati grandi?** → SVD diretta su $X$ (Golub-Reinsch o Lanczos), mai $X^\top X$.
- **Devo $\min \|Ax-b\|$ con $A$ mal condizionata?** → SVD + pseudoinversa con regolarizzazione (ignora $\sigma_i < $ tolleranza).
- **Devo comprimere una matrice?** → SVD troncata (Eckart-Young).

## Connessioni nascoste

- **Numero di condizionamento ↔ varianza dello stimatore.** In [[Metodi Numerici]] $K_2$ misura amplificazione del rumore in $Ax=b$; nel modello lineare normale, $1/\sigma_n^2$ misura la varianza dell'OLS lungo la direzione $v_n$. Stesso fenomeno, due linguaggi.
- **Regolarizzazione di Tikhonov ↔ shift sugli autovalori.** Aggiungere $\lambda I$ a $X^\top X$ trasforma $\sigma_i^2 \mapsto \sigma_i^2 + \lambda$, "alzando" gli autovalori piccoli. È lo stesso meccanismo del [[Gradiente coniugato]] precondizionato. Vedi [[Regolarizzazione di Tikhonov]] e [[Stima MAP]].
- **PCA ↔ MDS classico.** [[Multidimensional Scaling]] su distanze euclidee dà gli stessi assi della PCA, calcolati da $-\frac{1}{2} J D^{(2)} J$ (centratura di Young-Householder) invece che da $X^\top X$. Stessa SVD vista da due punti di vista (features vs distanze).

## Pagine collegate

- Concetti centrali: [[Singular Value Decomposition]], [[Autovalori e autovettori]], [[Principal Component Analysis]]
- Calcolo: [[Power iteration]], [[Algoritmo QR per autovalori]], [[Cerchi di Gershgorin]], [[Quoziente di Rayleigh]]
- Algebra: [[Diagonalizzazione]], [[Polinomio caratteristico]], [[Norma di Frobenius]]
- Applicazioni: [[Multidimensional Scaling]], [[Sistemi di raccomandazione]], [[Regolarizzazione di Tikhonov]]
- Condizionamento: [[Numero di condizionamento]]

## Fonti aggregate

- [[Dispense AlgLin — Galletti]] (cap. 4 — diagonalizzazione)
- [[Dispense Metodi Numerici — Galletti]] (cap. 7 — autovalori, SVD)
- [[Dispense Machine Learning — Galletti]] (§6 — PCA)
- [[Dispense MatML — Galletti]] (§2 — modello lineare normale)
- [[Dispense InfML — Galletti]] (§5 — raccomandazione, embeddings)
