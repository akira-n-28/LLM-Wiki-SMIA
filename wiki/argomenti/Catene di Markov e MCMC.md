---
tipo: argomento
titolo: Catene di Markov e MCMC
tag: [trasversale, probabilità, processi-stocastici, mcmc, fisica-statistica]
cluster: trasversale
corsi: [Probabilità e Statistica, Processi Stocastici, Matematica per il Machine Learning, Modelli Matematici per la Fisica II]
ultima-modifica: 2026-05-06
---

# Catene di Markov e MCMC

Argomento trasversale che attraversa **4 corsi**. La proprietà markoviana — il futuro dipende solo dal presente — è insegnata in tre forme parallele (discreta-finita, discreta-continua, tempo continuo) e usata in quattro modi diversi (asintotica, simulazione, ottimizzazione, fisica statistica).

## Il nucleo unificante

Una catena di Markov è un processo stocastico $\{X_t\}$ tale che

$$
\mathbb{P}(X_{t+1} = y \mid X_t = x, X_{t-1}, \ldots, X_0) = \mathbb{P}(X_{t+1} = y \mid X_t = x)
$$

L'**oggetto matematico fondamentale** è la matrice (o nucleo) di transizione $P$. Tre teoremi reggono tutta la teoria:

1. **Esistenza della stazionaria**: $\pi P = \pi$ — autovettore sinistro di $P$ con autovalore 1.
2. **Teorema ergodico** (irriducibile + aperiodica + ricorrente positiva): convergenza $P(X_n=j \mid X_0=i) \to \pi_j$ per ogni $i$.
3. **Bilancio dettagliato sufficiente** ma non necessario: $\pi(x) p(y|x) = \pi(y) p(x|y) \Rightarrow \pi$ stazionaria.

Il bilancio dettagliato è il vero "trucco di design": permette di **costruire una catena** la cui stazionaria è esattamente la distribuzione $\pi$ desiderata, anche se $\pi$ è nota solo a meno di una costante.

## Il tour dei corsi

### [[Probabilità e Statistica]] — la base discreta finita
Introduce le catene di Markov a stati finiti come applicazione della [[Probabilità condizionata]]. Esempi tipici: random walk simmetrico su $\mathbb{Z}$, catena ergodica $2\times 2$, classificazione di stati. Il livello rimane discreto e calcolatorio.

### [[Processi Stocastici]] — la teoria formale
Sviluppo rigoroso:
- **Spazio di stati discreto, tempo discreto**: matrice stocastica $P$, classi comunicanti, ricorrenza vs transienza, periodo, [[Teorema ergodico]] — distribuzione stazionaria come $1/\mu_j(j)$ (tempo medio di ritorno).
- **Tempo continuo**: [[Generatore infinitesimale]] $Q$, equazioni di Kolmogorov $P'(t) = P(t)Q$, soluzione $P(t) = e^{Qt}$. I [[Processo di nascita e morte|processi di nascita e morte]] sono il caso prototipo.
- **Equazione di Chapman-Kolmogorov** $P_{t+s} = P_t P_s$ — semigruppo.
- Connessione con la [[Passeggiata aleatoria]] e la [[Funzione generatrice delle probabilità]].

### [[Matematica per il Machine Learning]] — MCMC come algoritmo
Inverte la prospettiva: invece di studiare una catena data, **costruire una catena per simulare** una distribuzione $f$ intrattabile. Il programma:

- **[[Metropolis-Hastings]]**: catena costruita su una proposta $q(y|x)$, accettazione $\alpha = \min(1, \frac{f(y) q(x|y)}{f(x) q(y|x)})$. Soddisfa il bilancio dettagliato per costruzione.
- **[[Campionamento di Gibbs]]**: caso speciale per distribuzioni multivariate, aggiorna una coordinata alla volta dalle condizionali piene. Tasso di accettazione 1.
- **Burn-in e correlazione**: i campioni MCMC sono dipendenti, a differenza di [[Metodo accept-reject]].
- Lo spazio di stati è ora $\mathbb{R}^d$ (continuo): la "matrice" diventa nucleo di transizione.

### [[Modelli Matematici per la Fisica II]] — fisica statistica
La distribuzione di Boltzmann-Gibbs $P(\sigma) \propto e^{-\beta H(\sigma)}$ è la stazionaria della catena Metropolis costruita su flip di spin. Lega:
- **[[Modello di Ising]]** — Metropolis su $\{-1,+1\}^N$ simula equilibrio termico, transizione di fase a $T_c$.
- **[[Modello di Curie-Weiss e Hopfield]]** — campo medio, dinamica di rilassamento.
- **[[Principio di massima entropia]]** — la stazionaria $e^{-\beta H}/Z$ è la massima entropia con vincolo sull'energia media.

## Le quattro applicazioni

### 1. Asintotica pura
**Domanda:** dove finisce il sistema dopo molto tempo?
**Risposta:** $\pi$, l'unica stazionaria (se ergodica).
**Esempi:** PageRank, classificazione di stati di un sistema biologico/economico, mixing time.

### 2. Inferenza Bayesiana via MCMC
**Domanda:** come campiono dalla posteriori $f(\theta|\tau) \propto g(\tau|\theta) g(\theta)$?
**Risposta:** Metropolis-Hastings con target $f(\theta|\tau)$ — non serve normalizzare.
**Trucco chiave:** $\alpha = \min\bigl(1, \frac{g(\tau|\theta')\, g(\theta')\, q(\theta|\theta')}{g(\tau|\theta)\, g(\theta)\, q(\theta'|\theta)}\bigr)$ — la costante di normalizzazione si cancella.

### 3. Ottimizzazione globale ([[Simulated Annealing]])
**Domanda:** come trovo il minimo globale di $H$ (multi-modale)?
**Risposta:** catena Metropolis con target $e^{-\beta H}$ e $\beta$ crescente nel tempo (cooling schedule). Per $\beta\to\infty$ la stazionaria si concentra sui minimi globali.
**Connessione:** è MCMC con target che dipende dal tempo.

### 4. Fisica statistica (equilibrio termico)
**Domanda:** quanto vale $\langle m \rangle = \langle f(\sigma)\rangle_{\text{Boltzmann}}$?
**Risposta:** media temporale $(1/K)\sum_k f(\sigma^{(k)})$ con $\sigma^{(k)}$ generata da Metropolis. È un'applicazione di Monte Carlo via MCMC.

## Tabella delle equivalenze

| Punto di vista | Spazio di stati | Tempo | Target | Strumento principale |
|---|---|---|---|---|
| Processi finiti | finito | discreto | dato dalla catena | matrice stocastica $P$ |
| Processi continui | finito o numerabile | continuo | dato | generatore $Q$ |
| MCMC Bayesiano | $\mathbb{R}^d$ | discreto | $f(\theta\mid\tau)$ | Metropolis-Hastings |
| Simulated Annealing | $\{0,1\}^n$ o $\mathbb{R}^n$ | discreto | $e^{-\beta(t) H}$ | Metropolis con cooling |
| Fisica statistica | configurazioni | discreto | Boltzmann-Gibbs | Metropolis su flip |

## Connessioni nascoste

- **Stazionaria = autovettore.** La distribuzione stazionaria $\pi$ è l'autovettore sinistro di $P$ associato a $\lambda=1$. Il **secondo autovalore** $\lambda_2$ controlla il *mixing time*: quanto velocemente la catena converge. Lega a [[Autovalori e autovettori]] e quindi all'argomento [[SVD e decomposizione spettrale]].

- **Bilancio dettagliato = simmetria di trasformazione.** È esattamente la condizione di **reversibilità temporale** in fisica: la catena reversibile non distingue passato da futuro all'equilibrio.

- **MCMC ↔ approssimazione stocastica.** Entrambe sono dinamiche stocastiche con limite deterministico. La [[Approssimazione stocastica]] (Robbins-Monro) e MCMC sono "cugini": l'una stima un punto fisso, l'altra una distribuzione di equilibrio.

- **Update Bayesiano = catena sullo spazio delle densità.** Nel framework di [[Apprendimento Bayesiano]], il ciclo $w_t \propto w_{t-1} \cdot g(\tau\mid\theta)$ è una catena di Markov sullo spazio delle distribuzioni. La stazionaria è $\delta(\theta - \hat\theta_{ML})$.

## Punti di attenzione (errori comuni)

1. **Stazionarietà ≠ ergodicità.** Esistono catene con più stazionarie (riducibili) o periodiche; lì il limite di $P^n$ non esiste indipendentemente da $X_0$.
2. **Bilancio dettagliato non è necessario.** Una catena può essere ergodica senza essere reversibile. È solo un *modo conveniente* di garantire che $\pi$ sia stazionaria.
3. **MCMC ≠ campioni i.i.d.** I campioni sono correlati; le stime di varianza richiedono autocorrelation time.
4. **Burn-in non è universale.** Convergenza esponenziale, ma il tasso dipende dal mixing time.

## Pagine collegate

- Concetto centrale: [[Catena di Markov]]
- Generalizzazione tempo continuo: [[Generatore infinitesimale]], [[Processo di nascita e morte]]
- Algoritmi MCMC: [[Metropolis-Hastings]], [[Campionamento di Gibbs]]
- Proprietà: [[Bilancio dettagliato]]
- Framework: [[Metodi Monte Carlo]], [[Apprendimento Bayesiano]]
- Ottimizzazione: [[Simulated Annealing]], [[Approssimazione stocastica]]
- Fisica: [[Modello di Ising]], [[Principio di massima entropia]]
- Random walk: [[Passeggiata aleatoria]], [[Funzione generatrice delle probabilità]]

## Fonti aggregate

- [[Dispense Processi Stocastici — Galletti]] (§3, §5 — teoria formale)
- [[Dispense MatML — Galletti]] (§3.6-3.9 — MCMC)
- [[Dispense ProbStat — Galletti]] (esempi finiti)
- [[Dispense MMFII — Galletti]] (§4-5 — Ising, MaxEnt)
