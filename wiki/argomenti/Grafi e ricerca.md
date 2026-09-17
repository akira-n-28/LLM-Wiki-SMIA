---
tipo: argomento
titolo: Grafi e ricerca
tag: [trasversale, algoritmi, grafi, ricerca, ai]
cluster: trasversale
corsi: [Tecniche di Programmazione, Algoritmi e Complessità, Fondamenti di Intelligenza Artificiale, Machine Learning, Processi Stocastici]
ultima-modifica: 2026-05-06
---

# Grafi e ricerca

Argomento trasversale che attraversa **5 corsi**. Il grafo è la struttura dati universale di tutta la computer science: lo si vede come oggetto da visitare/ottimizzare in [[Tecniche di Programmazione]] e [[Algoritmi e Complessità]], come spazio di stati astratto in [[Fondamenti di Intelligenza Artificiale]], come grafo computazionale in [[Machine Learning]], e come supporto della dinamica in [[Processi Stocastici]] (catene di Markov).

## Il nucleo unificante

Un grafo $G = (V, E)$ con $n = |V|$ e $m = |E|$ accoglie tre famiglie di problemi:

| Famiglia | Domanda | Esempi |
|---|---|---|
| **Visita / connettività** | quali nodi sono raggiungibili? | BFS, DFS, componenti, sort topologico |
| **Cammini minimi** | qual è il cammino ottimo da $s$ a $t$? | Dijkstra, Bellman-Ford, A*, MST |
| **Decisione** | il grafo ha la proprietà $P$? | clique, vertex cover, Hamilton, NP-completi |

I tre regimi di complessità classici ricorrono ovunque:
- **Polinomiale efficiente**: $O(m + n)$ o $O(m\log n)$ per problemi "facili" (visita, MST, shortest path).
- **Polinomiale brutale**: $O(n^3)$ per all-pairs (Floyd-Warshall) o per matrici di adiacenza.
- **NP-completo**: ricerca esponenziale; richiede euristica ([[Ricerca A*]]) o approssimazione.

## Il tour dei corsi

### [[Tecniche di Programmazione]] — la base algoritmica
La seconda metà del corso. Ingredienti:

- **Rappresentazioni**: lista di adiacenza (sparse, $O(n+m)$) vs matrice (densa, $O(n^2)$).
- **[[BFS e DFS]]**: visita in $O(m)$ — è il workhorse di tutto. BFS dà shortest path su grafi non pesati; DFS dà sort topologico, articolazioni, fortemente connesse.
- **Cammini minimi pesati**: [[Algoritmo di Dijkstra]] in $O(m\log n)$ con min-heap (richiede pesi $\geq 0$); [[Algoritmo di Bellman-Ford]] in $O(nm)$ (gestisce pesi negativi, rileva cicli negativi).
- **MST**: [[Algoritmo di Prim]] (Dijkstra-like, vertex-by-vertex) e [[Algoritmo di Kruskal]] (edge-by-edge, Union-Find). Entrambi $O(m\log n)$. **Cut property**: l'arco minimo che attraversa qualsiasi taglio è in qualche MST.

### [[Algoritmi e Complessità]] — la teoria
Visione più astratta. Tre temi:

- **Paradigmi algoritmici su grafi**:
  - **Greedy** ([[Algoritmo greedy]]): MST, [[Interval Scheduling]], [[Algoritmo di Huffman]] (alberi prefix-free).
  - **DP**: [[Weighted Interval Scheduling]], shortest path con vincoli (non da Bellman-Ford, ma DP esplicita).
  - **Divide et Impera**: closest pair, FFT (in spazio dei coefficienti).
- **[[Stable Matching]]** (Gale-Shapley) — non è un grafo classico ma struttura bipartita; algoritmo $O(n^2)$.
- **[[NP-completezza]]**: catena delle riduzioni **SAT ≤ Clique ≤ IS ≤ VC ≤ Knapsack**. Tutti problemi di grafi "duri".
- **[[Macchina di Turing]]**: definizione di decidibilità; il problema della terminazione è indecidibile.
- **[[Locality Sensitive Hashing]]**: ricerca approssimata su grafi di similarità.

### [[Fondamenti di Intelligenza Artificiale]] — il grafo come spazio di stati
Salto concettuale: il grafo non è dato esplicitamente, ma **generato implicitamente** da uno stato iniziale e da una funzione di successori. Da qui:

- **Ricerca non informata**: BFS, DFS uniform-cost, iterative deepening — tutti algoritmi del cluster TecProg, ma applicati a grafo astratto.
- **[[Ricerca A*]]**: il salto è l'**euristica $h(n)$** che stima il costo restante. Con $h$ ammissibile ($h \leq h^*$), A* è ottimale. Con $h$ consistente ($h(n) \leq c + h(n')$), A* è anche efficient (mai ri-espande nodi).
- **Equivalenza**: BFS = A* con $h \equiv 0$ e tutti i costi unitari; Dijkstra = A* con $h \equiv 0$.
- **Logica e ricerca**: [[Concatenazione in avanti e all'indietro]] su [[Clausole di Horn]] è ricerca su un grafo AND-OR; [[Risoluzione (RES)]] è ricerca nello spazio delle clausole.

### [[Machine Learning]] — il grafo computazionale
Il grafo come struttura per organizzare il **calcolo**, non per modellare relazioni.

- **[[Grafo computazionale]]**: nodi = operazioni, archi = dipendenze di dati. Il forward pass è una visita topologica; il backward pass è la stessa visita in reverse.
- **[[Backpropagation]]**: applicazione sistematica della regola della catena lungo il grafo computazionale, in $O(\text{dim})$.
- **Grafi delle reti**: GNN, GCN (non in syllabus dettagliato, ma nominati): regola di update basata su aggregazione locale dai vicini — astrazione di un BFS layer-per-layer con pesi.

### [[Processi Stocastici]] — il grafo come dinamica
Una [[Catena di Markov]] discreta è un grafo orientato pesato dove i pesi sono **probabilità di transizione**. Tutta la teoria delle catene è teoria di grafi:

- **Classi comunicanti** = componenti fortemente connesse del grafo.
- **Irriducibilità** = grafo fortemente connesso.
- **Periodo** di uno stato = mcd dei lunghezza-cicli che lo attraversano.
- **Random walk** $q(j\mid i) = 1/\deg(i)$: il caso più semplice, stazionaria $\propto \deg$.

## Le quattro versioni di shortest path

| Algoritmo | Pesi | Complessità | Caso d'uso |
|---|---|---|---|
| **BFS** | $w \equiv 1$ | $O(n+m)$ | grafo non pesato |
| **Dijkstra** | $w \geq 0$ | $O(m\log n)$ | shortest path single-source |
| **Bellman-Ford** | $w \in \mathbb{R}$ (anche $<0$) | $O(nm)$ | pesi negativi, detect cicli neg |
| **A\*** | $w \geq 0$ + euristica $h$ | dipende da $h$ | spazio di stati grande, $h$ buona |
| **Floyd-Warshall** | $w \in \mathbb{R}$ | $O(n^3)$ | all-pairs shortest paths |

**Insight**: A\* è Dijkstra "guidata" da $h$. Se $h \equiv 0$, A\* = Dijkstra. Se $h = h^*$ (oracolo), A\* espande solo il cammino ottimo.

## I cinque tipi di grafo

1. **Statico esplicito** (TecProg): $V, E$ enumerati. Lista di adiacenza in memoria.
2. **Statico implicito** (FondAI): $V$ stati, successori generati da funzione. Esponenziale o infinito.
3. **Dinamico** (Processi): pesi sugli archi sono probabilità; nodi sono stati di un sistema.
4. **Computazionale** (ML): dipendenze di calcolo; visitato per evaluation, non per ottimizzazione.
5. **Bipartito / matching** (AlgComp): due classi di nodi, archi solo tra classi (es. Stable Matching, raccomandazione).

## Le tre proprietà strutturali che guidano gli algoritmi

### 1. Cut property (greedy ottimo per MST)
Per ogni taglio $(S, V\setminus S)$, l'arco di peso minimo che lo attraversa è in qualche MST. Da qui correttezza di Prim, Kruskal, e Borůvka. Generalizza il **principio greedy "stays ahead"** ([[Interval Scheduling]]).

### 2. Submodularità
Funzioni $f: 2^V \to \mathbb{R}$ con rendimento marginale decrescente: $f(S \cup \{v\}) - f(S) \geq f(T \cup \{v\}) - f(T)$ per $S \subseteq T$. Greedy garantisce $(1 - 1/e)$ approssimazione (vertex cover, max coverage).

### 3. Triangolare / disuguaglianza di consistenza
$h(n) \leq c(n, n') + h(n')$ è la disuguaglianza triangolare adattata: garantisce che A\* non ri-espanda nodi. È analoga al **bilancio dettagliato** in catene di Markov, alla **monotonia** in lattici.

## Connessioni con altri argomenti trasversali

- **[[SVD e decomposizione spettrale]]**: spectral graph theory — autovalori del Laplaciano $L = D - A$ codificano connettività (algebraic connectivity $\lambda_2$), bottleneck (Cheeger), embedding (Laplacian Eigenmaps). PageRank è autovalore principale di matrice di transizione.
- **[[Catene di Markov e MCMC]]**: ogni catena è un grafo pesato; mixing time = secondo autovalore del Laplaciano normalizzato.
- **[[Reti neurali]]**: grafo computazionale di backprop. GNN come BFS-pesato.
- **[[Ottimizzazione iterativa]]**: shortest path come problema di programmazione dinamica (Bellman); MST come problema di matroidi.
- **[[Probabilità bayesiana e inferenza]]**: reti bayesiane sono DAG con CPT; inferenza esatta = sum-product su tree (clique tree).

## Punti di attenzione (errori comuni)

1. **Dijkstra fallisce con pesi negativi.** Non è "lento", è *scorretto*. Bellman-Ford è la sostituzione corretta.
2. **A\* con euristica non ammissibile non è ottimale.** Può tagliare cammini ottimi.
3. **BFS non funziona per shortest path pesato.** Solo per non pesato (o pesi unitari).
4. **MST non è unico.** Con pesi distinti sì; con pesi ripetuti no, ma il *peso totale* è unico.
5. **DFS non dà shortest path.** Esplora in profondità: i percorsi trovati possono essere arbitrariamente lunghi.
6. **Topologico richiede DAG.** Su grafo con cicli, non esiste.

## Pagine collegate

- Concetto centrale: [[Grafo]]
- Visita: [[BFS e DFS]]
- Shortest path: [[Algoritmo di Dijkstra]], [[Algoritmo di Bellman-Ford]], [[Ricerca A*]]
- MST: [[Minimum Spanning Tree]], [[Algoritmo di Prim]], [[Algoritmo di Kruskal]]
- Greedy / DP: [[Algoritmo greedy]], [[Algoritmo di Huffman]], [[Interval Scheduling]], [[Weighted Interval Scheduling]]
- Bipartito: [[Stable Matching]]
- Complessità: [[NP-completezza]], [[Macchina di Turing]]
- AI: [[Agente intelligente]], [[Concatenazione in avanti e all'indietro]], [[Risoluzione (RES)]]
- ML: [[Grafo computazionale]], [[Backpropagation]]
- Stocastico: [[Catena di Markov]], [[Passeggiata aleatoria]]

## Fonti aggregate

- [[Dispense TecProg — Galletti]] (§6 — definizioni, BFS/DFS, Dijkstra, MST)
- [[Dispense Algoritmi — Galletti]] (greedy, DP, NP-completezza)
- [[Dispense FondAI — Galletti]] (§2 — ricerca A*; §4-§7 — logica come grafo)
- [[Dispense Machine Learning — Galletti]] (§5.5 — grafo computazionale)
- [[Dispense Processi Stocastici — Galletti]] (§3 — catene su grafi)
