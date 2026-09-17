---
tipo: argomento
titolo: Regolarizzazione
tag: [trasversale, ml, ottimizzazione, calcolo-numerico, statistica]
cluster: trasversale
corsi: [Machine Learning, Matematica per il Machine Learning, Informatica per il Machine Learning, Metodi Numerici, Ottimizzazione]
ultima-modifica: 2026-05-06
---

# Regolarizzazione

Argomento trasversale che attraversa **5 corsi**. Una sola idea — penalizzare soluzioni "troppo grandi" o "troppo complesse" — riappare sotto sei nomi diversi: ridge in ML, Tikhonov in MetNum, MAP gaussiano in MatML, dropout in InfML, early stopping in addestramento, weight decay nei deep model. Tutti questi sono **manifestazioni della stessa correzione**: invece di risolvere $\min L(\theta)$, si risolve $\min[L(\theta) + \lambda R(\theta)]$.

## Il nucleo unificante

Il problema di partenza è ill-posed: o sotto-determinato (più incognite che vincoli), o mal condizionato (sensibile a piccole perturbazioni). La regolarizzazione corregge aggiungendo:

$$
\theta^* = \arg\min_\theta \bigl[\, L(\theta) + \lambda R(\theta)\,\bigr]
$$

con tre meccanismi equivalenti che giustificano il termine $R(\theta)$:

| Meccanismo | Vista dal corso | Forma di $R$ |
|---|---|---|
| **Algebra lineare** | MetNum, ML | rendere $A^\top A + \lambda I$ invertibile |
| **Statistica bayesiana** | MatML | log-prior $-\log g(\theta)$ |
| **Statistical learning** | ML | penalità su capacità del modello |

L'identità centrale: per $L(\theta) = \|y - X\theta\|^2$ e $R(\theta) = \|\theta\|^2$, le tre prospettive coincidono — è lo stesso problema visto da tre angoli.

## Il tour dei corsi

### [[Metodi Numerici]] — l'origine numerica
**Il problema**: risolvere $Ax = b$ quando $A$ è mal condizionata ($K_2(A) = \sigma_1/\sigma_n$ enorme) o singolare. Tikhonov (1963) propone:
$$(A^\top A + \alpha I) x = A^\top b$$
- Effetto sugli autovalori: $\sigma_i^2 \mapsto \sigma_i^2 + \alpha$ — gli autovalori piccoli vengono "alzati".
- Tramite SVD: $x_\alpha = \sum_i \frac{\sigma_i}{\sigma_i^2 + \alpha} u_i^\top b \cdot v_i$ — *filter factor* $\sigma_i^2/(\sigma_i^2+\alpha)$.
- **Curva L** per scegliere $\alpha$: trade-off $\|Ax-b\|$ vs $\|x\|$.
- Cugini: **truncated SVD** (filter $\mathbf{1}_{\sigma_i > \tau}$), **PCG** preconditioned (cambio di base che riduce $K_2$).

### [[Machine Learning]] — la regolarizzazione come trade-off bias-varianza
- **[[Regolarizzazione di Tikhonov|Ridge]]**: $\min \|y - X\beta\|^2 + \lambda \|\beta\|^2$, soluzione chiusa.
- **Lasso**: $\min \|y - X\beta\|^2 + \lambda \|\beta\|_1$, soluzione sparsa.
- **Elastic Net**: combinazione delle due.
- **[[Bias-Variance trade-off]]**: $\lambda$ aumenta bias e riduce varianza. Optimum: dove la somma è minima.
- **[[Cross-validation]]**: scelta empirica di $\lambda$ minimizzando errore out-of-sample.
- **Predittori correlati**: ridge "spalma" il peso tra correlati; Lasso ne sceglie uno solo.

### [[Matematica per il Machine Learning]] — la regolarizzazione come MAP
**Risultato chiave** (cfr. argomento [[Probabilità bayesiana e inferenza]]):
$$\bar\theta = \arg\max[\log g(\tau\mid\theta) + \log g(\theta)]$$
Il termine $\log g(\theta)$ è esattamente $-\lambda R(\theta)$ per scelte specifiche del prior:

| Prior | Forma | Penalty equivalente |
|---|---|---|
| Gaussiano $\mathcal{N}(0, \sigma_p^2)$ | $\log g \propto -\frac{1}{2\sigma_p^2}\|\theta\|^2$ | **Ridge** $\lambda = 1/(2\sigma_p^2)$ |
| Laplace $\mathrm{Lap}(0, b)$ | $\log g \propto -\frac{1}{b}\|\theta\|_1$ | **Lasso** $\lambda = 1/b$ |
| Cauchy | $\log g \propto -\sum\log(1+\theta_i^2)$ | non convessa, sparsità più forte |
| Spike-and-slab | mistura di $\delta$ e gaussiana | sparsità "vera" $L^0$ |

**Insight**: ogni regolarizzatore corrisponde a una credenza a priori sui parametri.

### [[Informatica per il Machine Learning]] — i regolarizzatori delle reti profonde
Le reti profonde sono *over-parametrizzate*: regolarizzazione cruciale.

- **L2 (weight decay)**: $\nabla L \mapsto \nabla L + \lambda \theta$. Equivalente a SGD su $L + \frac{\lambda}{2}\|\theta\|^2$.
- **L1 (Lasso)**: rara nei pesi di rete, comune sui gradienti per features.
- **[[Dropout]]**: a ogni iterazione, "spegne" ogni neurone con probabilità $p$. Tre interpretazioni:
  1. ensemble implicito di $2^N$ sotto-reti (mediano in inference);
  2. data augmentation strutturata (rumore moltiplicativo);
  3. approssimazione variazionale di rete bayesiana.
- **Batch normalization**: regolarizzazione implicita riducendo covariate shift; agisce come noise.
- **Early stopping**: implicit regularization. Per regressione lineare con SGD, equivalente a ridge con $\lambda$ funzione del numero di iterazioni.
- **Data augmentation**: trasformazioni invarianti (flip, crop) → prior implicito di simmetria.

### [[Ottimizzazione]] — la regolarizzazione come problema vincolato
**Equivalenza penalty ↔ vincolo**:
$$\min_\theta L(\theta) + \lambda R(\theta) \quad \Longleftrightarrow \quad \min_{\theta: R(\theta) \leq c} L(\theta)$$
con corrispondenza biiettiva $\lambda \leftrightarrow c$ (per $L, R$ convessi). [[Condizioni KKT]] con vincolo $R(\theta) - c \leq 0$ producono $\nabla L + \lambda \nabla R = 0$, $\lambda \geq 0$ — esattamente la stationarity del problema penalizzato.

**Frank-Wolfe** e **proiezione** sono i metodi naturali per la formulazione vincolata.

## Il quadro unificato

Tutta la regolarizzazione collassa in tre dimensioni:

### 1. Cosa penalizza?
| Forma | Effetto |
|---|---|
| $\|\theta\|^2$ | shrinkage uniforme |
| $\|\theta\|_1$ | sparsità (selezione di feature) |
| $\|D\theta\|^2$ | smoothness (penalizza derivate) |
| $\|D\theta\|_1$ | total variation (preserva edge) |
| entropia $H(\theta)$ | uniformità (max entropy regularizer) |

### 2. Come è imposta?
- **Esplicita**: termine in loss.
- **Implicita**: tramite training dynamics (early stopping, SGD bias).
- **Architetturale**: dropout, batch norm, weight tying.
- **Dati**: data augmentation, label smoothing.

### 3. Come si calibra $\lambda$?
- **Cross-validation** (ML, InfML): empirica.
- **Curva L** (MetNum): grafica.
- **Empirical Bayes** (MatML): massimizza marginal likelihood.
- **BIC / AIC** (MatML): correzione asintotica.

## Tre teoremi che lo unificano

### 1. Equivalenza ridge ↔ MAP gaussiano
$$\arg\min[\|y - X\beta\|^2 + \lambda\|\beta\|^2] = \arg\max[\log\mathcal{N}(y; X\beta, I) + \log\mathcal{N}(\beta; 0, \tfrac{1}{\lambda}I)]$$
Penalty quadratica = log-prior gaussiano.

### 2. Filter factor di Tikhonov via SVD
$$\beta_\lambda = \sum_i \frac{\sigma_i}{\sigma_i^2 + \lambda} (u_i^\top y) v_i$$
Componenti con $\sigma_i^2 \gg \lambda$: invariate. Con $\sigma_i^2 \ll \lambda$: soppresse. Lega a [[SVD e decomposizione spettrale]].

### 3. Early stopping ↔ ridge per regressione lineare
SGD su $\frac{1}{2}\|y - X\beta\|^2$ con step $\eta$ produce $\beta_t$ che coincide approssimativamente con la soluzione ridge $\beta_\lambda$ per $\lambda \approx 1/(\eta t)$. Più training = $\lambda$ minore.

## Connessioni con altri argomenti trasversali

- **[[SVD e decomposizione spettrale]]**: ridge = shift uniforme degli autovalori di $X^\top X$. Truncated SVD = hard threshold; ridge = soft threshold. Stesso problema, due filter.
- **[[Probabilità bayesiana e inferenza]]**: ogni regolarizzatore è un prior. Cross-validation stima ciò che evidence Bayesiana calcola in chiuso (con prior coniugato).
- **[[Reti neurali]]**: dropout, weight decay, BN, early stopping sono tutti regolarizzatori per reti profonde.
- **[[Ottimizzazione iterativa]]**: PCG = ridge nello spazio dell'iterazione (preconditioning); proximal methods (ISTA, FISTA) ottimizzano direttamente il problema regolarizzato L1.
- **[[Catene di Markov e MCMC]]**: SGD = Langevin discretizzato → bias verso minimi piatti = regolarizzazione implicita.
- **[[Entropia e information theory]]**: maximum entropy regularization in policy networks; KL regularization in RL ($\beta \cdot D_{KL}$).

## Punti di attenzione (errori comuni)

1. **Ridge non è scale-invariant.** Standardizzare le feature prima.
2. **Lasso seleziona arbitrariamente tra correlati.** Con due predittori identici, può scegliere uno con peso $\beta$ e l'altro con $0$, o viceversa.
3. **$\lambda$ ottimo dipende da $n$.** Più dati = meno regolarizzazione necessaria.
4. **Early stopping non è ridge esatto.** L'equivalenza è approssimata e dipende dalla geometria del landscape.
5. **Dropout durante test va spento.** O scalato (inverted dropout) per coerenza.
6. **Regolarizzare il bias è di solito sbagliato.** Solo i pesi $W$, non l'intercetta $b$.

## Pagine collegate

- Concetti centrali: [[Regolarizzazione di Tikhonov]], [[Lasso e Elastic Net]], [[Stima MAP]], [[Dropout]]
- Trade-off: [[Bias-Variance trade-off]], [[Overfitting e underfitting]], [[Cross-validation]]
- Selezione modello: [[BIC]]
- Vincoli: [[Condizioni KKT]], [[Frank-Wolfe e gradiente proiettato]]
- Spettrale: [[Singular Value Decomposition]], [[Numero di condizionamento]]
- Probabilistico: [[Apprendimento Bayesiano]], [[Distribuzioni coniugate]]

## Fonti aggregate

- [[Dispense Machine Learning — Galletti]] (§3.4 — Tikhonov, ridge)
- [[Dispense MatML — Galletti]] (§2.10-2.11 — MAP, prior gaussiano)
- [[Dispense InfML — Galletti]] (§3.2 — Lasso/Elastic Net, §6 — Dropout)
- [[Dispense Metodi Numerici — Galletti]] (cap. 4 — sistemi mal cond., LS sovradeterminati)
- [[Dispense Ottimizzazione — Galletti]] (cap. 4-5 — KKT, problemi vincolati)
