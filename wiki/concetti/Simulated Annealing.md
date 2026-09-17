---
tipo: concetto
titolo: Simulated Annealing
tag: [ottimizzazione, statistica-computazionale, ml]
cluster: ottimizzazione
fonti: 1
ultima-modifica: 2026-05-04
---

# Simulated Annealing (Ricottura simulata)

Metodo stocastico per la **minimizzazione globale** di una funzione di costo `S(x)`, `x ∈ X`. Ispirato al processo fisico di ricottura dei metalli: raffreddamento lento permette di raggiungere la configurazione di minima energia.

## Idea fondamentale

Si associa `S(x)` all'energia di un sistema fisico e si introduce la **distribuzione di Gibbs** a temperatura `T`:

$$
f_T(x) = \frac{1}{Z_T}\exp\!\left(-\frac{S(x)}{T}\right), \quad Z_T = \int \exp\!\left(-\frac{S(x)}{T}\right)\,dx
$$

Proprietà chiave:
- **Alta temperatura** `T → ∞`: `f_T → U(X)` — esplorazione quasi uniforme dello spazio.
- **Bassa temperatura** `T → 0`: `f_T` concentra la massa attorno ai **minimi globali** di `S`.

Raffreddando progressivamente `T → 0`, la distribuzione si concentra sempre di più sui minimizzatori.

## Algoritmo

Per una sequenza decrescente di temperature `T_0 > T_1 > T_2 > …`:

```
Inizializza x₀
Per t = 1, 2, …:
  1. Campiona xₜ ∼ f_{Tₜ}(x)  (via Metropolis-Hastings a temperatura Tₜ)
  2. Abbassa la temperatura: Tₜ₊₁ < Tₜ
Restituisci xₜ (dopo criterio di arresto)
```

Ogni passo di campionamento usa [[Metropolis-Hastings]] con distribuzione target `f_{T_t}`. Per proposta simmetrica:

$$
\alpha(x,y) = \min\!\left(e^{-[S(y)-S(x)]/T_t},\, 1\right) = \min(e^{-\Delta S/T_t}, 1)
$$

Se `ΔS ≤ 0` (energia diminuisce): accetta sempre. Se `ΔS > 0`: accetta con prob. `e^{-ΔS/T}` — il sistema può "salire" colline di energia, sfuggendo ai minimi locali.

## Sequenze di raffreddamento

**Geometrica** (la più comune): `T_t = β · T_{t-1}`, `β < 1`.

**Condizione teorica per convergenza al minimo globale**: la temperatura deve decrescere abbastanza lentamente — tipicamente `T_t = C/log(t)` (molto lenta in pratica, quasi mai usata).

## Criteri di arresto

- `|S(x_t) - S(x_{t+1})| < ε` (variazione della funzione costo sotto soglia)
- Stallo: `S(x_t) = S(x_{t+1}) = … = S(x_{t+d})` per `d` iterazioni
- Temperatura sotto soglia: `T_t < T_soglia`
- Numero massimo di iterazioni

## Trade-off temperatura

| Temperatura alta | Temperatura bassa |
|---|---|
| Esplorazione libera | Sfruttamento locale |
| Esce dai minimi locali | Rischio di rimanere intrappolato |
| Convergenza lenta | Convergenza veloce al minimo locale più vicino |

## Connessione con Metropolis-Hastings

SA usa M-H come subroutine: a ogni temperatura `T_t` si esegue una catena di Markov per "termalizzare" il sistema, campionando configurazioni distribuite secondo `f_{T_t}`. La distribuzione target cambia a ogni passo.

## Connessione con la distribuzione di Boltzmann-Gibbs

La distribuzione `f_T(x) ∝ e^{-S(x)/T}` è esattamente la distribuzione di Boltzmann-Gibbs. Il parametro `β = 1/T` è l'inverso della temperatura. Vedi [[Boltzmann, Ludwig]], [[Gibbs, J. Willard]].

## Connessione con il Metodo Cross-Entropy

Entrambi usano una distribuzione parametrica che si "concentra" sui buoni candidati al diminuire delle iterazioni. SA usa la temperatura come parametro; [[Metodo Cross-Entropy]] usa il parametro `v` della famiglia `f(·|v)`.

## Applicazioni

- Ottimizzazione combinatoria (TSP, scheduling, progettazione di circuiti).
- In ML: addestramento di reti neurali difficili (alternativa o complemento a SGD).
- Fisica computazionale: campionamento di configurazioni di spin.

## Connessione con i corsi SMIA

- [[Ottimizzazione]]: metodi di discesa del gradiente vs metodi stocastici globali.
- [[Modelli Matematici per la Fisica II]]: modelli di spin, distribuzione di Boltzmann.
- [[Processi Stocastici]]: catene di Markov non omogenee (la temperatura cambia nel tempo).

## Persone

Proposto da [[Kirkpatrick, Scott]], [[Gelatt, Charles D.]], [[Vecchi, Mario P.]] (1983), *Science* 220(4598).

## Connessione con l'ottimizzazione stocastica con rumore

SA è un caso speciale di [[Approssimazione stocastica]] in cui il "gradiente rumoroso" è sostituito da un campionamento Bayesiano dalla distribuzione `f_T`.

## Collegamenti

- Usa: [[Metropolis-Hastings]], [[Catena di Markov]]
- Target: [[Boltzmann, Ludwig]] (distribuzione `e^{-S/T}`)
- Alternativa deterministica: [[Discesa del gradiente]], [[Stochastic Gradient Descent]]
- Alternativa stocastica globale: [[Metodo Cross-Entropy]]
- Ottimizzazione con rumore: [[Approssimazione stocastica]]

## Fonti

- [[Dispense MatML — Galletti]] (§3.14, algoritmo 8, pp. 62-64)
