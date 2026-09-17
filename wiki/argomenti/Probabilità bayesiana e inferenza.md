---
tipo: argomento
titolo: Probabilità bayesiana e inferenza
tag: [trasversale, bayesiano, inferenza, ml, statistica]
cluster: trasversale
corsi: [Probabilità e Statistica, Matematica per il Machine Learning, Modelli Matematici per la Fisica II, Informatica per il Machine Learning, Machine Learning]
ultima-modifica: 2026-05-06
---

# Probabilità bayesiana e inferenza

Argomento trasversale che attraversa **5 corsi**. Il [[Formula di Bayes|teorema di Bayes]] è una formula breve, ma incarna un cambio di paradigma profondo: i parametri sono variabili aleatorie, non costanti incognite. Cinque corsi raccontano cinque pezzi della stessa storia: il framework formale, l'algoritmica, l'applicazione fisica, il pre-training neurale, e la regolarizzazione implicita.

## Il nucleo unificante

Tre densità + una formula:

$$
\underbrace{g(\theta\mid\tau)}_{\text{posterior}} = \frac{\overbrace{g(\tau\mid\theta)}^{\text{likelihood}} \cdot \overbrace{g(\theta)}^{\text{prior}}}{\underbrace{g(\tau)}_{\text{evidence}}}
$$

Quattro modi di "usare" la posterior:

| Uso | Cosa restituisce | Costo computazionale |
|---|---|---|
| **[[Stima MAP]]** | un punto $\bar\theta = \arg\max g(\theta\mid\tau)$ | ottimizzazione |
| **Predittiva bayesiana** | $g_\tau(x) = \int g(x\mid\theta)g(\theta\mid\tau)d\theta$ | integrale (spesso MCMC) |
| **[[Intervalli di credibilità]]** | regione $C$ con $\mathbb{P}(\theta\in C\mid\tau) = 0.95$ | quantili della posterior |
| **Marginal likelihood** | $g(\tau)$ per model selection | integrale (Laplace, [[BIC]]) |

Ogni corso privilegia uno o più di questi usi.

## Il tour dei corsi

### [[Probabilità e Statistica]] — la base
Introduce [[Probabilità condizionata]] e il teorema di Bayes nella forma elementare. Esempi tipici: test medici (false positive rate, valore predittivo positivo), ragionamento sotto incertezza. Il prior è ancora "soggettivo"; non si parla ancora di learning.

### [[Matematica per il Machine Learning]] — la teoria completa
Trattamento più sistematico dell'intero framework:

- **[[Apprendimento Bayesiano]]**: paradigma alternativo al frequentista (MLE).
- **[[Distribuzioni coniugate]]**: prior scelti per chiusura analitica (Beta-Binomiale, Normale-Inverse Gamma, Dirichlet-Multinomiale).
- **[[Stima MAP]]**: $\bar\theta = \arg\max[g(\tau\mid\theta) g(\theta)]$ — **MLE + termine di regolarizzazione** $\log g(\theta)$.
- **Convergenza a MLE**: per $n\to\infty$, $\bar\theta_n \to \hat\theta_{ML}$ (il prior diventa trascurabile).
- **Approssimazione di Laplace → [[BIC]]**: espansione al secondo ordine intorno a $\bar\theta_n$.
- **Aggiornamento iterativo** $w_t \propto w_{t-1} \cdot g(\tau\mid\theta)$: catena di Markov sullo spazio delle densità che converge a $\delta(\theta - \hat\theta_{ML})$ — connessione con [[Catene di Markov e MCMC]].
- **Rischio = [[Divergenza di Kullback-Leibler]]**: $\ell(g) = D_{KL}(f \| \int g(\cdot\mid\theta)w(\theta)d\theta) + c$.

### [[Modelli Matematici per la Fisica II]] — la prospettiva fisica
Connessione profonda con la **fisica statistica**:

- **[[Principio di massima entropia]]**: il prior "meno informativo" possibile è quello a entropia massima, sotto vincoli di momenti noti.
- **Distribuzione di Boltzmann-Gibbs** $P(\sigma) \propto e^{-\beta H(\sigma)}/Z$ è la posterior bayesiana implicita di un modello con prior MaxEnt e $\beta$ come iperparametro.
- La normalizzazione $Z(\beta)$ in fisica = evidenza $g(\tau)$ in stat.
- **Energia libera = log-evidenza con segno**: $-\log Z = $ negative log-likelihood marginale.
- Lega a [[Modello di Ising]] e [[Modello di Curie-Weiss e Hopfield]]: l'inferenza su spin-config è un problema bayesiano in alta dimensione.

### [[Informatica per il Machine Learning]] — l'ottica neurale
La struttura bayesiana è **implicita** nelle reti, ma riconoscibile:

- **[[Language Model]]**: probabilità $P(w_t \mid w_{<t})$ — è una posterior condizionata. Smoothing (Kneser-Ney, add-$\alpha$) è prior bayesiano sui n-gram.
- **[[Dropout]] come Bayesian inference**: training con dropout ≈ approssimazione variazionale di una rete bayesiana (Gal & Ghahramani 2016).
- **Pre-training + fine-tuning** ([[BERT]]): il pretraining costruisce un *prior* sui pesi; il fine-tuning è MAP con quel prior.
- **Negative sampling** in Word2Vec ottimizza una verosimiglianza con prior implicito uniforme sul vocabolario.

### [[Machine Learning]] — la regolarizzazione come MAP
Cardinale punto di incontro:

- **Ridge regression** è MAP con prior gaussiano: $\beta\sim N(0, \lambda^{-1}I)$ → $\arg\max[\text{NLL} - \lambda\|\beta\|^2]$.
- **[[Regolarizzazione di Tikhonov]] = MAP gaussiano** (vedi argomento futuro [[Regolarizzazione]]).
- **Lasso** = MAP con prior Laplace: $\beta\sim \text{Laplace}(0, \lambda^{-1})$ → $\arg\max[\text{NLL} - \lambda\|\beta\|_1]$.
- **Cross-validation** stima la stessa quantità che BIC approssima analiticamente.

## La gerarchia degli stimatori

| Stimatore | Formula | Quando usarlo |
|---|---|---|
| **MLE** | $\arg\max_\theta g(\tau\mid\theta)$ | $n$ grande, no info a priori |
| **MAP** | $\arg\max_\theta g(\tau\mid\theta) g(\theta)$ | regolarizzazione, $n$ piccolo |
| **Bayes posteriore** | $E[\theta\mid\tau]$ | quantifico incertezza |
| **Bayes predittivo** | $\int g(x\mid\theta)g(\theta\mid\tau)d\theta$ | predizione robusta |
| **Empirical Bayes** | stima il prior dai dati | gerarchico, dati grandi |

**Insight**: MLE e MAP sono "punti", mentre il Bayes completo è una distribuzione. Tutto il valore aggiunto del bayesiano sta nel "non collassare" la posterior in un punto.

## I cinque ruoli del prior

1. **Regolarizzatore** (ML, MetNum): prior gaussiano = ridge, Laplace = Lasso.
2. **Informazione esperta** (statistica medica, ProbStat): incorpora prevalenza nota, costi clinici.
3. **Coniugato** (MatML): scelto per chiusura analitica, anche se non riflette credenze reali.
4. **Massima entropia** (MMFII): minimo bias dato un vincolo di momento.
5. **Pretraining** (InfML): peso pre-trainato su dati massivi → prior implicito su pesi della rete fine-tuned.

## Tre teoremi che attraversano i corsi

### 1. Teorema di Bernstein-von Mises
Sotto regolarità + likelihood identificabile, per $n\to\infty$:
$$
g(\theta\mid\tau) \approx N\bigl(\hat\theta_{ML}, \tfrac{1}{n}I^{-1}(\hat\theta_{ML})\bigr)
$$
La posterior diventa gaussiana centrata in MLE con varianza inversa di Fisher. Conseguenze:
- giustifica intervalli di credibilità asintotici.
- la scelta del prior non importa per $n$ grande.
- dà il [[BIC]] tramite Laplace.

### 2. Teorema di Bayes ricorsivo
$$
g(\theta\mid\tau_{1:t}) \propto g(\tau_t\mid\theta) \cdot g(\theta\mid\tau_{1:t-1})
$$
Aggiornamento incrementale: la posterior di ieri diventa il prior di oggi. È la base di filtri Kalman, particle filter, online learning.

### 3. Identità della log-evidenza (ELBO)
$$
\log g(\tau) = E_q[\log g(\tau,\theta) - \log q(\theta)] + D_{KL}(q\|g(\cdot\mid\tau))
$$
Il primo termine è l'**ELBO**, il secondo è $\geq 0$. Da qui l'inferenza variazionale: massimizzare ELBO = minimizzare KL alla posterior. Lega a [[Disuguaglianza di Jensen]] e [[Divergenza di Kullback-Leibler]].

## Connessioni con altri argomenti trasversali

- **[[Catene di Markov e MCMC]]**: ogni volta che la posterior è intrattabile, MCMC è la via maestra. Metropolis-Hastings non richiede $g(\tau)$.
- **[[SVD e decomposizione spettrale]]**: nel modello lineare normale, la varianza della posterior è $\sigma^2 (X^\top X + \lambda I)^{-1}$ — gli autovalori di $X^\top X$ controllano l'incertezza nelle PC. Ridge "sposta" gli autovalori.
- **[[Ottimizzazione iterativa]]**: MAP è ottimizzazione del log-posterior. Variational inference è ottimizzazione di ELBO.
- **[[Reti neurali]]**: dropout, weight decay, e early stopping sono regolarizzatori che corrispondono a vari prior. La rete bayesiana esplicita esiste ma è costosa.

## Punti di attenzione (errori comuni)

1. **Bayes ≠ "il prior conta sempre"**. Per $n$ grande il prior è trascurato (BvM).
2. **MAP non è la media bayesiana**. La media è $E[\theta\mid\tau]$, la moda è MAP. Coincidono solo per posterior simmetrica.
3. **L'evidenza dipende dal modello**, non solo dai dati. Confronto bayesiano di modelli usa $g(\tau\mid M)$.
4. **Coniugato è comodo, non corretto**. Beta su una proporzione è un prior; non riflette necessariamente il fenomeno.
5. **MCMC dà approssimazione, non l'esatto**. La qualità dipende da burn-in e mixing time.

## Pagine collegate

- Concetti centrali: [[Apprendimento Bayesiano]], [[Formula di Bayes]], [[Stima MAP]], [[Intervalli di credibilità]]
- Stima puntuale frequentista: [[Stima di Massima Verosimiglianza]]
- Prior: [[Distribuzioni coniugate]], [[Principio di massima entropia]]
- Approssimazioni: [[BIC]], [[Disuguaglianza di Jensen]]
- Algoritmico: [[Metropolis-Hastings]], [[Campionamento di Gibbs]], [[Catena di Markov]]
- Misura: [[Divergenza di Kullback-Leibler]]
- Applicazioni: [[Regolarizzazione di Tikhonov]], [[Lasso e Elastic Net]], [[Dropout]]
- Modelli: [[Modello lineare normale]], [[Language Model]]

## Fonti aggregate

- [[Dispense MatML — Galletti]] (§2.10-2.11 — framework completo, MAP, BIC)
- [[Dispense ProbStat — Galletti]] (§2 — Bayes elementare)
- [[Dispense MMFII — Galletti]] (§3-4 — MaxEnt, Boltzmann-Gibbs)
- [[Dispense InfML — Galletti]] (§3-§5 — language models, dropout, BERT)
- [[Dispense Machine Learning — Galletti]] (§3 — Tikhonov come MAP)
