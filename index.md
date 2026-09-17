# Indice della Wiki

Catalogo navigabile di tutto ciò che è stato compilato. Aggiornato a ogni ingest.

> **Come usarlo:** scorri per categoria, clicca su una pagina per aprirla. Cerca per tag con la search di Obsidian (`Ctrl+Shift+F`). Le pagine in stato 🟡 sono scheletri (programma estratto, contenuti non ancora ingeriti); le 🟢 sono complete.

---

## 📚 Corsi
*Una pagina per ogni corso universitario. Punto d'ingresso per studiare la materia. Tutti gli scheletri sono basati sulle dispense di Marco Galletti, A.A. 2024/25 e 2025/26, corso di laurea SMIA, Sapienza.*

| Corso                                      | Docente                  | A.A.  | Stato |
| ------------------------------------------ | ------------------------ | ----- | ----- |
| [[Algebra Lineare]]                        | Malvenuto                | 24/25 | 🟢    |
| [[Algoritmi e Complessità]]                | Panconesi + Chierichetti | 24/25 | 🟢    |
| [[Analisi Matematica I]]                   | Martinazzi               | 24/25 | 🟢    |
| [[Analisi Matematica II]]                  | Galise                   | 24/25 | 🟢    |
| [[Architetture degli Elaboratori]]         | Pontarelli               | 25/26 | 🟢    |
| [[Fondamenti di Intelligenza Artificiale]] | Baccini                  | 24/25 | 🟢    |
| [[Gestione dei Dati]]                      | Poggi                    | 24/25 | 🟢    |
| [[Informatica per il Machine Learning]]    | Silvestri                | 25/26 | 🟢    |
| [[Machine Learning]]                       | Rodolà                   | 24/25 | 🟢    |
| [[Matematica per il Machine Learning]]     | Agliari                  | 25/26 | 🟢    |
| [[Metodi Numerici]]                        | Puppo                    | 24/25 | 🟢    |
| [[Modelli Matematici per la Fisica I]]     | Caglioti                 | 24/25 | 🟢    |
| [[Modelli Matematici per la Fisica II]]    | Zamponi                  | 24/25 | 🟢    |
| [[Ottimizzazione]]                         | Sciandrone               | 24/25 | 🟢    |
| [[Probabilità e Statistica]]               | Isopi                    | 24/25 | 🟢    |
| [[Processi Stocastici]]                    | Isopi                    | 25/26 | 🟢    |
| [[Strutture Algebriche]]                   | Malvenuto                | 24/25 | 🟢    |
| [[Tecniche di Programmazione]]             | Trappolini + Fusco       | 24/25 | 🟢    |

---

## 🧠 Concetti
*Idee, definizioni, teoremi, modelli. Atomici e collegati tra loro.*

### Statistica di base (da MatML §1)
- [[Statistica descrittiva]] — [[Statistica inferenziale]]
- [[Media campionaria]] — [[Varianza campionaria]] — [[Outlier]]
- [[Intervallo di confidenza]] — [[Test di ipotesi]]
- [[Distribuzione t-Student]] — [[Distribuzione chi-quadro]] — [[Distribuzione F di Fisher-Snedecor]]
- [[Distribuzione Gamma]] — [[Distribuzione Inverse-Gamma]] — [[Distribuzione Beta]]

### Apprendimento statistico (da MatML §2)
- [[Apprendimento statistico]] — [[Funzione di perdita]] — [[Rischio teorico]] — [[Rischio empirico]] — [[ERM]]
- [[Bias-Variance trade-off]] — [[Errore di approssimazione e di stima]]
- [[Regressione polinomiale]] — [[Matrice di Vandermonde]] — [[Matrice di Hilbert]] — [[Minimi quadrati]]
- [[Rischio in-sample]] — [[Ottimismo]] — [[Cross-validation]] — [[BIC]]
- [[Stima di Massima Verosimiglianza]] — [[Divergenza di Kullback-Leibler]]
- [[Funzione generatrice dei momenti]] — [[Distribuzione Normale Multivariata]] — [[Modello lineare normale]]
- [[Apprendimento Bayesiano]] — [[Distribuzioni coniugate]] — [[Stima MAP]] — [[Intervalli di credibilità]]
- [[Formula di Bayes]]
- [[Disuguaglianza di Jensen]]

### Metodi Monte Carlo (da MatML §3)
- [[Metodi Monte Carlo]] — [[Generatore MRG]]
- [[Algoritmo di Box-Muller]] — [[Metodo della funzione inversa]] — [[Metodo accept-reject]]
- [[Catena di Markov]] — [[Bilancio dettagliato]]
- [[Metropolis-Hastings]] — [[Campionamento di Gibbs]] — [[Bootstrap]]
- [[Riduzione della varianza]] — [[Importance Sampling]]
- [[Simulated Annealing]] — [[Approssimazione stocastica]] — [[Metodo del corrispondente stocastico]]
- [[Metodo Cross-Entropy]]

### Probabilità e Statistica (da ProbStat — ingest profondo)
- [[Spazio di probabilità]] — [[Probabilità condizionata]] — [[Formula di Bayes]]
- [[Combinatoria]] — [[Lemma di Schwarz-Zippel]] — [[Metodo probabilistico]]
- [[Variabile aleatoria]] *(arricchita: caso continuo CDF/PDF, Uniforme, Esponenziale, Normale)*
- [[Funzione di ripartizione]] — CDF, quantili, Glivenko-Cantelli, trasformazione integrale
- [[Valore atteso]] — [[Varianza e covarianza]] — [[Attesa condizionata]]
- [[Distribuzione geometrica]] — [[Distribuzione di Poisson]] — [[Distribuzione esponenziale]]
- [[Disuguaglianza di Markov]] — [[Disuguaglianza di Chebyshev]] — [[Legge dei Grandi Numeri]]
- [[Stimatore]] — bias, MSE, consistenza, sufficienza

### Processi Stocastici (da Processi — ingest profondo + chiusura gap)
- [[Passeggiata aleatoria]] *(alias: Random Walk, Rovina del giocatore)* — [[Funzione generatrice delle probabilità]]
- [[Processo di nascita e morte]] — [[Generatore infinitesimale]] — [[Catena immersa]]
- [[Processo di Poisson (continuo)]] — assiomi, interarrivi $\mathrm{Exp}(\lambda)$, sovrapposizione/thinning
- [[Equazione logistica]] — limite deterministico di processi nascita-morte
- [[Teorema ergodico]] — irriducibilità+aperiodicità+ricorrenza positiva → $P^n_{ij} \to \pi_j$
- [[Catena di Markov]] *(arricchita: teoria formale, ergodico, classi comunicanti)*

### Tecniche di Programmazione (da TecProg — ingest profondo)
- [[Complessità computazionale]] — [[Divide et Impera]] — [[Master Theorem]]
- [[Merge Sort]] — [[Quick Sort]] — [[Heap Sort]] — [[Quick Select]]
- [[Strutture dati]] — [[Tabella hash]] — [[Albero binario di ricerca]]
- [[Programmazione dinamica]] — [[Knapsack]]
- [[Grafo]] — [[BFS e DFS]]
- [[Algoritmo di Dijkstra]] — [[Algoritmo di Bellman-Ford]] — [[Minimum Spanning Tree]]
- [[Algoritmo di Prim]] — [[Algoritmo di Kruskal]]
- [[Algoritmo di Karatsuba]] — [[Algoritmo di Strassen]]

### Ottimizzazione (da Ottimizzazione — ingest profondo)
- [[Problema di ottimizzazione]] — [[Convessità]]
- [[Condizioni di ottimalità]] — [[Metodo di Armijo]]
- [[Gradiente coniugato]] — [[Metodo di Newton (ottimizzazione)]]
- [[Condizioni KKT]] — [[Proiezione su insiemi convessi]]
- [[Frank-Wolfe e gradiente proiettato]] — [[Metodi Quasi-Newton]]
- [[Algoritmo del percettrone]]

### Fondamenti di Intelligenza Artificiale (da FondAI — ingest profondo)
- [[Agente intelligente]] — PEAS, tipi di agenti PS/KB
- [[Ricerca A*]] — $f(n) = g(n) + h(n)$, ammissibilità, consistenza, ottimalità
- [[Logica proposizionale]] — sintassi, semantica, modelli, tautologie
- [[Conseguenza logica]] — $F_1 \models F_2$, model checking
- [[Alberi di Beth]] — refutazione automatica
- [[Sistema Hilbertiano]] — HAL, derivabilità $\Phi \vdash A$, correttezza/completezza
- [[Risoluzione (RES)]] — CNF, clausola vuota $\bot$, completezza per refutazione
- [[Clausole di Horn]] — definite, fatti, regole, goal
- [[Concatenazione in avanti e all'indietro]] — PL-CA, grafo AND-OR
- [[Logica del primo ordine]] — predicati, quantificatori, decidibilità, unificazione, Skolem

### Algoritmi e Complessità (da AlgComp — ingest profondo)
- [[Stable Matching]] — Gale-Shapley, best/worst, $O(n^2)$
- [[Algoritmo greedy]] — paradigma, tecnica di scambio
- [[Interval Scheduling]] — earliest finish, ottimalità
- [[Interval Partitioning]] — profondità, heap $O(n \log n)$
- [[Algoritmo di Huffman]] — prefix-code, ABL minima
- [[Weighted Interval Scheduling]] — DP, ricorrenza $\mathrm{OPT}(j)$
- [[Problema degli esperti]] — WM, Randomized WM, lower bound
- [[Locality Sensitive Hashing]] — Jaccard, Single Linkage
- [[NP-completezza]] — P/NP, Cook-Levin, SAT≤Clique≤IS≤VC≤Knapsack
- [[Macchina di Turing]] — definizione, Halting, decidibilità

### Strutture Algebriche (da StrAlg — ingest profondo)
- [[Relazione di equivalenza]] — [[Relazione d'ordine]]
- [[Principio di induzione]]
- [[Massimo comun divisore]] — [[Algoritmo di Euclide]]
- [[Aritmetica modulare]] — ℤ_n, U(ℤ_n), φ(n), Eulero-Fermat
- [[Teorema Binomiale]] — [[Permutazione]]
- [[Gruppo (struttura algebrica)]] — [[Gruppo simmetrico]]
- [[Classi di coniugio]] — struttura ciclica in S_n
- [[Sottogruppo]] — sottogruppo generato, normale
- [[Teorema di Lagrange]] — classi laterali, corollari
- [[Omomorfismo di gruppi]] — nucleo, 1° teorema isomorfismo
- [[Anello e campo]] — ℤ_p campo per p primo

### Algebra Lineare (da AlgLin — ingest profondo)
- [[Spazio vettoriale]] *(arricchita: campo K, esempi Mₘₙ e Rₜ[x])* — [[Sottospazio vettoriale]] — [[Base di uno spazio vettoriale]]
- [[Dipendenza lineare]] — [[Sottospazio generato]]
- [[Formula di Grassmann]] — dim(U+W)+dim(U∩W)=dimU+dimW, somma diretta
- [[Algoritmo di Gauss-Jordan]] — RREF, teorema del calcolo (6 applicazioni), Rouché-Capelli
- [[Applicazione lineare]] — matrice associata, ker/Im, cambio base A'=C⁻¹AB, similitudine
- [[Teorema della dimensione (algebra lineare)]] — n=n(T)+rg(T), rank-nullity
- [[Polinomio caratteristico]] — p_T(λ)=det(A-λI), m_a, m_g
- [[Diagonalizzazione]] — teorema m_g=m_a, algoritmo 5-step, forma di Jordan
- [[Mappe lineari]] *(arricchita: nucleo/immagine, rank-nullity)*
- [[Autovalori e autovettori]] *(arricchita: autospazio V_{λ₀}, m_a/m_g, diagonalizzabilità)*

### Machine Learning (da ML — ingest profondo)
- [[Spazio vettoriale]] — [[Mappe lineari]] *(algebra lineare §2)*
- [[Regressione lineare]] — [[Regressione polinomiale]] — [[Regressione logistica]]
- [[Funzione sigmoide]] — [[Cross-entropy]] — [[Overfitting e underfitting]]
- [[Regolarizzazione di Tikhonov]] — [[Curse of dimensionality]]
- [[Discesa del gradiente]] — [[Stochastic Gradient Descent]]
- [[Multi-Layer Perceptron]] — [[Backpropagation]] — [[Grafo computazionale]]
- [[Funzione sigmoide]] — [[Teorema di approssimazione universale]]
- [[Autovalori e autovettori]] — [[Quoziente di Rayleigh]] — [[Power iteration]]
- [[Singular Value Decomposition]] — [[Principal Component Analysis]]
- [[Norma di Frobenius]]
- [[Spazio metrico]] — [[Embedding isometrico]]
- [[Multidimensional Scaling]] — [[Stochastic Neighbor Embedding]] — [[t-SNE]]
- [[Decision Tree]] — [[Random Forest]]
- [[AdaBoost]] — [[Gradient Boosting]]

### Metodi Numerici (da MetNum — ingest profondo)
- [[Numeri di macchina e aritmetica floating-point]] — IEEE 754, eps_M, cancellazione catastrofica
- [[Sistemi lineari — metodi diretti]] — Gauss, LU+pivoting PA=LU, Cholesky, costo O(n³/3)
- [[Numero di condizionamento]] — K(A)=‖A‖‖A⁻¹‖, K₂(SPD)=λmax/λmin, K₂(ortog)=1
- [[Metodi iterativi per sistemi lineari]] — Jacobi, Gauss-Seidel, Richardson (ρ=(K-1)/(K+1))
- [[Gradiente coniugato]] *(arricchita: GC lineare, α_k/β_k, ρ=√(K-1)/√(K+1), PCG)*
- [[Metodi per equazioni non lineari]] — bisezione, Newton (quadratica), secanti, punto fisso
- [[Teorema delle Contrazioni]] — Banach-Caccioppoli, esistenza/unicità punto fisso
- [[Interpolazione di Lagrange]] — basi di Lagrange, fenomeno di Runge, Gauss-Lobatto
- [[Integrazione numerica]] — trapezi O(h²), Cavalieri-Simpson O(h⁴), Gauss (grado 2n+1)
- [[Fattorizzazione QR]] — Householder, QR ridotta, minimi quadrati sovradeterminati
- [[Cerchi di Gershgorin]] — spec(A)⊂∪C_i, separazione → conta autovalori
- [[Metodo delle potenze]] — autovalore dominante, potenza inversa, shift
- [[Algoritmo QR per autovalori]] — iterazione QR, fattorizzazione di Schur, Hessenberg
- [[Autovalori e autovettori]] *(arricchita: Gershgorin, power method, Schur)*
- [[Singular Value Decomposition]] *(arricchita: σ₁=‖A‖₂, rank=#σ nonzeri, SVD ridotta, Golub-Reinsch)*
- [[Metodi numerici per ODE]] — Eulero esplicito/implicito, A-stabilità, Runge-Kutta 4

### Informatica per il Machine Learning (da InfML — ingest profondo)
- [[Lasso e Elastic Net]] — regolarizzazione L1, Elastic Net, sparsità
- [[Metriche di classificazione]] — confusion matrix, precision, recall, F1, ROC-AUC
- [[Metriche di ranking]] — Precision@k, MRR, MAP, NDCG
- [[Learning to Rank]] — pointwise/pairwise/listwise, RankNet, LambdaRank
- [[Sistemi di raccomandazione]] — matrix factorization $R \approx QP$
- [[Dropout]] — co-adaptation, ensemble interpretation, inverted dropout
- [[Sentiment Analysis]] — task NLP multiclasse
- [[Bag of Words e TF-IDF]] — BoW, TF-IDF, hashing trick
- [[Language Model]] — K-gram, smoothing, OOV, neural LM, autoregressivo, Teacher Forcing
- [[Word Embedding]] — Word2Vec (CBOW, Skip-Gram), Negative Sampling, analogie vettoriali
- [[Recurrent Neural Network]] — parameter sharing, BPTT, vanishing/exploding gradient
- [[LSTM]] — 3 gate (forget, input, output), cell state, highway gradient
- [[GRU]] — 2 gate (reset, update), confronto con LSTM
- [[Seq2Seq e Encoder-Decoder]] — many-to-many, context vector, Teacher Forcing, information bottleneck
- [[Meccanismo di Attention]] — Bahdanau, alignment score, self-attention, scaled dot-product
- [[Transformer]] — Multi-Head Attention, Positional Encoding, Encoder-Decoder, parallelizzazione
- [[BERT]] — MLM, NSP, fine-tuning (classificazione, NER, NLI)
- [[Convolutional Neural Network]] — conv 1D/2D, pooling, AlexNet, VGGNet, YOLO, segmentazione
- [[Residual Connection]] — skip connection, ResNet, degradation problem, loss surface smooth
- [[Softmax]] *(già in ML, arricchita da InfML)*

### Architetture degli Elaboratori (da Architetture — ingest profondo)
- [[Architettura RISC-V]] — ISA, metriche CPU time/CPI, formati R/I/S/B, ABI (ra/sp/a0-a7), stack
- [[Aritmetica dei computer]] — complemento a 2, overflow, IEEE 754 FP, FMA, SIMD (SSE/AVX/AVX-512)
- [[Pipeline e processore]] — pipeline 5 stadi, hazard (forwarding, branch prediction 1/2 bit), out-of-order, ROB, register renaming
- [[Gerarchia di memoria e cache]] — locality, DRAM, direct-mapped, AMAT, N-way, LRU, write-back, 3C, snooping, Amdahl, Flynn, SMT
- [[GPU e CUDA]] — DSA vs ASIC, systolic arrays, roofline, TPU, grid/block/warp, shared memory, tiling, bank conflicts, coalescing

### Gestione dei Dati (da GestioneDati — ingest profondo)
- [[Modello relazionale]] — relazione, schema/istanza, algebra relazionale (σ/π/ρ/join), NULL, CWA, superchiave, FK
- [[SQL]] — DDL/DML/DQL; SELECT semantica, JOIN, aggregazioni, subquery, CASE, VIEW
- [[Modello Entità-Relazione]] — entità, attributi, relazioni ER, ISA, cardinalità, identificatori, ridondanze

### Analisi Matematica II (da AnalisiII — ingest profondo)
- [[Successioni di funzioni]] — conv. puntuale vs uniforme, M-test, serie di potenze, Cauchy-Hadamard, sviluppabilità
- [[Spazio metrico]] *(arricchita: completezza, Cauchy, Banach, norme $\|\cdot\|_p$, Cauchy-Schwarz)*
- [[Disuguaglianza di Cauchy-Schwarz]]
- [[Calcolo differenziale in più variabili]] — gradiente, differenziabilità, piano tangente, Taylor 2°ord., Hessiana, ottimizzazione
- [[Integrale di Lebesgue]] — misura, Beppo Levi, Fatou, dominata, Fubini/Tonelli, cambi variabile
- [[Spazi Lp]] — $L^p(E)$ Banach, Young, Hölder, Minkowski, $L^\infty$
- [[Curve e integrali curvilinei]] — curve regolari, lunghezza, int. I/II specie, forme esatte, potenziale

### Analisi Matematica I (da AnalisiI — ingest profondo)
- [[Limite di una funzione]] — def. topologica + ε-δ, algebra dei limiti, squeeze, forme indeterminate, gerarchia infiniti
- [[Limiti notevoli]] — 6 limiti (sin x/x, (1+1/x)^x→e, …), o-piccoli (7 proprietà), espansioni asintotiche
- [[Successioni]] — convergenza, BW (dim. bisezione), serie geometrica e armonica, 4 criteri, conv. assoluta
- [[Continuità di una funzione]] — ε-δ, Weierstrass (dim.), TVI/Bolzano (dim.), continuità uniforme
- [[Derivata]] — rapporto incrementale, tabella derivate, Leibniz/catena/inversa, Fermat, Rolle, Lagrange, monotonia/convessità
- [[Polinomi di Taylor]] — $T^n_{f;x_0}$, resto di Peano e Lagrange (via Cauchy), sviluppi notevoli
- [[Integrale di Riemann]] — somme di Darboux, TFC I/II, per parti, sostituzione, frazioni parziali, impropri, criterio integrale
- [[Equazione differenziale ordinaria]] *(arricchita: seconda fonte AnalisiI §7)*

### Modelli Matematici per la Fisica I (da MMFI — ingest profondo)
- [[Equazione differenziale ordinaria]] — problema di Cauchy, Lipschitz, Picard, Grönwall
- [[Oscillatore armonico]] — $T=2\pi\sqrt{m/k}$, piano delle fasi, pendolo, energia $H=T+U$
- [[Stabilità di un punto di equilibrio]] — Lyapunov, linearizzato, Poincaré-Bendixson, Van der Pol
- [[Meccanica Lagrangiana]] — EL, principio di Hamilton, variazionale, brachistocrona
- [[Leggi di Keplero]] — massa ridotta, orbita ellittica, 3 leggi, $T^2/a^3=4\pi^2/GM$

### Modelli Matematici per la Fisica II (da MMFII — ingest profondo)
- [[Funzione generatrice dei momenti]] *(arricchita: cumulanti, TLC, grandi deviazioni)*
- [[Teoria delle grandi deviazioni]] — bound di Cramér, $\Omega_X(u)$, Gumbel, Fréchet
- [[Entropia di Shannon]] — $H(X)=-\sum p_i\log_2 p_i$, informazione mutua, divergenza KL
- [[Principio di massima entropia]] — MaxEnt, distribuzione di Boltzmann-Gibbs, energia libera
- [[Modello di Ising]] — matrice di trasferimento, $Z=\text{Tr}(T^N)$, correlazioni $e^{-r/\xi}$, 1D
- [[Modello di Curie-Weiss e Hopfield]] — campo medio $m=\tanh(\beta(Jm+h))$, $T_c=J$, Hopfield

---

## 👤 Persone
*Autori, scienziati, filosofi, figure storiche citate.*

### Docenti del corso
- [[Agliari, Elena]] — prof.ssa MatML, Sapienza
- [[Baccini, Federica]] — prof.ssa FondAI, Sapienza
- [[Fusco, Federico]] — prof. TecProg (II parte), Sapienza
- [[Galletti, Marco]] — autore dispense (tutti i corsi SMIA)
- [[Rodolà, Emanuele]] — prof. Machine Learning, Sapienza
- [[Isopi, Marco]] — prof. Prob-Stat + Processi Stocastici, Sapienza
- [[Malvenuto, Claudia]] — prof.ssa AlgLin + StrAlg, Sapienza
- [[Martinazzi, Luca]] — prof. AnalisiI, Sapienza
- [[Puppo, Gabriella]] — prof.ssa Metodi Numerici, Sapienza
- [[Trappolini, Giovanni]] — prof. TecProg (I parte), Sapienza

### Matematici e statistici
- [[Bayes, Thomas]] — Teorema di Bayes
- [[Bellman, Richard]] — programmazione dinamica, Bellman-Ford
- [[Efron, Bradley]] — Bootstrap
- [[Ford, Lester]] — algoritmo di Bellman-Ford
- [[Bernoulli, Jakob]] — probabilità discreta, LGN
- [[Boltzmann, Ludwig]] — distribuzione di Boltzmann-Gibbs
- [[Box, George]] — algoritmo Box-Muller
- [[Cauchy]] — analisi
- [[Fletcher, Roger]] — gradiente coniugato (Fletcher-Reeves), BFGS
- [[Karush, William]] — condizioni KKT (1939)
- [[Kuhn, Harold]] — condizioni KKT (1951, con Tucker)
- [[Sciandrone, Marco]] — prof. Ottimizzazione, Sapienza
- [[Tucker, Albert]] — condizioni KKT (1951, con Kuhn)
- [[Chebyshev, Pafnuty]] — disuguaglianza di Chebyshev
- [[Cholesky, André-Louis]] — decomposizione di Cholesky
- [[Dijkstra, Edsger]] — algoritmo shortest path
- [[Fisher, Ronald]] — MLE, distribuzione F
- [[Frobenius]] — norma di Frobenius
- [[Gauss, Carl Friedrich]] — minimi quadrati, varianza
- [[Gelatt, Charles D.]] — Simulated Annealing
- [[Geman, Stuart e Donald]] — Campionamento di Gibbs
- [[Gibbs, J. Willard]] — termodinamica statistica
- [[Hastings, W.K.]] — algoritmo di Metropolis-Hastings
- [[Hilbert, David]] — matrice di Hilbert
- [[Jensen, Johan]] — disuguaglianza di Jensen
- [[Karatsuba, Anatoly]] — moltiplicazione veloce O(n^{1.585})
- [[Khinchin, Aleksandr]] — entropia di Shannon
- [[Schwarz, Hermann Amandus]] — disuguaglianza di Cauchy-Schwarz
- [[Kirkpatrick, Scott]] — Simulated Annealing
- [[Kullback, Solomon]] — divergenza di Kullback-Leibler
- [[Kolmogorov, Andrey]] — assiomatizzazione della probabilità
- [[Kruskal, Joseph]] — MST, MDS
- [[Leibler, Richard A.]] — divergenza di Kullback-Leibler
- [[Laplace, Pierre-Simon]] — approssimazione di Laplace, BIC
- [[Markov, Andrey]] — catene di Markov
- [[Metropolis, Nicholas]] — algoritmo di Metropolis
- [[Newton, Isaac]] — metodo di Newton, analisi
- [[Muller, Mervin]] — algoritmo Box-Muller
- [[Poisson, Siméon Denis]] — distribuzione di Poisson
- [[Prim, Robert]] — algoritmo di Prim (MST)
- [[Rubinstein, Reuven]] — metodo Cross-Entropy
- [[Strassen, Volker]] — moltiplicazione di matrici O(n^{2.807})
- [[Vecchi, Mario P.]] — Simulated Annealing
- [[Tikhonov]] — regolarizzazione di Tikhonov
- [[Vandermonde, Alexandre]] — matrice di Vandermonde
- [[Weierstrass]] — teorema di Stone-Weierstrass

---

## 🌐 Argomenti trasversali e MOC
*Temi che attraversano più corsi (argomenti) + mappe di studio per cluster (MOC).*

### Map of Content (MOC) — guide di studio per cluster
- [[MOC — Machine Learning]] — 59 concetti, percorso pedagogico per ML/InfML/MatML
- [[MOC — Probabilistica]] — 54 concetti, percorso ProbStat/Processi/MatML/MMFII
- [[MOC — Algoritmi]] — 41 concetti, percorso TecProg/AlgComp/FondAI
- [[MOC — Algebra]] — 38 concetti, percorso AlgLin/StrAlg/MetNum (spettrale)

### Argomenti trasversali — sintesi multi-corso

- [[SVD e decomposizione spettrale]] — 5 corsi (AlgLin, MetNum, ML, MatML, InfML); autovalori, SVD, PCA, pseudoinversa, condizionamento
- [[Catene di Markov e MCMC]] — 4 corsi (ProbStat, Processi, MatML, MMFII); ergodicità, bilancio dettagliato, Metropolis-Hastings, Simulated Annealing
- [[Reti neurali]] — 4 corsi (ML, InfML, Ottimizzazione, MMFII); MLP, backprop, RNN/LSTM/Transformer, percettrone, Hopfield
- [[Ottimizzazione iterativa]] — 5 corsi (Ottimizzazione, ML, MetNum, MatML, InfML); GD/SGD, Newton, GC, KKT, approssimazione stocastica
- [[Probabilità bayesiana e inferenza]] — 5 corsi (ProbStat, MatML, MMFII, InfML, ML); prior/posterior, MAP, BIC, Bernstein-von Mises, ELBO
- [[Entropia e information theory]] — 5 corsi (MMFII, MatML, ML, InfML, ProbStat); Shannon, KL, cross-entropy, MaxEnt, mutual information
- [[Regolarizzazione]] — 5 corsi (ML, MatML, InfML, MetNum, Ottimizzazione); ridge/Lasso, MAP gaussiano, dropout, early stopping, filter factor SVD
- [[Grafi e ricerca]] — 5 corsi (TecProg, AlgComp, FondAI, ML, Processi); BFS/DFS, Dijkstra/A\*, MST, NP-completezza, grafo computazionale, catene come grafi

---

## 📄 Fonti
*Una entry per ogni fonte ingerita in profondità.*

| Fonte | Corso | Data ingest | Pagine create |
|---|---|---|---|
| [[Dispense MatML — Galletti]] | [[Matematica per il Machine Learning]] | 2026-05-04 | 51 concetti, 16 persone (2 ingest) |
| [[Dispense ProbStat — Galletti]] | [[Probabilità e Statistica]] | 2026-05-04 (+2026-05-06) | 15 concetti, 4 persone (ingest profondo + approfondimento fondamenti) |
| [[Dispense TecProg — Galletti]] | [[Tecniche di Programmazione]] | 2026-05-04 | 14 concetti, 7 persone (ingest profondo) |
| [[Dispense AlgLin — Galletti]] | [[Algebra Lineare]] | 2026-05-05 | 10 concetti nuovi, 3 aggiornamenti |
| [[Dispense StrAlg — Galletti]] | [[Strutture Algebriche]] | 2026-05-05 | 15 concetti nuovi (ingest profondo) |
| [[Dispense AnalisiI — Galletti]] | [[Analisi Matematica I]] | 2026-05-06 | 7 concetti nuovi, 1 aggiornamento (ingest profondo) |
| [[Dispense Architetture — Galletti]] | [[Architetture degli Elaboratori]] | 2026-05-06 | 5 concetti nuovi (ingest profondo) |
| [[Dispense GestioneDati — Galletti]] | [[Gestione dei Dati]] | 2026-05-06 | 3 concetti nuovi (ingest profondo) |
| [[Dispense AnalisiII — Galletti]] | [[Analisi Matematica II]] | 2026-05-06 | 5 concetti nuovi, 1 aggiornamento (ingest profondo) |
| [[Dispense Processi Stocastici — Galletti]] | [[Processi Stocastici]] | 2026-05-04 (+2026-05-06) | 8 concetti, 2 aggiornamenti (ingest profondo + chiusura gap) |
| [[Dispense Ottimizzazione — Galletti]] | [[Ottimizzazione]] | 2026-05-04 | 11 concetti, 1 aggiornamento (ingest profondo) |
| [[Dispense FondAI — Galletti]] | [[Fondamenti di Intelligenza Artificiale]] | 2026-05-04 | 10 concetti, 1 persona (ingest profondo) |
| [[Dispense Machine Learning — Galletti]] | [[Machine Learning]] | 2026-04-30 (+2026-05-04) | 25 concetti, 4+1 persone (ingest profondo + completamento) |
| [[Dispense InfML — Galletti]] | [[Informatica per il Machine Learning]] | 2026-05-05 | 20 concetti nuovi, 5 aggiornamenti, 1 persona |
| [[Dispense Metodi Numerici — Galletti]] | [[Metodi Numerici]] | 2026-05-05 | 13 concetti nuovi, 3 aggiornamenti, 1 persona |
| [[Dispense Algoritmi — Galletti]] | [[Algoritmi e Complessità]] | 2026-05-05 | 10 concetti nuovi, 1 aggiornamento (ingest profondo) |
| [[Dispense MMFI — Galletti]] | [[Modelli Matematici per la Fisica I]] | 2026-05-06 | 5 concetti nuovi (ingest profondo) |
| [[Dispense MMFII — Galletti]] | [[Modelli Matematici per la Fisica II]] | 2026-05-06 | 5 concetti nuovi, 1 aggiornamento (ingest profondo) |

**Raw disponibili (in attesa di ingest profondo):** *nessuno — tutti i corsi completati.*

---

## ❓ Domande esplorate
*Risposte filed-back, derivate da query.*

_Nessuna domanda ancora._

---

## 📝 Esercizi & esami
*Esercitazioni ed esami passati ingeriti. Vedi protocollo §5.4 in `CLAUDE.md`.*

```dataview
TABLE WITHOUT ID
  file.link AS "Esercitazione",
  corso AS "Corso",
  data AS "Data",
  difficoltà AS "Difficoltà"
FROM "wiki/esercizi"
SORT data DESC
```

**Raw disponibili (in attesa di ingest):** *nessuno.*

---

## 🗺️ Sintesi globale

- [[panoramica]] — 18 corsi, 5 cluster tematici, 8 fili trasversali, pagine hub, guida alla navigazione
- [[dashboard]] — statistiche live (richiede plugin Dataview): pagine per tipo/cluster, fonti, concetti recenti, orfane, hub

---

## 📊 Statistiche live

*(Si renderizzano solo con plugin Dataview attivo. Vedi [[dashboard]] per la versione completa.)*

**Pagine per tipo:**

```dataview
TABLE WITHOUT ID
  tipo AS "Tipo",
  length(rows) AS "Pagine"
FROM "wiki"
WHERE tipo
GROUP BY tipo
SORT length(rows) DESC
```

**Concetti per cluster:**

```dataview
TABLE WITHOUT ID
  cluster AS "Cluster",
  length(rows) AS "Pagine"
FROM "wiki/concetti" OR "wiki/argomenti"
WHERE cluster
GROUP BY cluster
SORT length(rows) DESC
```

**Ultime 5 modifiche:**

```dataview
TABLE WITHOUT ID
  file.link AS "Pagina",
  ultima-modifica AS "Modificato"
FROM "wiki/concetti" OR "wiki/argomenti"
SORT ultima-modifica DESC
LIMIT 5
```

---

*Ultimo aggiornamento: 2026-05-06 — Pulizia finale lint: +3 concetti (Funzione di ripartizione, Teorema ergodico, Schwarz). 352 pagine totali.*
