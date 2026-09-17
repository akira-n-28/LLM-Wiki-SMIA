---
tipo: argomento
titolo: Reti neurali
tag: [trasversale, deep-learning, ml, ottimizzazione, fisica-statistica]
cluster: trasversale
corsi: [Machine Learning, Informatica per il Machine Learning, Ottimizzazione, Modelli Matematici per la Fisica II]
ultima-modifica: 2026-05-06
---

# Reti neurali

Argomento trasversale che attraversa **4 corsi**. Le reti neurali nascono come modello di neurone ([[Algoritmo del percettrone]] in [[Ottimizzazione]]), maturano come architetture profonde feedforward in [[Machine Learning]], si specializzano per dati strutturati (sequenze, immagini, grafi) in [[Informatica per il Machine Learning]], e ricomparire come sistemi dinamici a memoria associativa in [[Modelli Matematici per la Fisica II]].

## Il nucleo unificante

Una rete neurale è una composizione $g_\Theta = f_n \circ f_{n-1} \circ \cdots \circ f_1$ di trasformazioni parametrizzate alternate a non linearità. Tre domande fondamentali in ogni corso:

1. **Cosa può rappresentare?** → espressività ([[Teorema di approssimazione universale]])
2. **Come la addestro?** → ottimizzazione ([[Discesa del gradiente]] + [[Backpropagation]])
3. **Generalizza?** → controllo della varianza ([[Regolarizzazione di Tikhonov]], [[Dropout]], [[Bias-Variance trade-off]])

## Il tour dei corsi

### [[Ottimizzazione]] — la radice storica
**[[Algoritmo del percettrone]]** (Rosenblatt, 1958): un singolo neurone $f(x) = \mathrm{sign}(w^\top x + b)$ con regola di update $w_{t+1} = w_t + y_i x_i$ se misclassificato. Il **teorema di convergenza del percettrone** garantisce convergenza in $O(R^2/\gamma^2)$ iterazioni se i dati sono linearmente separabili con margine $\gamma$. È l'unico corso che tratta la rete neurale come problema di ottimizzazione *non differenziabile* (segno) — limite essenziale che motiva il passaggio alle attivazioni differenziabili.

### [[Machine Learning]] — la teoria feedforward
**[[Multi-Layer Perceptron]]** generalizza il percettrone con attivazioni differenziabili (sigmoide, ReLU). Tre risultati chiave:

- **[[Teorema di approssimazione universale]]** (Cybenko, Hornik): MLP con un solo hidden layer sufficientemente largo approssima qualsiasi funzione continua su un compatto. Spiega *perché* le reti funzionano in linea di principio.
- **[[Backpropagation]]**: calcolo del gradiente $\partial L / \partial \Theta$ in tempo lineare nella dimensione della rete. È regola della catena applicata sistematicamente sul [[Grafo computazionale]].
- **Loss e attivazioni si accoppiano**: MSE + lineare per regressione, [[Cross-entropy]] + softmax per classificazione, BCE + sigmoide per multi-label.

### [[Informatica per il Machine Learning]] — le architetture moderne
Tre estensioni dell'MLP per dati strutturati:

| Architettura | Struttura sfruttata | Idea chiave |
|---|---|---|
| [[Convolutional Neural Network]] | invarianza traslazionale (immagini) | filtri condivisi, pooling, gerarchia di feature |
| [[Recurrent Neural Network]], [[LSTM]], [[GRU]] | sequenzialità (testo, time series) | parameter sharing nel tempo, gate per memoria |
| [[Transformer]] | dipendenze a lungo raggio | attention $\mathrm{softmax}(QK^\top/\sqrt{d_k})V$, parallelizzazione |

Trattamento approfondito di:
- **Vanishing/exploding gradient** in RNN profonde → motivazione di LSTM (gate forget/input/output) e [[Residual Connection]] (ResNet).
- **[[Backpropagation]] through time** (BPTT): backprop su sequenze srotolate.
- **Pretraining + fine-tuning** ([[BERT]]): MLM e NSP come task auto-supervisionati.
- **[[Word Embedding]]** come strato di look-up: la prima rete di milioni di parametri.
- **[[Dropout]]**: regolarizzazione tramite ensemble implicito; equivalente a un prior gaussiano sui pesi.

### [[Modelli Matematici per la Fisica II]] — la rete come sistema dinamico
**[[Modello di Curie-Weiss e Hopfield]]**: rete a $N$ neuroni binari $\sigma_i \in \{-1,+1\}$ con dinamica di flip locale. La funzione di energia $H = -\frac{1}{2}\sum_{ij} J_{ij}\sigma_i\sigma_j - h\sum_i \sigma_i$ è il duale dell'MLP energy-based. Risultati:
- **Memoria associativa**: pesi $J_{ij}$ codificano pattern; la dinamica di Glauber rilassa allo stato più vicino.
- **Capacità $\alpha_c \approx 0.14 N$** pattern memorizzabili senza interferenza.
- **Transizione di fase a $T_c$** — analoga al modello di Ising.

È una rete *ricorrente, energy-based, simmetrica*: niente backprop, l'apprendimento è la regola di Hebb $J_{ij} \propto \sum_\mu \xi_i^\mu \xi_j^\mu$.

## Le tre prospettive matematiche

| Prospettiva | Visione | Punto di partenza |
|---|---|---|
| **Funzionale** (ML) | $g_\Theta: \mathbb{R}^d \to \mathbb{R}^q$ approssima una funzione | teorema universale |
| **Ottimizzazione** (Ott) | minimizzo $L(\Theta) = \frac{1}{n}\sum \ell(y_i, g_\Theta(x_i))$ | landscape, convessità, GD |
| **Sistema dinamico** (MMFII) | $\sigma(t+1) = \mathrm{sign}(J\sigma(t))$ converge a punti fissi | energia, attrattori |

Le tre sono coerenti: il punto fisso di una rete energy-based corrisponde al minimizzatore di un MLP feedforward con la stessa architettura simmetrica. La differenza è dove si "spende" la complessità — funzione, parametri, o stati.

## Backpropagation: l'idea che unifica tutto

Vista dal [[Grafo computazionale]], la backprop è solo regola della catena con riuso intelligente. La sua portata cross-corso è enorme:

- È **l'algoritmo che rende fattibile** ogni rete moderna (ML, InfML).
- Calcola gradienti che alimentano [[Stochastic Gradient Descent|SGD]] (Ott) e Adam.
- Si estende a parametrizzazioni non standard (BPTT per RNN, attention per Transformer).
- Non si applica a sistemi non differenziabili (Hopfield), motivo per cui MMFII tratta apprendimento Hebbiano.
- La **memoria** è $O(\text{dim della rete})$ in forward; può essere ridotta con gradient checkpointing.

## Tre fenomeni che attraversano i corsi

### 1. Vanishing/exploding gradient
**Sintomo:** in reti profonde, il gradiente decade o esplode esponenzialmente con la profondità.
- ML lo accenna come motivo per cui gli MLP profondi sono difficili da addestrare.
- InfML lo formalizza: in RNN, $\partial L / \partial \Theta_t \sim \prod_{s=t}^T W^\top \mathrm{diag}(\sigma'(\cdot))$, prodotto che esplode/svanisce con $T$.
- **Soluzioni**: LSTM/GRU (gate impediscono il decay), [[Residual Connection]] ($x \mapsto x + f(x)$ rende l'identità l'inizializzazione), normalizzazione (batch norm, layer norm).

### 2. Overparametrizzazione e generalizzazione
**Domanda:** perché reti con più parametri che dati non overfittano?
- ML: [[Bias-Variance trade-off]] classico predice overfitting, ma osservazione empirica contraria.
- InfML: la *implicit regularization* di SGD trova soluzioni di norma minima (in spirito ridge).
- Ott: il landscape di una rete profonda è non convesso ma con molti minimi globali approssimativi (paesaggio "benigno").
- MMFII: connessione con la teoria delle vetri di spin — il numero di stati metastabili scala in modo controllato.

### 3. Regolarizzazione
Tutte e quattro le materie offrono una declinazione (vedi anche argomento [[Regolarizzazione]] futuro):
- **L2/Tikhonov** (ML, MetNum): penalty $\lambda\|\Theta\|^2$ → equivalente a prior gaussiano (MAP).
- **L1/Lasso** (InfML): induce sparsità.
- **[[Dropout]]** (InfML): ensemble implicito di sotto-reti.
- **Early stopping**: regolarizzazione implicita via training dinamics.

## Connessioni con altri argomenti trasversali

- **[[SVD e decomposizione spettrale]]**: il calcolo di Hessiana e curvature in reti profonde richiede analisi spettrale; LoRA fattorizza pesi via SVD; PCA sui hidden states diagnostica feature collapse.
- **Catene di Markov**: la dinamica di Glauber su Hopfield è una catena di Markov; SGD può essere visto come catena con stazionaria $e^{-L/T}$ (Langevin).
- **Ottimizzazione iterativa** (futuro): SGD è il caso stocastico di [[Discesa del gradiente]]; Adam aggiunge momentum + scaling per coordinate.

## Punti di attenzione (errori comuni)

1. **MLP universale ≠ MLP addestrabile.** Cybenko garantisce esistenza, non che SGD la trovi.
2. **Backprop è esatto, non approssimato.** A differenza di MCMC, non c'è bias se non per arrotondamenti FP.
3. **Hopfield non è un MLP rovesciato.** Sono due famiglie diverse: feedforward (acyclic, differenziabile) vs energy-based (cyclic, simmetrico, discreto).
4. **Attention ≠ recurrence.** Il Transformer non condivide pesi nel tempo come l'RNN; condivide pesi *tra le posizioni* via stesso $W_Q, W_K, W_V$.

## Pagine collegate

- Concetti centrali: [[Multi-Layer Perceptron]], [[Backpropagation]], [[Grafo computazionale]]
- Espressività: [[Teorema di approssimazione universale]]
- Architetture: [[Convolutional Neural Network]], [[Recurrent Neural Network]], [[LSTM]], [[GRU]], [[Transformer]], [[BERT]], [[Residual Connection]]
- Ottimizzazione: [[Discesa del gradiente]], [[Stochastic Gradient Descent]], [[Algoritmo del percettrone]]
- Loss: [[Cross-entropy]], [[Softmax]]
- Regolarizzazione: [[Regolarizzazione di Tikhonov]], [[Dropout]], [[Lasso e Elastic Net]]
- Fisica statistica: [[Modello di Curie-Weiss e Hopfield]], [[Modello di Ising]]
- Embedding: [[Word Embedding]], [[Meccanismo di Attention]]

## Fonti aggregate

- [[Dispense Machine Learning — Galletti]] (§5 — MLP, backprop)
- [[Dispense InfML — Galletti]] (§4-§7 — RNN, LSTM, Transformer, BERT, CNN, ResNet)
- [[Dispense Ottimizzazione — Galletti]] (§5.6 — percettrone)
- [[Dispense MMFII — Galletti]] (§6 — Curie-Weiss, Hopfield)
