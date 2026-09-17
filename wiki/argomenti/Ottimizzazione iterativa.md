---
tipo: argomento
titolo: Ottimizzazione iterativa
tag: [trasversale, ottimizzazione, ml, calcolo-numerico]
cluster: trasversale
corsi: [Ottimizzazione, Machine Learning, Metodi Numerici, Matematica per il Machine Learning, Informatica per il Machine Learning]
ultima-modifica: 2026-05-06
---

# Ottimizzazione iterativa

Argomento trasversale che attraversa **5 corsi**. Lo stesso schema — partire da $x_0$, costruire $x_{k+1} = x_k + \alpha_k d_k$ con direzione $d_k$ e passo $\alpha_k$, fermarsi vicino a un punto stazionario — viene insegnato cinque volte con motivazioni e analisi diverse: come algoritmo per ML (stocastico), come metodo per problemi vincolati (KKT), come solver per equazioni nonlineari, come sistema dinamico, come zoom su problemi convessi.

## Lo schema universale

Tutti i metodi iterativi seguono lo stesso template:

$$
x_{k+1} = x_k + \alpha_k d_k
$$

Le scelte fanno la differenza:

| Componente | Opzioni | Costo per iterazione |
|---|---|---|
| **Direzione $d_k$** | $-\nabla f$, $-H^{-1}\nabla f$, ortogonalizzata, stocastica | da $O(d)$ a $O(d^3)$ |
| **Passo $\alpha_k$** | costante, [[Metodo di Armijo\|Armijo]] (line search), Wolfe, scheduling decrescente | da $O(1)$ a $O(d)$ |
| **Vincoli** | nessuno, proiezione, Lagrangiano, KKT | dipende dalla geometria |
| **Stocasticità** | gradiente esatto, mini-batch, single-sample | scalabilità in $n$ |

Tre domande comuni:
1. **Converge?** condizioni sufficienti
2. **Quanto velocemente?** lineare, superlineare, quadratica
3. **A cosa converge?** minimo locale, globale, punto stazionario, sella

## Il tour dei corsi

### [[Ottimizzazione]] — la teoria deterministica
Visione più matura. Quattro pilastri:

- **[[Convessità]]**: minimo locale = globale; gradiente nullo = ottimo. Tutto il resto della teoria si appoggia qui.
- **[[Condizioni di ottimalità]]**: ordine I (gradiente) e II (Hessiana semidefinita). Estensione vincolata via [[Condizioni KKT]] (1939 Karush, 1951 Kuhn-Tucker).
- **Algoritmi unconstrained**: [[Discesa del gradiente]] (lineare), [[Metodo di Newton (ottimizzazione)|Newton]] (quadratico locale), [[Metodi Quasi-Newton]] (BFGS — superlineare senza Hessiana esatta), [[Gradiente coniugato]] (lineare ottimale per quadratiche).
- **Algoritmi constrained**: [[Proiezione su insiemi convessi]], [[Frank-Wolfe e gradiente proiettato]] (per simplex e politopi), penalty/barrier.

Il [[Metodo di Armijo]] è la guida universale per scegliere $\alpha_k$: sufficient decrease + curvatura → garanzia di convergenza globale.

### [[Metodi Numerici]] — la prospettiva linear-algebrica
La stessa famiglia di metodi vista come *risolvere $Ax = b$ con $A$ SPD* equivale a *minimizzare $\frac{1}{2}x^\top A x - b^\top x$*. Da qui:

- **[[Metodi iterativi per sistemi lineari]]**: Jacobi, Gauss-Seidel, Richardson — convergenza con $\rho = (K-1)/(K+1)$.
- **[[Gradiente coniugato]] (lineare)**: $\rho = (\sqrt{K}-1)/(\sqrt{K}+1)$ — drasticamente più veloce. È esatto in $\leq n$ iterazioni in aritmetica esatta.
- **PCG** (preconditioned CG): scegliere $M^{-1} \approx A^{-1}$ trasforma $K(A) \to K(M^{-1}A)$ piccolo.
- **[[Metodi per equazioni non lineari]]**: Newton converge quadraticamente, secanti superlinearmente. Lega al [[Teorema delle Contrazioni]] (Banach-Caccioppoli).

Il taglio numerico aggiunge consapevolezza di:
- **[[Numero di condizionamento]]**: governa la velocità di tutti gli iterativi.
- **Aritmetica finita**: cancellazione catastrofica vicino al minimo, propagazione errori.

### [[Machine Learning]] — la versione stocastica
Il salto: $f(\Theta) = \frac{1}{n}\sum_i \ell(y_i, g_\Theta(x_i))$ con $n$ enorme. Calcolare $\nabla f$ esatto è proibitivo.

- **[[Stochastic Gradient Descent]]** (Robbins-Monro 1951): stima $\nabla f$ con un singolo sample (o mini-batch). Convergenza in *media* sotto $\sum \alpha_k = \infty$, $\sum \alpha_k^2 < \infty$.
- **Tradeoff varianza-step**: più batch = meno varianza, più costo per iterazione. La curva di convergenza in funzione del *tempo di calcolo* favorisce mini-batch piccoli.
- **Momentum, Adam**: accumulano statistiche del primo (momentum) e secondo (Adam) momento del gradiente per scaling per coordinata.
- **Backpropagation**: rende fattibile il calcolo di $\nabla_\Theta f$ in tempo lineare nella rete (vedi argomento [[Reti neurali]]).

### [[Matematica per il Machine Learning]] — l'approssimazione stocastica
Visione probabilistica:

- **[[Approssimazione stocastica]]** (Robbins-Monro): risolvere $E[H(\theta, \xi)] = 0$ con $\theta_{n+1} = \theta_n - \gamma_n H(\theta_n, \xi_n)$. Converge sotto regolarità + step decrescente. È la generalizzazione astratta di SGD.
- **[[Metodo del corrispondente stocastico]]**: ottimizzazione di $E[F(x, \xi)]$ via traiettorie campionate.
- **[[Simulated Annealing]]**: ottimizzazione globale via Metropolis-Hastings con cooling. Usa MCMC per *esplorare* invece che sfruttare gradiente.
- **[[Metodo Cross-Entropy]]**: rare-event simulation come ottimizzazione iterativa di una distribuzione di sampling.

Il punto unificante: tutti questi sono *catene di Markov* sullo spazio dei parametri (cfr. argomento [[Catene di Markov e MCMC]]).

### [[Informatica per il Machine Learning]] — applicazioni e varianti
Pratica di SGD su reti profonde:

- **Mini-batch**: tipicamente 32-512 campioni; bilancia rumore e parallelismo GPU.
- **Learning rate scheduling**: warmup + decay (cosine, step, exponential).
- **AdamW**: Adam con decoupled weight decay.
- **Negative sampling** (Word2Vec): gradient estimator efficiente per softmax con vocabolario enorme.
- **Teacher Forcing** vs scheduled sampling in training di modelli sequenziali.

## I tre regimi di convergenza

| Tasso | Errore $\|x_k - x^*\|$ dopo $k$ passi | Esempi | Costo per iter |
|---|---|---|---|
| **Sublineare** | $O(1/\sqrt{k})$ | SGD non convesso | $O(d)$ stocastico |
| **Lineare** | $O(\rho^k)$, $\rho < 1$ | GD, GC su SPD, Jacobi | $O(d)$ o $O(d^2)$ |
| **Superlineare** | $\|x_{k+1}-x^*\| / \|x_k - x^*\| \to 0$ | Quasi-Newton (BFGS), secanti | $O(d^2)$ |
| **Quadratica** | $\|x_{k+1}-x^*\| \leq C\|x_k - x^*\|^2$ | Newton vicino al minimo | $O(d^3)$ |

**Insight chiave**: il costo aumenta con il tasso. Un'iterazione di Newton vale tante iterazioni di GD; SGD è "lento" per iterazione *singola* ma vince in $n$ grande perché ogni iterazione costa $O(d)$ invece di $O(nd)$.

## Sei principi che attraversano tutti i corsi

### 1. Sufficient decrease
Ogni metodo deterministico (Armijo, Wolfe) garantisce $f(x_{k+1}) \leq f(x_k) - c \alpha_k \|d_k\|^2$. Senza questo, oscillazioni.

### 2. Direzione di discesa
$d_k$ è di discesa se $\nabla f(x_k)^\top d_k < 0$. Newton sceglie $d = -H^{-1}\nabla f$ (di discesa solo se $H \succ 0$). Quasi-Newton mantiene $H_k \succ 0$ tramite update BFGS.

### 3. Step decrescente per la stocastica
$\sum \alpha_k = \infty$, $\sum \alpha_k^2 < \infty$ → $\alpha_k \asymp 1/k$ tipico. Bilancia esplorazione (∞) e stabilizzazione (varianza somma).

### 4. Precondizionamento
Cambiare base: $y = M^{1/2} x$ trasforma $f(x) \to \tilde f(y)$ con condizionamento migliore. Usato in PCG (MetNum), Adam (ML, scaling per coordinata), natural gradient.

### 5. Proiezione vs penalizzazione
Per vincoli $x \in C$: due strategie.
- **Proiezione** (Frank-Wolfe, gradient projection): $x_{k+1} = \Pi_C(x_k - \alpha\nabla f)$. Richiede $\Pi_C$ calcolabile.
- **Penalizzazione**: aggiungi $\mu \cdot \mathrm{dist}(x, C)^2$ alla loss; $\mu \to \infty$. Usato in Lagrangiano aumentato.

### 6. Trust region vs line search
Due strategie globali per Newton:
- **Line search**: scegli $d$ poi cerca $\alpha$ ottimale.
- **Trust region**: scegli un raggio $\Delta$, ottimizza $f$ sul modello quadratico in $B(x_k, \Delta)$.

## Connessioni con altri argomenti trasversali

- **[[SVD e decomposizione spettrale]]**: il [[Numero di condizionamento]] $K_2 = \sigma_1/\sigma_n$ governa $\rho$ in tutti i metodi del prim'ordine. La decomposizione spettrale del Hessiano predice il tasso locale di Newton e quasi-Newton.
- **[[Catene di Markov e MCMC]]**: SGD può essere visto come Langevin discretizzato — catena con stazionaria $\propto e^{-f(\Theta)/T}$ per $T \to 0$. [[Simulated Annealing]] è MCMC con cooling. La connessione lega ottimizzazione e sampling.
- **[[Reti neurali]]**: backpropagation è il calcolo del gradiente che alimenta SGD. La non convessità del landscape spiega perché SGD converge a punti stazionari ma non globali, e perché questo è "abbastanza buono" in pratica.

## Punti di attenzione (errori comuni)

1. **Newton è quadratico solo localmente.** Lontano dal minimo può divergere o andare verso massimi/selle. Servono safeguards (Levenberg-Marquardt).
2. **GD su funzioni mal condizionate è lento.** $\rho = (K-1)/(K+1) \to 1$ per $K \to \infty$. Soluzione: GC, precondizionamento, Adam.
3. **SGD ≠ GD con piccolo batch.** Le proprietà di convergenza (varianza, scheduling) sono qualitativamente diverse.
4. **Convergenza ≠ ottimo globale.** Tutti i metodi iterativi convergono a *un* punto stazionario; selle e minimi locali sono comuni in non convesso.
5. **Il numero di condizionamento dipende dalla parametrizzazione.** Riscalare le coordinate cambia $K$. Da qui l'importanza di normalizzare i dati.

## Pagine collegate

- Concetti centrali: [[Discesa del gradiente]], [[Stochastic Gradient Descent]], [[Approssimazione stocastica]]
- Metodi: [[Metodo di Newton (ottimizzazione)]], [[Metodi Quasi-Newton]], [[Gradiente coniugato]], [[Frank-Wolfe e gradiente proiettato]]
- Vincoli: [[Condizioni KKT]], [[Proiezione su insiemi convessi]], [[Convessità]]
- Step: [[Metodo di Armijo]]
- Stocastico: [[Metodo del corrispondente stocastico]], [[Simulated Annealing]], [[Metodo Cross-Entropy]]
- Linear-algebrico: [[Metodi iterativi per sistemi lineari]], [[Metodi per equazioni non lineari]], [[Teorema delle Contrazioni]]
- Condizionamento: [[Numero di condizionamento]]
- Applicazioni: [[Algoritmo del percettrone]], [[Backpropagation]]

## Fonti aggregate

- [[Dispense Ottimizzazione — Galletti]] (cap. 1-5 — teoria, GD, Newton, KKT, vincoli)
- [[Dispense Metodi Numerici — Galletti]] (cap. 4-5 — sistemi non lineari, GC, contrazioni)
- [[Dispense Machine Learning — Galletti]] (§4 — GD, SGD)
- [[Dispense MatML — Galletti]] (§3 — approssimazione stocastica, SA, CE)
- [[Dispense InfML — Galletti]] (§3-4 — varianti SGD)
