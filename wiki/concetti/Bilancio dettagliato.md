---
tipo: concetto
titolo: Bilancio dettagliato
tag: [probabilità, processi-stocastici, statistica-computazionale]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Bilancio dettagliato (Detailed Balance)

Condizione di **reversibilità temporale** per una catena di Markov con densità di transizione effettiva `q̃(y|x)` e distribuzione target `f(x)`:

$$
f(x)\,\tilde q(y|x) = f(y)\,\tilde q(x|y) \quad \forall x, y
$$

Il flusso di probabilità da `x` a `y` è esattamente bilanciato dal flusso inverso da `y` a `x`.

## Implicazione per la stazionarietà

Il bilancio dettagliato è una condizione **sufficiente** (non necessaria) per la stazionarietà:

$$
\int f(x)\,\tilde q(y|x)\,dx = f(y)\,\underbrace{\int \tilde q(x|y)\,dx}_{= 1} = f(y)
$$

La distribuzione `f` è quindi stazionaria per la catena con transizione `q̃`.

## Bilancio dettagliato vs Stazionarietà

| | Stazionarietà | Equilibrio (Bilancio dettagliato) |
|---|---|---|
| **Condizione** | Globale: flussi in entrata = uscita per ogni stato | Locale: flusso bilanciato per ogni coppia di stati |
| **Cicli** | Possono esistere cicli netti `A→B→C→A` | Non esistono cicli netti |
| **Forza** | Più debole | Più forte |

**Analogia**: tre piazze A, B, C. Stazionarietà: ogni piazza mantiene lo stesso numero di persone (flussi totali bilanciati). Bilancio dettagliato: per ogni coppia di piazze, il flusso diretto e inverso sono identici.

## Verifica per Metropolis-Hastings

L'algoritmo [[Metropolis-Hastings]] costruisce `q̃` in modo da soddisfare automaticamente il bilancio dettagliato. La probabilità di transizione effettiva è:

$$
\tilde q(y|x) = q(y|x)\,\alpha(x,y), \quad \alpha(x,y) = \min\!\left(\frac{f(y)\,q(x|y)}{f(x)\,q(y|x)}, 1\right)
$$

Si verifica che `f(x) q̃(y|x) = f(y) q̃(x|y)` per i due casi `α < 1` e `α = 1` (simmetrico).

## Caso Gibbs

Il [[Campionamento di Gibbs]] con aggiornamento casuale delle componenti (random scan) soddisfa il bilancio dettagliato; con scan sistematico non lo soddisfa, ma la distribuzione limite è comunque `f` (per il Teorema di Hammersley-Clifford).

## Bilancio globale (condizione necessaria per stazionarietà)

La condizione necessaria (più debole) è il **bilancio globale**:

$$
\int f(x)\,q(y|x)\,dx = f(y)
$$

Esistono catene ergodiche (con flussi ciclici netti) che soddisfano il bilancio globale ma non quello dettagliato.

## Connessione con la fisica

In termodinamica, il bilancio dettagliato corrisponde alla **reversibilità microscopica** (principio di microscopic reversibility o principio di Onsager). La distribuzione di Boltzmann-Gibbs `P(σ) ∝ e^{-βH(σ)}` è la distribuzione stazionaria della catena M-H per la proposta simmetrica.

## Schema delle condizioni per MCMC

$$
\underbrace{\text{Irriducibilità + Aperiodicità}}_{\text{ergodicità: } \exists!\pi} + \underbrace{\text{Bilancio dettagliato}}_{\pi = f} \Rightarrow \text{convergenza a } f(x)
$$

BD ed ergodicità sono **condizioni indipendenti**: una catena può essere reversibile ma non ergodica (es. sconnessa), o ergodica ma non reversibile.

## Importanza pratica

Il bilancio dettagliato è preferito al semplice bilancio globale in MCMC perché è **più semplice da verificare** e garantisce in modo robusto la convergenza alla distribuzione desiderata.

## Connessione con i Processi Stocastici

In fisica statistica e processi stocastici, il bilancio dettagliato è legato alla reversibilità della dinamica di Markov e all'equazione master (equazione di Chapman-Kolmogorov). Vedi [[Processi Stocastici]].

## Connessione con il collegamento con la termodinamica

Nei modelli di spin (Ising, Potts), imporre il bilancio dettagliato con la distribuzione di Boltzmann-Gibbs garantisce che la simulazione MCMC converga all'equilibrio termodinamico.

## Collegamenti

- Garantisce stazionarietà per: [[Metropolis-Hastings]], [[Campionamento di Gibbs]] (random scan)
- Concetto più debole: bilancio globale
- Framework: [[Catena di Markov]], [[Metodi Monte Carlo]]
- Applicazione fisica: [[Modelli Matematici per la Fisica II]] (Boltzmann-Gibbs)

## Fonti

- [[Dispense MatML — Galletti]] (§3.9.1, pp. 50-52)
