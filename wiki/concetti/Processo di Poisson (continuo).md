---
tipo: concetto
titolo: Processo di Poisson (continuo)
aliases: ["Processo di Poisson"]
tag: [probabilità, processi-stocastici, catene-continue]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-06
---

# Processo di Poisson (a tempo continuo)

Processo stocastico $\{N_t\}_{t \geq 0}$ a valori in $\mathbb{N}$, con $N_0 = 0$, che conta il **numero di eventi accaduti** in $[0, t]$. È il modello canonico per **arrivi casuali** in tempo continuo (chiamate, decadimenti radioattivi, click, mutazioni).

## Definizione assiomatica

Tre proprietà caratterizzano il processo di Poisson omogeneo a tasso $\lambda > 0$:

1. **Incrementi indipendenti:** per $0 \leq s_1 < t_1 \leq s_2 < t_2$, le v.a. $N_{t_1} - N_{s_1}$ e $N_{t_2} - N_{s_2}$ sono indipendenti.
2. **Incrementi stazionari:** $N_{t+s} - N_s \stackrel{d}{=} N_t$ — la legge dipende solo dalla lunghezza dell'intervallo, non dall'origine.
3. **Localizzazione infinitesimale:** per $\Delta t \to 0$:
$$
P(N_{t+\Delta t} - N_t = 0) = 1 - \lambda \Delta t + o(\Delta t)
$$
$$
P(N_{t+\Delta t} - N_t = 1) = \lambda \Delta t + o(\Delta t)
$$
$$
P(N_{t+\Delta t} - N_t \geq 2) = o(\Delta t)
$$

## Distribuzione del conteggio

Da queste tre proprietà segue:

$$
\boxed{N_t \sim \mathrm{Poisson}(\lambda t)}
$$

cioè $P(N_t = k) = e^{-\lambda t}(\lambda t)^k / k!$ per $k = 0, 1, 2, \ldots$. Da cui $E[N_t] = \mathrm{Var}(N_t) = \lambda t$.

## Tempi di interarrivo

Sia $T_k$ il tempo del $k$-esimo arrivo, $T_0 = 0$. I tempi di interarrivo $\tau_k = T_k - T_{k-1}$ sono **indipendenti e identicamente distribuiti**:

$$
\tau_k \overset{\text{i.i.d.}}{\sim} \mathrm{Exp}(\lambda)
$$

Cioè con [[Distribuzione esponenziale]] di parametro $\lambda$. Inversamente, **un processo i cui interarrivi sono $\mathrm{Exp}(\lambda)$ i.i.d. è un processo di Poisson** — caratterizzazione equivalente.

**$T_k$ è una somma di $k$ esponenziali**: $T_k \sim \mathrm{Gamma}(k, \lambda)$ (anche detta Erlang).

## Memoryless e legame con Markov

L'esponenziale è l'unica distribuzione continua **senza memoria**: $P(\tau > t+s \mid \tau > s) = P(\tau > t)$. Questo rende $\{N_t\}$ una catena di Markov a tempo continuo (passato e futuro indipendenti dato il presente).

Il [[Generatore infinitesimale]] è bidiagonale:
$$
Q_{ii} = -\lambda, \quad Q_{i,i+1} = \lambda, \quad \text{altrimenti } 0
$$

## Distribuzione condizionata degli arrivi

Dato $N_t = n$, gli istanti di arrivo $T_1, \ldots, T_n$ sono distribuiti come **$n$ punti i.i.d. uniformi su $[0, t]$ ordinati** (statistica d'ordine):
$$
(T_1, \ldots, T_n) \mid N_t = n \stackrel{d}{=} (U_{(1)}, \ldots, U_{(n)}), \quad U_i \sim \mathrm{Unif}(0, t)
$$

Risultato controintuitivo che permette simulazione efficiente.

## Sovrapposizione e thinning

- **Sovrapposizione:** se $N^{(1)}, N^{(2)}$ sono processi di Poisson indipendenti a tassi $\lambda_1, \lambda_2$, allora $N^{(1)} + N^{(2)}$ è Poisson a tasso $\lambda_1 + \lambda_2$.
- **Thinning:** se ogni arrivo viene "tenuto" indipendentemente con probabilità $p$, il processo di arrivi tenuti è Poisson a tasso $p\lambda$.

## Processo di Poisson non omogeneo

Generalizzazione: il tasso $\lambda(t)$ è funzione del tempo. Allora:
$$
N_t \sim \mathrm{Poisson}\!\left(\int_0^t \lambda(s)\, ds\right)
$$
Gli incrementi non sono più stazionari, ma rimangono indipendenti.

## Relazione con altri processi

- **Caso particolare di [[Processo di nascita e morte]]:** birth-only con tasso $\lambda$ costante, niente morti.
- **Limite di [[Distribuzione di Poisson|Binomiali]]:** per $n \to \infty$ con $np \to \lambda$, il numero di successi su $n$ prove Bernoulli converge alla Poisson — discretizzazione di un processo continuo.
- **Compound Poisson:** somma di v.a. i.i.d. al ritmo di un processo di Poisson; usato in modelli assicurativi (insurance ruin, Cramér-Lundberg).

## Esempi applicativi

- Decadimento radioattivo (numero di decadimenti in $[0, t]$).
- Code (arrivi a uno sportello bancario, modello $M/M/1$).
- Genetica (mutazioni lungo un genoma).
- Fisica statistica: cosmic ray events.

## Connessioni

- Tempo di attesa: [[Distribuzione esponenziale]]
- Conteggio: [[Distribuzione di Poisson]] (caso discreto)
- Estensione: [[Generatore infinitesimale]], [[Catena di Markov]] a tempo continuo
- Applicazione: [[Processo di nascita e morte]]
- Costruzione: tramite simulazione, [[Catena immersa]] degli istanti di salto

## Persone

- **Siméon Denis Poisson** ([[Poisson, Siméon Denis]]): distribuzione (1837).
- **Filip Lundberg** (1903): primo uso del processo per modelli attuariali.
- Formalizzazione moderna in **Khinchin** ([[Khinchin, Aleksandr]]) e **Doob** (1953).

## Fonti

- [[Dispense Processi Stocastici — Galletti]] (§5.2, pp. 21-23)
