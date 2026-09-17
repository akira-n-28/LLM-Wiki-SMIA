---
tipo: concetto
titolo: Rischio teorico
tag: [ml, statistica, fondamenti]
cluster: ml
fonti: 1
ultima-modifica: 2026-04-30
---

# Rischio teorico (Expected Loss)

Valore atteso della [[Funzione di perdita]] sull'intera distribuzione dei dati. Quantifica l'errore medio che il modello commetterebbe **su dati mai visti** — la sua capacità di generalizzazione.

## Definizione

$$
\ell(g) = \mathbb{E}_{(X,Y) \sim P}[L(Y, g(X))]
$$

dove `P` è la vera distribuzione congiunta `f(x, y)`, in generale **ignota**.

## Predittore ottimo

L'obiettivo è:

$$
g^* = \arg\min_g \ell(g), \quad \ell^* := \ell(g^*)
$$

`ℓ*` è detto **rischio di Bayes** (limite teorico inferiore, dovuto al rumore irriducibile `ε(x)` con `Var[ε(x)] = ν²`).

### Forma esplicita per due loss notevoli

- **Loss MSE** (`L = (y-ŷ)²`): il predittore ottimo è `g*(x) = E[Y|X=x]` (Teorema 2.1, dimostrazione classica via espansione del quadrato e legge dell'aspettativa iterata).
- **Loss 0-1**: il predittore ottimo è il classificatore di Bayes `g*(x) = arg max_y f(y|x)`, e il rischio coincide con `P(Y ≠ g(X))`.

## Approssimazione pratica

Poiché `P` è ignota, nella pratica si usa il [[Rischio empirico]] calcolato su un training set, applicando il principio dell'[[ERM|Empirical Risk Minimization]].

## Decomposizione

Su una classe `G`:

$$
\ell(g_\tau^G) = \underbrace{\ell^*}_{\text{Bayes}} + \underbrace{(\ell(g^G) - \ell^*)}_{\text{approssimazione}} + \underbrace{(\ell(g_\tau^G) - \ell(g^G))}_{\text{stima}}
$$

Vedi [[Errore di approssimazione e di stima]].

## Collegamenti

- Approssimato da: [[Rischio empirico]]
- Componenti: [[Errore di approssimazione e di stima]], [[Bias-Variance trade-off]]
- Stima pratica: [[Cross-validation]], test set

## Fonti

- [[Dispense MatML — Galletti]] (def. 2.1, p. 9; teor. 2.1, p. 11)
