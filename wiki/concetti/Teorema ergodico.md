---
tipo: concetto
titolo: Teorema ergodico
aliases: ["Ergodicità"]
tag: [probabilità, processi-stocastici, catene-di-markov]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-06
---

# Teorema ergodico

Il **teorema ergodico** è il risultato fondamentale che lega due nozioni di "media" in un sistema dinamico stocastico:

- **Media spaziale** (sull'ensemble): $\sum_j j \cdot \pi_j$, dove $\pi$ è la distribuzione stazionaria.
- **Media temporale** (sulla traiettoria): $\frac{1}{n} \sum_{k=1}^n f(X_k)$ lungo un singolo cammino.

Per sistemi **ergodici**, queste due quantità coincidono.

## Enunciato per [[Catena di Markov]] discrete

Sia $\{X_n\}$ una catena a stati finiti o numerabili, **irriducibile**, **aperiodica**, e **positivamente ricorrente**. Allora esiste un'unica [[Catena di Markov|distribuzione stazionaria]] $\pi$ con:

$$
\boxed{\ \lim_{n \to \infty} P(X_n = j \mid X_0 = i) = \pi_j = \frac{1}{\mu_j(j)}\quad \forall i, j\ }
$$

dove $\mu_j(j) = E[T_j \mid X_0 = j]$ è il **tempo medio di ritorno** allo stato $j$.

Equivalentemente, per ogni funzione limitata $f$:

$$
\frac{1}{n} \sum_{k=1}^n f(X_k) \xrightarrow{q.c.} \sum_j \pi_j f(j)
$$

## Le tre ipotesi essenziali

| Ipotesi | Cosa esclude |
|---|---|
| **Irriducibilità** | catene riducibili (più classi comunicanti) hanno più stazionarie |
| **Aperiodicità** | catene periodiche oscillano ciclicamente, $P^n$ non converge |
| **Ricorrenza positiva** | catene transienti o nulle non hanno stazionaria normalizzabile |

**Esempio violazione aperiodicità:** catena su $\{0, 1\}$ con $P_{01} = P_{10} = 1$. Ha stazionaria $\pi = (1/2, 1/2)$, ma $P^n_{ii}$ alterna tra 0 e 1 senza limite.

## Versione a tempo continuo

Per una catena continua con [[Generatore infinitesimale]] $Q$, irriducibile e con stazionaria $\pi$ (autovettore sinistro: $\pi Q = 0$):

$$
\lim_{t \to \infty} P(X_t = j \mid X_0 = i) = \pi_j
$$

Non serve l'aperiodicità (il tempo è continuo, non c'è ciclicità discreta).

## Versione astratta (Birkhoff)

Per un sistema dinamico misurabile preservante la misura $(S, \mu, T)$ con $T$ ergodico, e $f \in L^1(\mu)$:

$$
\lim_{n \to \infty} \frac{1}{n} \sum_{k=0}^{n-1} f(T^k x) = \int f\, d\mu \qquad \mu\text{-q.c.}
$$

La media temporale lungo l'orbita di un punto generico converge alla media spaziale rispetto a $\mu$. Le catene di Markov sono un caso particolare con $\mu = \pi$.

## Connessione con la [[Legge dei Grandi Numeri]]

Per v.a. **i.i.d.** (caso senza memoria), la LGN dà $\frac{1}{n}\sum X_i \to E[X]$. Il teorema ergodico **estende la LGN** a sequenze dipendenti che condividono la struttura markoviana — purché le tre ipotesi siano verificate.

## Applicazioni

- **MCMC:** dopo il burn-in, $\frac{1}{N}\sum f(X_k)$ approssima $E_\pi[f]$. Cfr. [[Metropolis-Hastings]].
- **Page Rank:** la stazionaria della random walk sui link è la distribuzione di "importanza".
- **Fisica statistica:** la media temporale di un'osservabile coincide con l'ensemble (ipotesi ergodica di Boltzmann).
- **Code:** $M/M/1$ ha stazionaria geometrica se $\rho = \lambda/\mu < 1$; il teorema ergodico dà i tempi medi di attesa.

## Mixing time

Quanto velocemente si raggiunge la stazionaria? Il **mixing time** è:
$$
t_{\mathrm{mix}}(\epsilon) = \min\{n : \max_i \|P^n(i, \cdot) - \pi\|_{TV} \leq \epsilon\}
$$
Lega al **secondo autovalore** $|\lambda_2|$ di $P$: $t_{\mathrm{mix}} \asymp 1/(1 - |\lambda_2|)$. Vedi [[SVD e decomposizione spettrale]].

## Connessioni

- Concetto centrale: [[Catena di Markov]] (proprietà ergodiche)
- Caso speciale: [[Legge dei Grandi Numeri]] (i.i.d.)
- Applicazione: [[Metropolis-Hastings]], [[Catene di Markov e MCMC]]
- Spettrale: il rate di convergenza dipende da $|\lambda_2|$
- Estensione: ergodicità a tempo continuo, [[Generatore infinitesimale]]

## Persone

- **George Birkhoff** (1931): teorema ergodico astratto.
- **John von Neumann** (1932): versione $L^2$.
- **Aleksandr Khinchin** ([[Khinchin, Aleksandr]]): contributi alla teoria.

## Fonti

- [[Dispense Processi Stocastici — Galletti]] (§3, §5 — caso discreto e continuo)
