---
tipo: concetto
titolo: Generatore MRG
tag: [probabilità, statistica-computazionale]
cluster: probabilistica
fonti: 1
ultima-modifica: 2026-05-04
---

# Generatore MRG (Multiple Recursive Generator)

Algoritmo per generare sequenze di numeri pseudo-casuali uniformemente distribuiti in `(0,1)`. Si basa su una **relazione di ricorrenza lineare** (processo autoregressivo di ordine `k`):

$$
x_t = (a_1 x_{t-1} + a_2 x_{t-2} + \cdots + a_k x_{t-k}) \bmod m, \quad t \geq k
$$

I numeri pseudo-casuali si ottengono normalizzando: `U_t = x_t / m`.

## Parametri di configurazione

- **Modulo `m`**: numero primo grande (tipicamente `2^{31} - 1`). Determina il range degli interi.
- **Coefficienti `a_1, …, a_k`**: scelti affinché la formula percorra tutti i `m^k - 1` stati possibili prima di ripetersi (periodo massimo).
- **Semi iniziali** `{x_0, x_1, …, x_{k-1}}`: non tutti nulli (lo zero è uno stato assorbente).

## Periodo massimo

Poiché la memoria è limitata agli ultimi `k` stati, la sequenza è necessariamente periodica. Con la scelta ottimale di `m` e `a_i`, il **periodo massimo** è `m^k - 1` (si esclude lo stato tutto-zero).

## Proprietà pseudo-casuali

I numeri `U_t = x_t / m` simulano v.a. i.i.d. `∼ U(0,1)` in senso statistico: passano i test standard di uniformità e indipendenza. Non sono "veri" casuali: deterministica dalla seed.

## Importanza della seed

Fissare la seed garantisce la **riproducibilità** degli esperimenti — fondamentale in ML per la validazione di risultati sperimentali.

## Uso nei metodi Monte Carlo

Il MRG è il blocco di base di tutti i [[Metodi Monte Carlo]]: ogni metodo di campionamento parte da `U ∼ U(0,1)` generato dal MRG e applica trasformazioni per ottenere campioni da distribuzioni più complesse.

## Limitazioni

- Pseudo-casuale, non casuale: una sequenza molto lunga rivela la struttura deterministica.
- La qualità statistica dipende dalla scelta dei parametri; scelte errate producono sequenze con pattern visibili.

## Alternativa hardware

Per applicazioni crittografiche si usano generatori hardware (TRNG, True Random Number Generators) basati su fenomeni fisici; per ML e statistica i generatori software come MRG sono sufficienti.

## Connessione con catene di Markov

Un MRG è tecnicamente una catena di Markov di ordine `k` su uno spazio di stati finito `{0, 1, …, m-1}^k`. Il periodo massimo corrisponde all'irriducibilità e all'aperiodicità della catena.

## Collegamenti

- Strumento base di: [[Metodi Monte Carlo]]
- Usato in: [[Algoritmo di Box-Muller]], [[Metodo della funzione inversa]], [[Metodo accept-reject]], [[Metropolis-Hastings]], [[Bootstrap]]

## Fonti

- [[Dispense MatML — Galletti]] (§3.2, pp. 44-45)
