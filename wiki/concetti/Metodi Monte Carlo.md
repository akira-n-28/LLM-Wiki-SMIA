---
tipo: concetto
titolo: Metodi Monte Carlo
tag: [ml, probabilità, statistica-computazionale]
cluster: ml
fonti: 1
ultima-modifica: 2026-05-04
---

# Metodi Monte Carlo

Classe di algoritmi computazionali basati sul **campionamento casuale ripetuto** per ottenere risultati numerici su problemi deterministicamente intrattabili. Il nome deriva dal Casinò di Montecarlo.

## Tre macro-applicazioni

1. **Campionamento**: generare configurazioni da distribuzioni complesse. Esempio classico: distribuzione di Boltzmann-Gibbs `P(σ) = e^{-βH(σ)}/Z` per sistemi con `N` spin, dove la somma su `2^N` stati è impraticabile. MC genera campioni proporzionali alla probabilità senza mai calcolare `Z`.

2. **Integrazione numerica** (stima di valore atteso):
   $$\mu = \mathbb{E}[Y] = \int y f(y)\,dy \approx \bar y_N = \frac{1}{N}\sum_{i=1}^N y_i$$
   Per la **Legge dei Grandi Numeri**: `ȳ_N → μ` quasi certamente.
   Per il **Teorema Limite Centrale**: `ȳ_N ∼ N(μ, σ²/N)` asintoticamente.

3. **Ottimizzazione stocastica**: esplorazione dello spazio delle soluzioni per trovare minimi globali.

## Stima di integrali via MC (Crude Monte Carlo)

Per stimare `μ = E[Y]` con `Var[Y] = σ² < ∞`:

$$
\bar y_N = \frac{1}{N}\sum_{i=1}^N y_i, \qquad \mathrm{SE}(\bar y_N) = \frac{\sigma}{\sqrt{N}}
$$

Intervallo di confidenza asintotico al livello `1-α`:

$$
\left[\bar y_N \pm z_{1-\alpha/2}\frac{S}{\sqrt{N}}\right]
$$

**Proprietà chiave**: il tasso di convergenza `O(N^{-1/2})` è **indipendente dalla dimensione** dello spazio. Per integrali in `ℝ^d`, la quadratura deterministica richiede `N^d` punti, MC richiede lo stesso `N` indipendentemente da `d`. Fondamentale per problemi ad alta dimensionalità (→ [[Curse of dimensionality]]).

## Generazione di numeri casuali

Tutti i metodi MC si basano su un generatore di numeri pseudo-casuali uniformi:
- [[Generatore MRG]] — Multiple Recursive Generator

## Metodi di campionamento

| Metodo | Quando usarlo |
|---|---|
| [[Algoritmo di Box-Muller]] | Normali standard da uniformi |
| [[Metodo della funzione inversa]] | CDF invertibile analiticamente |
| [[Metodo accept-reject]] | Densità con maggiorante noto |
| [[Metropolis-Hastings]] | Densità nota a meno di normalizzazione |
| [[Campionamento di Gibbs]] | Full conditionals trattabili |

## Connessione con la Fisica Statistica

La distribuzione di Boltzmann-Gibbs `P(σ) ∝ e^{-βH(σ)}` (meccanica statistica) è il caso d'uso storico di Metropolis-Hastings. L'MCMC permette di campionare configurazioni di spin senza calcolare la funzione di partizione `Z`. Vedi anche [[Modelli Matematici per la Fisica II]] per il legame con l'entropia di Shannon.

## Bootstrap

Il [[Bootstrap]] è un caso particolare di MC applicato alla stima di distribuzioni campionarie: si ricampiona il dataset osservato `τ` con reinserimento per stimare la variabilità di statistiche.

## Collegamento con i corsi SMIA

- [[Processi Stocastici]]: le catene di Markov sono il fondamento teorico di MCMC.
- [[Metodi Numerici]]: integrazione di Monte Carlo vs quadratura deterministica.
- [[Modelli Matematici per la Fisica II]]: Boltzmann-Gibbs, entropia, spin models.

## Collegamenti

- Strumenti: [[Generatore MRG]], [[Algoritmo di Box-Muller]], [[Metodo della funzione inversa]], [[Metodo accept-reject]]
- Algoritmi MCMC: [[Metropolis-Hastings]], [[Campionamento di Gibbs]]
- Fondamento probabilistico: [[Catena di Markov]]
- Ricampionamento: [[Bootstrap]]

## Fonti

- [[Dispense MatML — Galletti]] (§3.1, §3.11, pp. 43-44, 55-56)
