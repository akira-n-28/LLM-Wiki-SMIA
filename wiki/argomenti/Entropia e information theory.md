---
tipo: argomento
titolo: Entropia e information theory
tag: [trasversale, teoria-informazione, fisica-statistica, ml, statistica]
cluster: trasversale
corsi: [Modelli Matematici per la Fisica II, Matematica per il Machine Learning, Machine Learning, Informatica per il Machine Learning, Probabilità e Statistica]
ultima-modifica: 2026-05-06
---

# Entropia e information theory

Argomento trasversale che attraversa **5 corsi**. Una sola idea — quantificare l'incertezza/informazione di una distribuzione — genera quattro oggetti collegati (entropia di Shannon, divergenza KL, cross-entropy, mutual information) che ricompaiono in fisica statistica, inferenza bayesiana, classificazione neurale, language modeling e riduzione di dimensionalità.

## Il nucleo unificante

Quattro funzionali, una sola origine logaritmica:

| Quantità | Formula | Interpretazione |
|---|---|---|
| **Entropia** $H(P)$ | $-\sum_x p(x)\log p(x)$ | incertezza media di $P$ |
| **Cross-entropy** $H(P,Q)$ | $-\sum_x p(x)\log q(x)$ | costo di codificare $P$ con codice ottimale per $Q$ |
| **KL divergence** $D_{KL}(P\|Q)$ | $\sum_x p(x)\log\frac{p(x)}{q(x)}$ | bit "sprecati" usando $Q$ invece di $P$ |
| **Mutual information** $I(X;Y)$ | $D_{KL}(P_{XY} \| P_X P_Y)$ | quanta informazione $X$ porta su $Y$ |

L'identità centrale che lega tutto:

$$
\boxed{\ H(P, Q) = H(P) + D_{KL}(P\|Q)\ }
$$

Da qui:
- minimizzare $H(P,Q)$ rispetto a $Q$ (con $P$ fissa) ≡ minimizzare $D_{KL}(P\|Q)$;
- $H(P,Q) \geq H(P)$ con uguaglianza sse $P=Q$ (Gibbs).

**[[Disuguaglianza di Jensen]]** applicata a $-\log$ è la madre di tutte le proprietà ($D_{KL}\geq 0$, $H \leq \log|\mathcal{X}|$, ELBO).

## Il tour dei corsi

### [[Modelli Matematici per la Fisica II]] — l'origine fisica
Punto di partenza più rigoroso. Tre risultati:

- **[[Entropia di Shannon]]** $H(X) = -\sum p_i \log_2 p_i$ — Shannon (1948), assiomatizzazione dell'unica funzione che misura "sorpresa" con additività su eventi indipendenti.
- **[[Principio di massima entropia]]** (Jaynes 1957): tra tutte le distribuzioni compatibili con vincoli noti (momenti $E[f_k(X)] = c_k$), quella di massima entropia è $p(x) \propto e^{-\sum_k \lambda_k f_k(x)}$. Caso classico: vincolo solo sull'energia media → distribuzione di Boltzmann-Gibbs $p(x) \propto e^{-\beta H(x)}$.
- **Energia libera = log-evidenza con segno**: $F = -\frac{1}{\beta}\log Z$. Variazione di $F$ ↔ KL alla distribuzione di equilibrio.

Il legame tra termodinamica, MaxEnt e inferenza è il **fondamento epistemologico** dell'intera information theory.

### [[Matematica per il Machine Learning]] — la divergenza come rischio
La KL appare come **rischio teorico naturale** in apprendimento:

- Loss logaritmica → rischio = $D_{KL}(f \| g(\cdot\mid\theta)) + \text{const}$ (con $f$ vera, $g$ modello).
- **MLE = minimizzazione KL empirica**: $\hat\theta_{ML} = \arg\min D_{KL}(\hat f_n \| g(\cdot\mid\theta))$ con $\hat f_n$ empirica.
- **[[BIC]]**: derivato espandendo log-evidenza al II ordine; il termine $\frac{d}{2}\log n$ penalizza modelli complessi (rasoio di Occam).
- **Bound di Cramér** ([[Teoria delle grandi deviazioni]]): $\mathbb{P}(\bar X_n > a) \asymp e^{-n I(a)}$ con $I(a) = \sup_t (ta - \log M_X(t))$ — la *rate function* è una KL travestita.
- **ELBO / variational inference**: $\log g(\tau) = E_q[\log g(\tau,\theta)] + H(q) + D_{KL}(q\|g(\cdot\mid\tau))$.

### [[Machine Learning]] — la cross-entropy come loss
Punto di vista pratico: la cross-entropy è la **loss universale per classificazione**.

- **[[Cross-entropy]]** + **[[Softmax]]** — per classificazione multiclasse $K$:
$$\ell(\theta; x, y) = -\log \frac{e^{z_y}}{\sum_k e^{z_k}}$$
dove $z_k = w_k^\top \phi(x)$. È esattamente $-\log q_\theta(y\mid x)$ → MLE.
- **Equivalenza MSE / cross-entropy** in regressione gaussiana: NLL gaussiana = MSE, NLL multinomiale = cross-entropy.
- **[[t-SNE]]** e **[[Stochastic Neighbor Embedding|SNE]]**: definiscono distribuzioni $P$ (coppie nello spazio originale) e $Q$ (coppie nello spazio embedded), minimizzano $D_{KL}(P\|Q)$ rispetto agli embedding.

### [[Informatica per il Machine Learning]] — language modeling e information bottleneck
Tre applicazioni dirette:

- **[[Language Model]]**: la cross-entropy media sui token è la *perplexity* (in scala log). $\text{PPL} = e^{H(P_{\text{data}}, Q_{\text{model}})}$. Minimizzare PPL = stringere $Q$ verso $P_{\text{data}}$.
- **Smoothing dei n-gram** (Laplace, Kneser-Ney): regolarizza $Q$ per evitare $D_{KL} = +\infty$ su token mai visti (zero probabilità).
- **Encoder-Decoder / [[Seq2Seq e Encoder-Decoder]]**: il "context vector" è un *information bottleneck* che comprime l'input — l'attention rilassa questa compressione.
- **[[BERT]] MLM**: cross-entropy mascherata — predizione di token nascosti come problema di information completion.
- **Negative sampling** (Word2Vec): approssima cross-entropy completa con $K+1$ termini; legato a NCE (Noise Contrastive Estimation).

### [[Probabilità e Statistica]] — il fondamento elementare
Introduzione di entropia e informazione mutua come funzionali astratti delle distribuzioni. Esempi sui canali rumorosi (Shannon coding theorem visto a livello introduttivo).

## Le quattro identità da ricordare

### 1. Decomposizione cross-entropy
$H(P,Q) = H(P) + D_{KL}(P\|Q)$ → minimizzare cross-entropy = minimizzare KL (con $P$ fissa).

### 2. Decomposizione entropia congiunta
$H(X,Y) = H(X) + H(Y\mid X) = H(Y) + H(X\mid Y)$ → catena di entropie condizionate.

### 3. Mutual information
$I(X;Y) = H(X) - H(X\mid Y) = H(Y) - H(Y\mid X) = H(X) + H(Y) - H(X,Y)$
$= D_{KL}(P_{XY}\|P_X P_Y)$ → quanta dipendenza c'è.

### 4. Pinsker
$\|P-Q\|_{TV}^2 \leq \frac{1}{2}D_{KL}(P\|Q)$ → bound della distanza in variazione totale via KL.

## I cinque ruoli dell'entropia

| Ruolo | Corso | Esempio |
|---|---|---|
| **Misura di incertezza** | ProbStat | $H(\text{Bernoulli}(p))$ massima a $p=1/2$ |
| **Numero medio di bit** | InfML, MMFII | code length, perplexity |
| **Limite di compressione** | InfML | source coding theorem |
| **Funzionale variazionale** | MMFII | MaxEnt → Boltzmann-Gibbs |
| **Termine di esplorazione** | ML/RL | entropy regularization |

## Tre asimmetrie da non confondere

### KL non è simmetrica
$D_{KL}(P\|Q) \neq D_{KL}(Q\|P)$. La scelta cambia il comportamento dell'inferenza variazionale:
- **Forward KL** $D_{KL}(P\|Q)$: $Q$ "copre" il supporto di $P$ → distribuzione approssimante *larga*.
- **Reverse KL** $D_{KL}(Q\|P)$: $Q$ si concentra in *un* picco di $P$ → mode-seeking.
VAE usa reverse KL; EP (Expectation Propagation) usa forward.

### Cross-entropy non è simmetrica
$H(P,Q) \neq H(Q,P)$. In ML usiamo sempre $H(P_{\text{data}}, Q_{\text{model}})$.

### Mutual information è simmetrica
$I(X;Y) = I(Y;X)$, ma le entropie condizionate no: $H(X\mid Y)\neq H(Y\mid X)$ in generale.

## Connessioni con altri argomenti trasversali

- **[[Probabilità bayesiana e inferenza]]**: il rischio bayesiano con log-loss è una KL; la log-evidenza si decompone in ELBO + KL alla posterior.
- **[[Catene di Markov e MCMC]]**: la stazionaria di una catena Metropolis con target $e^{-\beta H}$ è la distribuzione MaxEnt. Il *mixing time* è legato a un decay esponenziale di KL.
- **[[Reti neurali]]**: cross-entropy è la loss standard di classificazione; entropy regularization in policy networks.
- **[[SVD e decomposizione spettrale]]**: PCA preserva la varianza; t-SNE preserva le similarità via KL — due diverse "info-preserving projections".
- **[[Ottimizzazione iterativa]]**: gradient descent su cross-entropy ha gradienti $\partial \ell / \partial z_k = q_k - p_k$ — pulito e ben condizionato (a differenza di MSE su sigmoide).

## Punti di attenzione (errori comuni)

1. **KL non è una metrica**. Niente disuguaglianza triangolare, niente simmetria. Per metriche reali usa Jensen-Shannon o Wasserstein.
2. **Entropia massima non è "uniforme"**. Lo è solo senza vincoli. Con vincoli di momento si ha Boltzmann-Gibbs.
3. **Cross-entropy esplode** se $q(x) = 0$ dove $p(x) > 0$. Da qui l'esigenza di smoothing in language models.
4. **Perplexity non è "accuratezza"**. PPL = 1 significa modello deterministico perfetto; PPL = $|V|$ significa uniforme su vocabolario.
5. **Massimizzare $I(X;Y)$ non è sempre buono**. In information bottleneck, si massimizza $I(Y;\hat Y)$ con vincolo su $I(X;\hat X)$.

## Pagine collegate

- Concetti centrali: [[Entropia di Shannon]], [[Divergenza di Kullback-Leibler]], [[Cross-entropy]]
- Principio variazionale: [[Principio di massima entropia]]
- Disuguaglianze: [[Disuguaglianza di Jensen]]
- Inferenza: [[Apprendimento Bayesiano]], [[BIC]], [[Stima di Massima Verosimiglianza]]
- Applicazioni: [[t-SNE]], [[Stochastic Neighbor Embedding]], [[Language Model]], [[Softmax]]
- Fisica: [[Modello di Ising]], [[Modello di Curie-Weiss e Hopfield]], [[Teoria delle grandi deviazioni]]

## Fonti aggregate

- [[Dispense MMFII — Galletti]] (§3 — Shannon, MaxEnt)
- [[Dispense MatML — Galletti]] (§2.8-2.10 — KL, BIC, rischio bayesiano)
- [[Dispense Machine Learning — Galletti]] (§7 — cross-entropy, t-SNE)
- [[Dispense InfML — Galletti]] (§3-§5 — language model, attention, BERT)
- [[Dispense ProbStat — Galletti]] (basi)
